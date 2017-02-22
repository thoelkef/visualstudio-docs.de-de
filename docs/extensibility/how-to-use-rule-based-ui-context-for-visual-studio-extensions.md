---
title: "Gewusst wie: Verwenden Sie regelbasierte Benutzeroberfl&#228;chenkontext f&#252;r Visual Studio-Erweiterungen | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 8dd2cd1d-d8ba-49b9-870a-45acf3a3259d
caps.latest.revision: 7
caps.handback.revision: 6
ms.author: "gregvanl"
---
# Gewusst wie: Verwenden Sie regelbasierte Benutzeroberfl&#228;chenkontext f&#252;r Visual Studio-Erweiterungen
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Visual Studio ermöglicht das Laden von VSPackages, wenn bestimmte bekannte <xref:Microsoft.VisualStudio.Shell.UIContext>s aktiviert werden. Diese Benutzeroberflächen\-Kontexte sind nicht sehr präzise umfassendere, Autoren keine Wahl lassen jedoch um eine verfügbare Benutzeroberflächenkontext auswählen, die vor dem aktiviert sie wollten das VSPackage geladen. Eine Liste der bekannten Benutzeroberflächen\-Kontexte, finden Sie unter <xref:Microsoft.VisualStudio.Shell.KnownUIContexts>.  
  
 Laden von Paketen kann Auswirkungen auf die Leistung und früher, als sie bei Bedarf laden wird nicht empfohlen. Visual Studio 2015 vorgestellt regelbasierte Benutzeroberflächen\-Kontexte, ein Mechanismus, können Autoren zum Definieren der präzisen Bedingungen, unter dem einem Benutzeroberflächenkontext wird aktiviert und zugehörigen VSPackages geladen.  
  
## Regelbasierte Benutzeroberflächenkontext  
 Eine "Regel" besteht aus einem neuen Benutzeroberflächenkontext \(eine GUID\) und ein boolescher Ausdruck, der ein oder mehrere "Ausdrücke" verweist auf zusammen mit logischen "und", "oder", "not" Vorgänge. "Begriffe" werden dynamisch zur Laufzeit ausgewertet und des Ausdrucks erneut ausgewertet, wenn dessen Begriffe ändert. Wenn der Ausdruck True ergibt, wird die zugeordneten UI\-Kontext aktiviert. Andernfalls ist der UI\-Kontext deaktiviert.  
  
 Regelbasierte Benutzeroberflächenkontext kann auf verschiedene Arten verwendet werden:  
  
1.  Geben Sie die Sichtbarkeit Einschränkungen für Befehle und Toolfenster. Sie können Windows Befehle\-Tools ausblenden, bis die Benutzeroberflächenkontext Regel erfüllt ist.  
  
2.  Laden Sie als Auto Einschränkungen: Automatisches Laden Pakete nur, wenn die Regel erfüllt ist  
  
3.  Verzögerter Vorgang: verzögern, laden erst ein angegebenes Zeitintervall und weiterhin die Regel erfüllt ist.  
  
 Der Mechanismus kann von Visual Studio\-Erweiterung verwendet werden.  
  
## Erstellen Sie eine regelbasierte Benutzeroberflächenkontext  
 Angenommen Sie, Sie haben die Erweiterung TestPackage, das einen Menübefehl bietet das gilt nur für Dateien mit der Erweiterung ".config" aufgerufen. Vor dem VS2015, war die beste Option TestPackage Laden beim <xref:Microsoft.VisualStudio.Shell.KnownUIContexts.SolutionExistsAndFullyLoadedContext%2A> Benutzeroberflächenkontext aktiviert wurde. Dies ist nicht effizient, da die geladene Projektmappe nicht selbst eine .config\-Datei enthalten. Lassen Sie uns finden Sie unter wie Benutzeroberflächenkontext regelbasierte verwendet werden kann, um einem Benutzeroberflächenkontext nur, wenn eine Datei mit der Config\-Erweiterung zu aktivieren ausgewählt ist, und Laden TestPackage, wenn diese Benutzeroberflächenkontext aktiviert ist.  
  
1.  Definieren Sie eine neue UIContext\-GUID und der VSPackage\-Klasse hinzufügen <xref:Microsoft.VisualStudio.Shell.ProvideAutoLoadAttribute> und <xref:Microsoft.VisualStudio.Shell.ProvideUIContextRuleAttribute>.  
  
     Zum Beispiel nehmen wir an, eine neue UIContext "UIContextGuid" ist, hinzugefügt werden. Die GUID erstellt \(Sie können eine GUID erstellen, indem Sie auf Extras \-\> Guid erstellen\) "8B40D5E2\-5626\-42AE\-99EF\-3DD1EFF46E7B" ist. Anschließend fügen Sie Folgendes in der Paketklasse:  
  
    ```c#  
    public const string UIContextGuid = "8B40D5E2-5626-42AE-99EF-3DD1EFF46E7B";  
    ```  
  
     Fügen Sie die folgenden, für die Attribute: \(Details zu diesen Attributen werden weiter unten erläutert\)  
  
    ```c#  
    [ProvideAutoLoad(TestPackage.UIContextGuid)]      
    [ProvideUIContextRule(TestPackage.UIContextGuid,  
        name: "Test auto load",   
        expression: "DotConfig",  
        termNames: new[] { "DotConfig" },  
        termValues: new[] { "HierSingleSelectionName:.config$" })]  
    ```  
  
     Diese Metadaten definieren, die neue UIContext GUID \(8B40D5E2\-5626\-42AE\-99EF\-3DD1EFF46E7B\) und einen Ausdruck, der auf einen einzelnen Begriff "DotConfig" verweisen. Der Begriff "DotConfig" wird zu True ausgewertet, wenn die aktuelle Auswahl in der aktiven Hierarchie einen Namen enthält, der das Muster eines regulären Ausdrucks "\\.config$" \(endet mit ".config"\) übereinstimmt. Der \(standardmäßige\) Wert definiert einen optionalen Namen für die Regel, die beim Debuggen hilfreich.  
  
     Die Werte des Attributs werden während der Buildzeit danach generiert Pkgdef hinzugefügt.  
  
2.  Fügen Sie das Flag "DynamicVisibility" in der VSCT\-Datei für die TestPackage\-Befehle mit den entsprechenden Befehlen:  
  
    ```xml  
    <CommandFlag>DynamicVisibility</CommandFlag>  
    ```  
  
3.  Verknüpfen Sie in den Abschnitt Sichtbarkeiten der VSCT die entsprechenden Befehle, um die neue UIContext GUID in \#1 definiert:  
  
    ```xml  
    <VisibilityConstraints>   
        <VisibilityItem guid="guidTestPackageCmdSet" id="TestId"  context="guidTestUIContext"/>   
    </VisibilityConstraints>  
    ```  
  
4.  Fügen Sie die Definition der UIContext im Abschnitt Symbole:  
  
    ```xml  
    <GuidSymbol name="guidTestUIContext" value="{8B40D5E2-5626-42AE-99EF-3DD1EFF46E7B}" />  
    ```  
  
     Kontextmenübefehle für \*.config\-Dateien werden nun angezeigt werden, nur, wenn das ausgewählte Element im Projektmappen\-Explorer eine ".config"\-Datei wird, und das Paket wird nicht geladen werden, bis eine dieser Befehle ausgewählt ist.  
  
 Als Nächstes verwenden wir einen Debugger um zu bestätigen, dass das Paket lädt nur wenn wir erwartet. So debuggen Sie TestPackage  
  
1.  Legen Sie einen Haltepunkt die <xref:Microsoft.VisualStudio.Shell.Package.Initialize%2A> Methode.  
  
2.  Erstellen Sie die TestPackage und das Debuggen starten.  
  
3.  Ein Projekt erstellen oder öffnen.  
  
4.  Wählen Sie alle Dateien mit einer anderen Erweiterung als config. Der Haltepunkt muss nicht erreicht werden.  
  
5.  Wählen Sie die Datei "App.config".  
  
 Der TestPackage lädt und hält am Haltepunkt.  
  
## Weitere Regeln hinzufügen für Benutzeroberflächenkontext  
 Da der UI\-Kontextregeln boolesche Ausdrücke sind, können Sie für einen Kontext für die Benutzeroberfläche eingeschränktere Regeln hinzufügen. In den obigen Benutzeroberflächenkontext können Sie beispielsweise angeben, dass die Regel gilt nur, wenn eine Projektmappe ein Projekt geladen wird. Auf diese Weise wird nicht die Befehle angezeigt, wenn Sie eine ".config"\-Datei als eigenständige Datei, nicht als Teil eines Projekts öffnen.  
  
```c#  
[ProvideAutoLoad(TestPackage.UIContextGuid)]      
[ProvideUIContextRule(TestPackage.UIContextGuid,    
    name: "Test auto load",  
    expression: "(SingleProject | MultipleProjects) & DotConfig",    
    termNames: new[] { "SingleProject", "MultipleProjects","DotConfig" },     
    termValues: new[] { VSConstants.UICONTEXT_SolutionHasSingleProject_string , VSConstants.UICONTEXT_SolutionHasMultipleProjects_string , "HierSingleSelectionName:.config$" })]  
```  
  
 Der Ausdruck verweist jetzt drei Begriffe. Die ersten beiden Begriffe, "SingleProject" und "MultipleProjects", finden Sie in anderen bekannten Benutzeroberflächen\-Kontexte \(anhand ihrer GUIDs\). Der dritte Ausdruck ist "DotConfig" der zuvor definierten Benutzeroberflächenkontext regelbasierte.  
  
## Verzögerte Aktivierung  
 Regeln können eine optionale "Verzögerung" enthalten. Die Verzögerung wird in Millisekunden angegeben. Falls vorhanden, wird die Verzögerung der Aktivierung oder Deaktivierung des Benutzeroberflächenkontext für einer Regel, die durch dieses Zeitintervalls verzögert werden. Wenn die regeländerungen vor dem Ablauf der Verzögerung zu sichern, geschieht dann nichts. Dieser Mechanismus kann verwendet werden, um "Initialisierungsschritte \- insbesondere einmalige Initialisierung ohne Timer oder Registrierung für Benachrichtigungen im Leerlauf staffeln".  
  
 Beispielsweise können Sie die Regel Test laden, um eine Verzögerung von 100 Millisekunden angeben:  
  
```c#  
[ProvideAutoLoad(TestPackage.UIContextGuid)]  
[ProvideUIContextRule(TestPackage.UIContextGuid,   
    name: "Test auto load",  
    expression: "DotConfig",   
    termNames: new[] { "DotConfig" },  
    termValues: new[] { "HierSingleSelectionName:.config$" },   
    delay: 100)]  
```  
  
## Begriff\-Typen  
 Hier werden die verschiedenen Typen von Begriff, die unterstützt werden:  
  
|||  
|-|-|  
|{Nnnnnnnn\-Nnnn\-Nnnn\-Nnnn\-Nnnnnnnnnnnn}|Die GUID bezieht sich auf ein UI\-Kontext. Der Begriff ist true, wenn die Benutzeroberflächenkontext aktiv, andernfalls false ist.|  
|HierSingleSelectionName: \< Pattern \>|Der Begriff werden true, wenn die Auswahl in der aktiven Hierarchie ein einzelnes Element ist und der Namen des ausgewählten Elements dem regulären Ausdrücken durch "Pattern" angegeben entspricht.|  
|UserSettingsStoreQuery: \< Abfrage \>|"Abfrage" stellt einen vollständigen Pfad in den Speicher des Benutzers Einstellungen der auf einen Wert ungleich NULL ausgewertet werden muss. Die Abfrage wird in eine "Auflistung" und "PropertyName" auf den letzten Schrägstrich aufgeteilt.|  
|ConfigSettingsStoreQuery: \< Abfrage \>|"Abfrage" stellt einen vollständigen Pfad in der Konfigurationsspeicher für die Einstellungen der auf einen Wert ungleich NULL ausgewertet werden muss. Die Abfrage wird in eine "Auflistung" und "PropertyName" auf den letzten Schrägstrich aufgeteilt.|  
|ActiveProjectFlavor: \< ProjectTypeGuid \>|Der Begriff "true" werden, sobald das aktuell ausgewählte Projekt flavored ist \(aggregiert\) und verfügt über einen Typ entsprechen den jeweiligen Projekttyp GUID.|  
|ActiveEditorContentType: \< ContentType \>|Der Begriff ist true, wenn das ausgewählte Dokument mit einem Text\-Editor mit dem angegebenen Inhaltstyp ist.|  
|ActiveProjectCapability: \< Ausdruck \>|Der Begriff ist true, wenn aktive Projektfunktionen den bereitgestellten Ausdruck übereinstimmt. Ein Ausdruck kann etwa VB &#124; CSharp|  
|SolutionHasProjectCapability: \< Ausdruck \>|Ähnlich wie oben, aber Begriff ist true, wenn Lösung alle geladenen Projekt, das mit dem Ausdruck übereinstimmt.|  
  
## Mit der Erweiterung Versionsübergreifende Kompatibilität  
 Regel basierend Benutzeroberflächen\-Kontexte ist ein neues Feature in Visual Studio 2015 und würde nicht mit früheren Versionen portiert werden. Dies führt zu einem Problem mit Erweiterungen\/Pakete, die als Ziel mehrere Versionen von Visual Studio automatisch geladen werden, in Visual Studio 2013 und frühere Versionen werden musste, aber von regelbasiert Benutzeroberflächen\-Kontexte, um zu verhindern, wird automatisch geladen in Visual Studio 2015 profitieren können.  
  
 Um diese Pakete unterstützen, bieten AutoLoadPackages Einträge in der Registrierung jetzt ein Flag im Feld "Wert" an, dass der Eintrag in Visual Studio 2015 und höher übersprungen werden soll. Dies kann durch Hinzufügen einer Flags\-Option auf <xref:Microsoft.VisualStudio.Shell.PackageAutoLoadFlags>. VSPackages können jetzt hinzufügen **SkipWhenUIContextRulesActive** option, um ihre <xref:Microsoft.VisualStudio.Shell.ProvideAutoLoadAttribute> Attribut an, dass der Eintrag in Visual Studio 2015 und höher ignoriert werden sollen.  
  
## Erweiterbare Benutzeroberfläche Kontextregeln  
 In einigen Fällen können keine Pakete statische Benutzeroberflächenkontext Regeln. Nehmen wir beispielsweise an, dass ein Paket Erweiterbarkeit unterstützen, so, dass der Befehlsstatus basierend auf Editor\-Typen, die von importierten MEF\-Anbieter unterstützt werden. Der Befehl ist aktiviert, es ist eine Erweiterung, die den aktuellen bearbeiten\-Typ unterstützen. In solchen Fällen kann nicht das Paket selbst eine statische Benutzeroberflächenkontext Regel verwenden, da die Begriffe ändern würde, je nachdem welche, die MEF Erweiterungen verfügbar sind.  
  
 Um diese Pakete unterstützen, unterstützen regelbasiert Benutzeroberflächen\-Kontexte einen hartcodierter Ausdruck "\*", der angibt, alle Begriffe unten wird mit angehören oder. Dies ermöglicht das Masterpaket definieren eine bekannte Regel Benutzeroberflächenkontext Grundlage und binden den Befehl Zustand an diesen Kontext. Jeder MEF\-Erweiterung für das Masterpaket vorgesehenen kann anschließend seine Ausdrücke für Editoren hinzufügen ohne Beeinträchtigung der anderen Begriffe oder der master\-Ausdruck unterstützt.  
  
 Der Konstruktor <xref:Microsoft.VisualStudio.Shell.ProvideExtensibleUIContextRuleAttribute.%23ctor%2A> Dokumentation zeigt die Syntax für erweiterbare Benutzeroberflächenkontext Regeln.