---
title: 'Vorgehensweise: Verwenden des regelbasierten Benutzeroberflächenkontexts für Visual Studio-Erweiterungen | Microsoft-Dokumentation'
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 8dd2cd1d-d8ba-49b9-870a-45acf3a3259d
author: gregvanl
ms.author: gregvanl
ms.workload:
- vssdk
ms.openlocfilehash: 720c27b4895abc390926813700bb906c4d0194af
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/02/2019
ms.locfileid: "53824287"
---
# <a name="how-to-use-rule-based-ui-context-for-visual-studio-extensions"></a>Vorgehensweise: Verwenden des regelbasierten Benutzeroberflächenkontexts für Visual Studio-Erweiterungen
Visual Studio ermöglicht das Laden von VSPackages, wenn bestimmte bekannte <xref:Microsoft.VisualStudio.Shell.UIContext>s aktiviert werden. Diese Benutzeroberfläche-Kontexte sind nicht in Ordnung umfassendere, d. h. erweiterungsautoren auf keine andere Möglichkeit jedoch um eine verfügbare UI-Kontext zu übernehmen, die vor dem Zeitpunkt aktiviert sie wollten das VSPackage zu laden. Eine Liste der gut bekannte benutzerschnittstellenkontexte, finden Sie unter <xref:Microsoft.VisualStudio.Shell.KnownUIContexts>.  
  
 Laden von Paketen haben Auswirkungen auf die Leistung aus, und Laden sie früher als erforderlich ist nicht die bewährte Methode. Visual Studio 2015 eingeführt, das Konzept der Benutzeroberflächenkontexte regelbasierten, ein Mechanismus, können Ersteller von Erweiterungen zum Definieren der präzisen Bedingungen, unter dem einen UI-Kontext aktiviert ist und die zugehörigen VSPackages werden geladen.  
  
## <a name="rule-based-ui-context"></a>Regel-basierte Benutzeroberfläche-Kontext  
 Eine "Regel" besteht aus einen neuen UI-Kontext (eine GUID) und ein boolescher Ausdruck, der eine oder mehrere "Terms" verweist auf zusammen mit logischen "und", "or", "not"-Vorgänge. "Terms" dynamisch zur Laufzeit ausgewertet, und der Ausdruck wird erneut ausgewertet, wenn die Bedingungen Änderungen. Wenn der Ausdruck "true" ergibt, wird die zugeordnete UI-Kontext aktiviert. Andernfalls ist der UI-Kontext de-activated.  
  
 Regel-basierte Benutzeroberfläche-Kontext kann auf verschiedene Weise verwendet werden:  
  
1. Geben Sie die Sichtbarkeit von Einschränkungen für Befehle und Toolfenster. Sie können die Windows-Befehle/Tools ausblenden, bis die UI-Kontext Regel erfüllt ist.  
  
2. Als Auto serverlastbeschränkungen: Automatisches Laden Pakete nur, wenn die Regel erfüllt ist.  
  
3. Als Aufgabe verzögert: verzögert geladen werden, bis ein angegebenes Intervall ist verstrichen, und weiterhin die Regel erfüllt ist.  
  
   Der Mechanismus kann von jedem Visual Studio-Erweiterung verwendet werden.  
  
## <a name="create-a-rule-based-ui-context"></a>Erstellen Sie einen regelbasierten UI-Kontext  
 Angenommen, Sie haben eine Erweiterung TestPackage aufgerufen, das einem Menübefehl, bietet gilt nur für Dateien mit *config* Erweiterung. Vor Visual Studio 2015, wurde die beste Option zum Laden von TestPackage beim <xref:Microsoft.VisualStudio.Shell.KnownUIContexts.SolutionExistsAndFullyLoadedContext%2A> UI-Kontext wurde aktiviert. Laden TestPackage auf diese Weise ist nicht effizient, da die geladene Projektmappe selbst möglicherweise keinen enthält eine *config* Datei. Diese Schritte zeigen, wie Regeln-basierte Benutzeroberfläche-Kontext kann verwendet werden, um einen UI-Kontext nur, wenn eine Datei mit der Aktivierung *config* Erweiterung aktiviert ist, und Laden Sie TestPackage, wenn diese UI-Kontext aktiviert ist.  
  
1. Definieren Sie eine neue UIContext-GUID und die VSPackage-Klasse hinzufügen <xref:Microsoft.VisualStudio.Shell.ProvideAutoLoadAttribute> und <xref:Microsoft.VisualStudio.Shell.ProvideUIContextRuleAttribute>.  
  
    Beispielsweise nehmen wir an einer neuen UIContext "UIContextGuid" wird hinzugefügt werden. Die GUID erstellt (Sie können eine GUID erstellen, durch Klicken auf **Tools** > **GUID erstellen**) ist "8B40D5E2-5626-42AE-99EF-3DD1EFF46E7B". Anschließend fügen Sie die folgende Deklaration in der Paketklasse hinzu:  
  
   ```csharp  
   public const string UIContextGuid = "8B40D5E2-5626-42AE-99EF-3DD1EFF46E7B";  
   ```  
  
    Fügen Sie für die Attribute die folgenden Werte ein: (Details zu diesen Attributen werden weiter unten erläutert)  
  
   ```csharp  
   [ProvideAutoLoad(TestPackage.UIContextGuid)]      
   [ProvideUIContextRule(TestPackage.UIContextGuid,  
       name: "Test auto load",   
       expression: "DotConfig",  
       termNames: new[] { "DotConfig" },  
       termValues: new[] { "HierSingleSelectionName:.config$" })]  
   ```  
  
    Diese Metadaten definieren, die neue UIContext-GUID (8B40D5E2-5626-42AE-99EF-3DD1EFF46E7B) und einen Ausdruck verweisen auf einen einzelnen Begriff "DotConfig". Der Begriff "DotConfig" auf "true" ausgewertet wird, wenn die aktuelle Auswahl in der aktiven Hierarchie einen Namen verfügt, das Muster des regulären Ausdrucks entspricht "\\config$" (endet mit *config*). Der Wert (Standard) definiert einen optionalen Namen für die Regel, die beim Debuggen nützlich.  
  
    Die Werte des Attributs werden generiert, bei der Erstellung danach Pkgdef hinzugefügt.  
  
2. Fügen Sie in der VSCT-Datei für die TestPackage Befehle auf den entsprechenden Befehlen das Flag "DynamicVisibility" hinzu:  
  
   ```xml  
   <CommandFlag>DynamicVisibility</CommandFlag>  
   ```  
  
3. Klicken Sie im Abschnitt Sichtbarkeiten des der VSCT verknüpfen Sie die entsprechenden Befehle, um die neue UIContext-GUID in #1 definiert:  
  
   ```xml  
   <VisibilityConstraints>   
       <VisibilityItem guid="guidTestPackageCmdSet" id="TestId"  context="guidTestUIContext"/>   
   </VisibilityConstraints>  
   ```  
  
4. Fügen Sie im Abschnitt "Symbole" die Definition der UIContext hinzu:  
  
   ```xml  
   <GuidSymbol name="guidTestUIContext" value="{8B40D5E2-5626-42AE-99EF-3DD1EFF46E7B}" />  
   ```  
  
    Jetzt die Kontextmenübefehle  *\*config* Dateien werden sichtbare nur, wenn das ausgewählte Element im Projektmappen-Explorer ist ein *config* -Datei und das Paket werden nicht werden geladen, bis eine solche Befehle ausgewählt ist.  
  
   Als Nächstes verwenden Sie einen Debugger, um sicherzustellen, dass das Paket lädt nur wenn Sie es erwarten. So debuggen Sie TestPackage:  
  
5. Festlegen eines Haltepunkts in der <xref:Microsoft.VisualStudio.Shell.Package.Initialize%2A> Methode.  
  
6. Erstellen Sie die TestPackage, und starten Sie das Debuggen.  
  
7. Erstellen Sie ein Projekt oder öffnen Sie eine.  
  
8. Wählen Sie alle Dateien mit der Erweiterung außer *config*. Der Haltepunkt sollte nicht erreicht werden.  
  
9. Wählen Sie die *"App.config"* Datei.  
  
   Die TestPackage lädt und die Ausführung am Haltepunkt beendet.  
  
## <a name="add-more-rules-for-ui-context"></a>Fügen Sie weitere Regeln für die UI-Kontext  
 Da die UI-Kontext Regeln boolesche Ausdrücke sind, können Sie restriktivere Regeln für einen UI-Kontext hinzufügen. In den oben genannten UI-Kontext, können Sie beispielsweise angeben, dass die Regel gilt nur, wenn eine Projektmappe mit einem Projekt geladen wird. Auf diese Weise können die Befehle wird nicht angezeigt, wenn Sie öffnen ein *config* Datei als eigenständige Datei und nicht als Teil eines Projekts.  
  
```csharp  
[ProvideAutoLoad(TestPackage.UIContextGuid)]      
[ProvideUIContextRule(TestPackage.UIContextGuid,    
    name: "Test auto load",  
    expression: "(SingleProject | MultipleProjects) & DotConfig",    
    termNames: new[] { "SingleProject", "MultipleProjects","DotConfig" },     
    termValues: new[] { VSConstants.UICONTEXT_SolutionHasSingleProject_string , VSConstants.UICONTEXT_SolutionHasMultipleProjects_string , "HierSingleSelectionName:.config$" })]  
```  
  
 Der Ausdruck verweist jetzt drei Begriffe. Die ersten beiden Begriffe, "SingleProject" und "MultipleProjects", finden Sie in anderen gut bekannte Benutzerschnittstellenkontexte (anhand ihrer GUIDs). Der dritte Begriff ist, ist "DotConfig" den regelbasierte UI-Kontext oben in diesem Artikel definiert.  
  
## <a name="delayed-activation"></a>Verzögerte Aktivierung  
 Regeln können eine optionale "Verzögerung" enthalten. Es ist die Verzögerung in Millisekunden angegeben. Falls vorhanden, wird die Verzögerung der Aktivierung oder Deaktivierung des UI-Kontext an einer Regel, die durch dieses Zeitintervalls verzögert werden. Wenn Änderungen an den zu bevor das Verzögerungsintervall sichern, passiert dann nichts. Dieser Mechanismus kann verwendet werden, um "Initialisierungsschritte – insbesondere einmalige Initialisierung, ohne auf Zeitgeber verlassen, oder Registrieren für im Leerlauf Benachrichtigungen staffeln".  
  
 Beispielsweise können Sie Ihre Test-Load-Regel, um eine Verzögerung von 100 Millisekunden angeben:  
  
```csharp  
[ProvideAutoLoad(TestPackage.UIContextGuid)]  
[ProvideUIContextRule(TestPackage.UIContextGuid,   
    name: "Test auto load",  
    expression: "DotConfig",   
    termNames: new[] { "DotConfig" },  
    termValues: new[] { "HierSingleSelectionName:.config$" },   
    delay: 100)]  
```  
  
## <a name="term-types"></a>Laufzeit-Typen  
 Hier sind die verschiedenen Typen von Begriff, die unterstützt werden:  
  
|Begriff|Beschreibung|  
|-|-|  
|{Nnnnnnnn-Nnnn-Nnnn-Nnnn-Nnnnnnnnnnnn}|Die GUID bezieht sich auf einen UI-Kontext. Der Begriff ist true, wenn der UI-Kontext aktiv und "false" ist.|  
|HierSingleSelectionName:\<Muster >|Der Begriff wird "true" sein, wenn die Auswahl in der aktiven Hierarchie ein einzelnes Element ist und der Namen des ausgewählten Elements dem regulären .net-Ausdruck, die durch "Pattern" angegeben entspricht.|  
|UserSettingsStoreQuery:\<Abfrage >|"Query" stellt einen vollständigen Pfad dar, in den Speicher für benutzereinstellungen, die einen Wert ungleich NULL ergeben muss. Die Abfrage wird in eine "Auflistung" und "Eigenschaftsname" auf den letzten Schrägstrich geteilt.|  
|ConfigSettingsStoreQuery:\<Abfrage >|"Query" stellt einen vollständigen Pfad dar, in dem Konfigurationsspeicher für die Einstellungen, die einen Wert ungleich NULL ergeben muss. Die Abfrage wird in eine "Auflistung" und "Eigenschaftsname" auf den letzten Schrägstrich geteilt.|  
|ActiveProjectFlavor:\<ProjectTypeGuid >|Der Begriff wird "true" werden, wenn das aktuell ausgewählte Projekt flavored ist (aggregiert) und verfügt über eine Flavor Übereinstimmung den angegebenen Projekttyp-GUID.|  
|ActiveEditorContentType:\<ContentType >|Der Ausdruck ist true, wenn das ausgewählte Dokument mit einem Text-Editor mit dem angegebenen Inhaltstyp ist.|  
|ActiveProjectCapability:\<Ausdruck >|Der Begriff ist "true", wenn das aktive Projektfunktionen mit dem angegebenen Ausdruck übereinstimmen. Ein Ausdruck kann sein, etwa VB &#124; CSharp.|  
|SolutionHasProjectCapability:\<Ausdruck >|Ähnlich wie im oben genannten jedoch Ausdruck ist true, wenn Lösung alle geladenes Projekt, das mit dem Ausdruck übereinstimmt.|  
|SolutionHasProjectFlavor:\<ProjectTypeGuid >|Der Begriff ist true, wenn eine Lösung verfügt über Projekt, das flavored ist (aggregiert) und verfügt über eine Flavor Übereinstimmung den angegebenen Projekttyp GUID.|


  
## <a name="compatibility-with-cross-version-extension"></a>Kompatibilität mit versionsübergreifende-Erweiterung  
 Regel-basierte Benutzeroberfläche-Kontexte ist ein neues Feature in Visual Studio 2015 und würde nicht mit früheren Versionen portiert werden. Portieren nicht mit früheren Versionen wird ein Problem mit den Erweiterungen/Paketen, die mehrere Versionen von Visual Studio erstellt. Diese Versionen werden, automatisch geladen werden, in Visual Studio 2013 und frühere Versionen, aber können von Benutzeroberflächen-Kontexten regelbasierte, um zu verhindern, wird automatisch geladen in Visual Studio 2015 profitieren.  
  
 Um diese Pakete unterstützen, können AutoLoadPackages Einträge in der Registrierung jetzt bereitstellen ein Flag im Wertfeld um anzugeben, dass der Eintrag in Visual Studio 2015 und höher übersprungen werden soll. Dies ist möglich durch eine Flags-Option zum Hinzufügen <xref:Microsoft.VisualStudio.Shell.PackageAutoLoadFlags>. VSPackages können jetzt hinzufügen **SkipWhenUIContextRulesActive** die Möglichkeit, ihre <xref:Microsoft.VisualStudio.Shell.ProvideAutoLoadAttribute> Attribut, um anzugeben, der Eintrag in Visual Studio 2015 und höher ignoriert werden sollen.  
  
## <a name="extensible-ui-context-rules"></a>Erweiterbare Benutzeroberfläche-Kontext-Regeln  
 In einigen Fällen können keine Pakete statische Regeln für UI-Kontext. Nehmen wir beispielsweise an, dass ein Paket die Erweiterbarkeit unterstützen, sodass der Befehlsstatus basierend auf der Editor-Typen, die vom importierten MEF-Anbieter unterstützt werden. Der Befehl ist aktiviert, wenn es ist eine Erweiterung, die den aktuellen "Edit" unterstützen. In solchen Fällen kann nicht das Paket selbst eine statische Regel für die UI-Kontext verwenden, da die Bedingungen ändern würde je nach der, die MEF-Erweiterungen verfügbar sind.  
  
 Um diese Pakete unterstützen, unterstützen die Benutzeroberflächenkontexte regelbasierte einen hartcodierter Ausdruck "*", der angibt, alle der untenstehenden Bestimmungen werden mit angehören oder. Dies ermöglicht das Masterpaket einen bekannten regelbasierte UI-Kontext definieren, und binden den Befehl Zustand an diesen Kontext. Anschließend kann alle MEF-Erweiterungen, die als Ziel für das Masterpaket die Nutzungsbedingungen für Editoren hinzufügen, die sie ohne Auswirkungen auf andere Begriffe oder der master-Ausdruck unterstützt.  
  
 Der Konstruktor <xref:Microsoft.VisualStudio.Shell.ProvideExtensibleUIContextRuleAttribute.%23ctor%2A> die Dokumentation zeigt die Syntax für die erweiterbare Benutzeroberfläche-Kontext-Regeln.