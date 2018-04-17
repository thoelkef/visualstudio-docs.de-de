---
title: 'Vorgehensweise: Verwenden Sie für Visual Studio-Erweiterungen regelbasierte Benutzeroberflächenkontext | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 8dd2cd1d-d8ba-49b9-870a-45acf3a3259d
author: gregvanl
ms.author: gregvanl
ms.workload:
- vssdk
ms.openlocfilehash: 8597c413c899b54e61e848649c3c524cbdb20724
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/16/2018
---
# <a name="how-to-use-rule-based-ui-context-for-visual-studio-extensions"></a>Vorgehensweise: Verwenden Sie regelbasierte Benutzeroberflächenkontext für Visual Studio-Erweiterungen
Visual Studio ermöglicht das Laden von VSPackages, wenn bestimmte bekannte <xref:Microsoft.VisualStudio.Shell.UIContext>s aktiviert werden. Diese Benutzeroberfläche Kontexte sind nicht sehr präzise umfassendere, verlassen Erweiterung Autoren keine andere Möglichkeit jedoch um eine verfügbare Benutzeroberflächenkontext auswählen, die vor dem Punkt, aktiviert sie wollten das VSPackage beim Laden. Eine Liste der bekannten Benutzeroberflächen-Kontexte, finden Sie unter <xref:Microsoft.VisualStudio.Shell.KnownUIContexts>.  
  
 Laden von Paketen kann die Auswirkungen auf die Leistung haben, und Laden sie früher als sie benötigt werden, ist nicht die bewährte Methode. Visual Studio 2015 eingeführt, das Konzept der regelbasierte UI Kontexten ein Mechanismus, der ermöglicht Autoren die Erweiterung zum Definieren der präzisen Bedingungen, unter dem eine UI-Kontext aktiviert ist, und zugeordnete VSPackages geladen, wird.  
  
## <a name="rule-based-ui-context"></a>Regel-basierte Benutzeroberflächenkontext  
 Eine "Regel" besteht aus einem neuen Benutzeroberflächenkontext (eine GUID) und ein boolescher Ausdruck, der einen oder mehrere "Begriffe" verweist auf zusammen mit logischen "und", "oder", "not" Vorgänge. "Ausdrücke" werden dynamisch zur Laufzeit ausgewertet, und der Ausdruck ist erneut ausgewertet, wenn ihre Änderungen Begriffe. Wenn der Ausdruck "true" ergibt, wird die zugeordnete UI-Kontext aktiviert. Andernfalls ist der Benutzeroberflächenkontext de-activated.  
  
 Regel-basierte Benutzeroberflächenkontext kann in einer Vielzahl von Möglichkeiten verwendet werden:  
  
1.  Geben Sie die Sichtbarkeit von Einschränkungen für Befehle und Toolfenster. Sie können Befehle/Toolfenstern ausblenden, bis die Regel Benutzeroberflächenkontext erfüllt ist.  
  
2.  Als Auto serverlastbeschränkungen: Automatisches Laden Pakete nur, wenn die Regel erfüllt ist  
  
3.  Verzögerte Aufgabe: verzögert geladen, bis ein angegebenen Zeitraums vergangen ist und die Regel wird weiterhin erfüllt.  
  
 Der Mechanismus kann von Visual Studio-Erweiterung verwendet werden.  
  
## <a name="create-a-rule-based-ui-context"></a>Erstellen Sie eine regelbasierte Benutzeroberflächenkontext  
 Angenommen, Sie haben die Erweiterung TestPackage, die einen Menübefehl bietet die gilt nur für Dateien mit der Erweiterung ".config" aufgerufen. Vor dem VS2015, wurde die beste Option zum Laden von TestPackage beim <xref:Microsoft.VisualStudio.Shell.KnownUIContexts.SolutionExistsAndFullyLoadedContext%2A> Benutzeroberflächenkontext aktiviert wurde. Dies ist nicht effizient, da die geladene Projektmappe auch eine config-Datei möglicherweise keinen enthält. Lassen Sie uns finden Sie unter wie Benutzeroberflächenkontext regelbasierte verwendet werden kann, zum Aktivieren einer Benutzeroberflächenkontext nur, wenn eine Datei mit der Dateierweiterung ".config" ausgewählt ist, und TestPackage zu laden, wenn diese Benutzeroberflächenkontext aktiviert wird.  
  
1.  Definieren Sie eine neue UIContext GUID und der VSPackage-Klasse hinzufügen <xref:Microsoft.VisualStudio.Shell.ProvideAutoLoadAttribute> und <xref:Microsoft.VisualStudio.Shell.ProvideUIContextRuleAttribute>.  
  
     Beispielsweise angenommen, eine neue UIContext "UIContextGuid" wird hinzugefügt werden. Die GUID erstellt (Sie können eine GUID erstellen, indem Sie die on-Tools auf -> Guid erstellen) ist "8B40D5E2-5626-42AE-99EF-3DD1EFF46E7B". Fügen Sie dann Folgendes in der Paketklasse:  
  
    ```csharp  
    public const string UIContextGuid = "8B40D5E2-5626-42AE-99EF-3DD1EFF46E7B";  
    ```  
  
     Fügen Sie Folgendes für die Attribute hinzu: (Details dieser Attribute werden weiter unten erläutert)  
  
    ```csharp  
    [ProvideAutoLoad(TestPackage.UIContextGuid)]      
    [ProvideUIContextRule(TestPackage.UIContextGuid,  
        name: "Test auto load",   
        expression: "DotConfig",  
        termNames: new[] { "DotConfig" },  
        termValues: new[] { "HierSingleSelectionName:.config$" })]  
    ```  
  
     Diese Metadaten definieren Sie die neue UIContext GUID (8B40D5E2-5626-42AE-99EF-3DD1EFF46E7B) und einen Ausdruck verweist auf einen einzelnen Begriff "DotConfig". Der Begriff "DotConfig" auf "true" ausgewertet wird, wenn die aktuelle Auswahl in der aktiven Hierarchie einen Namen aufweist, der Muster des regulären Ausdrucks übereinstimmt "\\config$" (endet mit ".config"). Der Wert "(Standard) definiert einen optionalen Namen für die Regel, die beim Debuggen hilfreich.  
  
     Die Werte des Attributs werden während des Buildvorgangs danach generiert Pkgdef hinzugefügt.  
  
2.  Fügen Sie in der VSCT-Datei für die TestPackage Befehle das Flag "DynamicVisibility" auf die entsprechenden Befehle aus:  
  
    ```xml  
    <CommandFlag>DynamicVisibility</CommandFlag>  
    ```  
  
3.  Klicken Sie im Bereich Sichtbarkeiten von der VSCT binden Sie die entsprechenden Befehle, um die neue UIContext GUID in #1 definiert:  
  
    ```xml  
    <VisibilityConstraints>   
        <VisibilityItem guid="guidTestPackageCmdSet" id="TestId"  context="guidTestUIContext"/>   
    </VisibilityConstraints>  
    ```  
  
4.  Fügen Sie im Abschnitt Symbole der Definition der UIContext hinzu:  
  
    ```xml  
    <GuidSymbol name="guidTestUIContext" value="{8B40D5E2-5626-42AE-99EF-3DD1EFF46E7B}" />  
    ```  
  
     Die Kontextmenübefehle für *.config-Dateien werden jetzt sichtbar sein, nur, wenn das ausgewählte Element im Projektmappen-Explorer eine Datei ".config wird" und das Paket wird nicht geladen werden, bis eine Kopie dieser Befehle ausgewählt ist.  
  
 Als Nächstes verwenden wir einen Debugger um zu bestätigen, dass das Paket lädt nur wenn wir das erwartete. So debuggen Sie TestPackage:  
  
1.  Legen Sie einen Haltepunkt der <xref:Microsoft.VisualStudio.Shell.Package.Initialize%2A> Methode.  
  
2.  Die TestPackage erstellen und mit dem Debuggen beginnen.  
  
3.  Erstellen Sie ein Projekt oder öffnen Sie eine.  
  
4.  Wählen Sie alle Dateien mit einer anderen Erweiterung als config. Der Haltepunkt sollte nicht erreicht werden.  
  
5.  Wählen Sie die Datei "App.config".  
  
 Die TestPackage lädt und hält am Haltepunkt an.  
  
## <a name="adding-more-rules-for-ui-context"></a>Weitere Regeln hinzufügen für Benutzeroberflächenkontext  
 Da die UI-Kontextregeln boolesche Ausdrücke sind, können Sie restriktivere Regeln für einen Kontext UI hinzufügen. Beispielsweise können Sie in der oben genannten Benutzeroberflächenkontext angeben, dass die Regel gilt nur, wenn eine Projektmappe mit einem Projekt geladen wird. Auf diese Weise werden die Befehle nicht angezeigt, wenn Sie eine Sicherungskopie der Datei ".config", als eigenständige Datei und nicht als Teil des Projekts öffnen.  
  
```csharp  
[ProvideAutoLoad(TestPackage.UIContextGuid)]      
[ProvideUIContextRule(TestPackage.UIContextGuid,    
    name: "Test auto load",  
    expression: "(SingleProject | MultipleProjects) & DotConfig",    
    termNames: new[] { "SingleProject", "MultipleProjects","DotConfig" },     
    termValues: new[] { VSConstants.UICONTEXT_SolutionHasSingleProject_string , VSConstants.UICONTEXT_SolutionHasMultipleProjects_string , "HierSingleSelectionName:.config$" })]  
```  
  
 Der Ausdruck verweist jetzt drei Begriffe. Die ersten beiden Begriffe, "SingleProject" und "MultipleProjects", beziehen sich auf anderen bekannten Benutzeroberflächen-Kontexte (durch ihren GUIDs). Der dritte Ausdruck ist "DotConfig" das regelbasierte Benutzeroberflächenkontext wir zuvor definiert.  
  
## <a name="delayed-activation"></a>Verzögerte Aktivierung  
 Regeln können eine optionale "Verzögerung" haben. Die Verzögerung in Millisekunden angegeben. Falls vorhanden, führt der Verzögerung auf, die Aktivierung oder Deaktivierung von einer Regel-UI-Kontext, der durch dieses Zeitintervalls verzögert werden. Wenn die regeländerungen vor dem Ablauf der Verzögerung zu sichern, erfolgt dann keine Aktion. Dieser Mechanismus kann "staffeln Sie Initialisierungsschritte - vor allem eine einmalige Initialisierung ohne Rückgriff auf Zeitgeber, oder Registrieren für Benachrichtigungen im Leerlauf" verwendet werden.  
  
 Beispielsweise können Sie Ihre Testregel laden, um eine Verzögerung von 100 Millisekunden angeben:  
  
```csharp  
[ProvideAutoLoad(TestPackage.UIContextGuid)]  
[ProvideUIContextRule(TestPackage.UIContextGuid,   
    name: "Test auto load",  
    expression: "DotConfig",   
    termNames: new[] { "DotConfig" },  
    termValues: new[] { "HierSingleSelectionName:.config$" },   
    delay: 100)]  
```  
  
## <a name="term-types"></a>Begriff-Typen  
 Hier werden die verschiedenen Typen von Ausdrücken, die unterstützt werden:  
  
|||  
|-|-|  
|{Nnnnnnnn-Nnnn-Nnnn-Nnnn-Nnnnnnnnnnnn}|Die GUID bezieht sich auf ein UI-Kontext. Der Begriff werden "true", wann immer der Benutzeroberflächenkontext aktiv und "false" ist.|  
|HierSingleSelectionName:\<Muster >|Der Begriff wird "true" sein, wenn die Auswahl in der aktiven Hierarchie ein einzelnes Element ist und der Namen des ausgewählten Elements den regulären Ausdruck von .net entspricht "Pattern" angegeben.|  
|UserSettingsStoreQuery:\<Abfrage >|"Abfrage" stellt einen vollständigen Pfad in den Speicher des Benutzers-Einstellungen der auf einen Wert ungleich 0 (null) ausgewertet werden muss. Die Abfrage wird in eine "Auflistung" und "PropertyName" auf der letzten Schrägstrich aufgeteilt.|  
|ConfigSettingsStoreQuery:\<Abfrage >|"Abfrage" stellt einen vollständigen Pfad in den Konfigurationsspeicher für die Einstellungen der auf einen Wert ungleich 0 (null) ausgewertet werden muss. Die Abfrage wird in eine "Auflistung" und "PropertyName" auf der letzten Schrägstrich aufgeteilt.|  
|ActiveProjectFlavor:\<ProjectTypeGuid >|Der Begriff wird "true" werden, wenn das aktuell ausgewählte Projekt flavored ist (aggregiert) und verfügt über ein Flavor entsprechen den jeweiligen Projekttyp GUID.|  
|ActiveEditorContentType:\<ContentType >|Der Begriff wird "true" sein, wenn das ausgewählte Dokument mit einem Text-Editor mit dem angegebenen Inhaltstyp ist.|  
|ActiveProjectCapability:\<Ausdruck >|Der Begriff ist "true", wenn aktiven Projektfunktionen mit dem angegebenen Ausdruck übereinstimmt. Ein Ausdruck kann etwa VB &#124; CSharp|  
|SolutionHasProjectCapability:\<Ausdruck >|Oben ähnlich, aber Begriff wird "true", bei der Lösung alle anderen geladenen Projekt aufweist, das dem Ausdruck übereinstimmt.|  
|SolutionHasProjectFlavor:\<ProjectTypeGuid >|Der Begriff werden "true", eine Lösung Projekt, das flavored ist (aggregiert) hat, und verfügt über ein Flavor entsprechen den jeweiligen Projekttyp GUID.|


  
## <a name="compatibility-with-cross-version-extension"></a>Kompatibilität mit der versionsübergreifenden-Erweiterung  
 Regel, die je UI Kontexten ist ein neues Feature in Visual Studio 2015 und würde nicht mit früheren Versionen portiert werden. Dadurch wird ein Problem mit den Erweiterungen/Paketen, die mehrere Versionen von Visual Studio, die in Visual Studio 2013 automatisch geladen und früher werden müssten ausgerichtet, sondern können hiervon profitieren regelbasiert UI Kontexte, um zu verhindern, wird automatisch geladen in Visual Studio 2015 erstellt.  
  
 Um solche Pakete unterstützen, bieten AutoLoadPackages Einträge in der Registrierung nun ein Flag im Feld "Wert", um anzugeben, dass der Eintrag in Visual Studio 2015 und höher übersprungen werden soll. Dies kann geschehen, indem eine Flags-Option zum Hinzufügen <xref:Microsoft.VisualStudio.Shell.PackageAutoLoadFlags>. VSPackages können jetzt hinzufügen **SkipWhenUIContextRulesActive** option, um ihre <xref:Microsoft.VisualStudio.Shell.ProvideAutoLoadAttribute> Attribut, um anzugeben, der Eintrag in Visual Studio 2015 und höher ignoriert werden sollen.  
  
## <a name="extensible-ui-context-rules"></a>Erweiterbare Benutzeroberfläche Kontextregeln  
 In einigen Fällen können keine Pakete statische Benutzeroberflächenkontext Regeln. Nehmen Sie beispielsweise an, dass ein Paket Erweiterbarkeit unterstützen, sodass der Befehlsstatus basierend auf der Editor-Typen, die vom importierten MEF-Anbieter unterstützt werden. Der Befehl ist aktiviert, wenn eine Erweiterung, die den aktuellen "Edit" unterstützen. In solchen Fällen kann nicht das Paket selbst eine statische Benutzeroberflächenkontext Regel verwenden, da die Begriffe ändern würde je nachdem welche, die MEF-Erweiterungen zur Verfügung stehen.  
  
 Um solche Pakete unterstützen, unterstützen regelbasiert UI Kontexten einen hartcodierter Ausdruck "*", die angibt, dass alle sen verknüpft es mit oder. Dies ermöglicht das Masterpaket definieren, dass eine bekannte Regel Benutzeroberflächenkontext beruhen verwendet und der Befehlsstatus in diesem Kontext. Danach kann alle MEF-Erweiterungen, die als Ziel für das Masterpaket die Begriffe für Editoren hinzufügen unterstützten ohne Auswirkungen auf die anderen Begriffe oder der master-Ausdruck.  
  
 Der Konstruktor <xref:Microsoft.VisualStudio.Shell.ProvideExtensibleUIContextRuleAttribute.%23ctor%2A> Dokumentation zeigt die Syntax für extensible Benutzeroberflächenkontext Regeln.