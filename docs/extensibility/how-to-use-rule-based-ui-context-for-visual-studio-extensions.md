---
title: 'Gewusst wie: Verwenden des regelbasierten UI-Kontexts für Visual Studio-Erweiterungen | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 8dd2cd1d-d8ba-49b9-870a-45acf3a3259d
author: acangialosi
ms.author: anthc
ms.workload:
- vssdk
ms.openlocfilehash: de1a1e0a2022482433f81b0b2810b0d201ab7b8f
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/06/2020
ms.locfileid: "80710594"
---
# <a name="how-to-use-rule-based-ui-context-for-visual-studio-extensions"></a>Gewusst wie: Verwenden des regelbasierten UI-Kontexts für Visual Studio-Erweiterungen

Visual Studio ermöglicht das Laden von <xref:Microsoft.VisualStudio.Shell.UIContext>VSPackages, wenn bestimmte bekannte s aktiviert sind. Diese UI-Kontexte sind jedoch nicht feinkörnig, sodass Erweiterungsautoren keine andere Wahl haben, als einen verfügbaren UI-Kontext auszuwählen, der vor dem Punkt aktiviert wird, an dem das VSPackage wirklich geladen werden soll. Eine Liste bekannter UI-Kontexte finden <xref:Microsoft.VisualStudio.Shell.KnownUIContexts>Sie unter .

Das Laden von Paketen kann auswirkungent sich auf die Leistung, und das Laden früher als erforderlich ist nicht die bewährte Methode. Visual Studio 2015 führte das Konzept der regelbasierten UI-Kontexte ein, ein Mechanismus, mit dem Erweiterungsautoren die genauen Bedingungen definieren können, unter denen ein UI-Kontext aktiviert und zugeordnete VSPackages geladen werden.

## <a name="rule-based-ui-context"></a>Regelbasierter UI-Kontext

Eine "Regel" besteht aus einem neuen UI-Kontext (einer GUID) und einem booleschen Ausdruck, der auf ein oder mehrere "Terms" in Kombination mit logischen "und", "oder", "nicht" Operationen verweist. "Begriffe" werden zur Laufzeit dynamisch ausgewertet, und der Ausdruck wird neu ausgewertet, wenn sich einer seiner Begriffe ändert. Wenn der Ausdruck als true ausgewertet wird, wird der zugeordnete UI-Kontext aktiviert. Andernfalls wird der UI-Kontext deaktiviert.

Regelbasierter UI-Kontext kann auf verschiedene Weise verwendet werden:

1. Geben Sie Sichtbarkeitseinschränkungen für Befehle und Werkzeugfenster an. Sie können die Befehle/Tools-Fenster ausblenden, bis die UI-Kontextregel erfüllt ist.

2. Als automatische Ladeeinschränkungen: Pakete nur dann automatisch laden, wenn die Regel erfüllt ist.

3. Als verzögerte Aufgabe: Verzögern Sie das Laden, bis ein angegebenes Intervall überschritten wurde und die Regel weiterhin erfüllt ist.

   Der Mechanismus kann von jeder Visual Studio-Erweiterung verwendet werden.

## <a name="create-a-rule-based-ui-context"></a>Erstellen eines regelbasierten UI-Kontexts
 Angenommen, Sie haben eine Erweiterung namens TestPackage, die einen Menübefehl bietet, der nur für Dateien mit *.config-Erweiterung* gilt. Vor VS2015 war die beste Option, <xref:Microsoft.VisualStudio.Shell.KnownUIContexts.SolutionExistsAndFullyLoadedContext%2A> TestPackage zu laden, wenn UI Context aktiviert wurde. Das Laden von TestPackage auf diese Weise ist nicht effizient, da die geladene Lösung möglicherweise nicht einmal eine *.config-Datei* enthält. Diese Schritte zeigen, wie der regelbasierte UI-Kontext nur verwendet werden kann, um einen UI-Kontext zu aktivieren, wenn eine Datei mit *der Erweiterung .config* ausgewählt ist, und TestPackage zu laden, wenn dieser UI-Kontext aktiviert ist.

1. Definieren Sie eine neue UIContext GUID, <xref:Microsoft.VisualStudio.Shell.ProvideAutoLoadAttribute> <xref:Microsoft.VisualStudio.Shell.ProvideUIContextRuleAttribute>und fügen Sie der VSPackage-Klasse und .

    Angenommen, es wird ein neuer UIContext "UIContextGuid" hinzugefügt. Die erstellte GUID (Sie können eine GUID erstellen, indem Sie auf **Tools** > **Create GUID**klicken ) ist "8B40D5E2-5626-42AE-99EF-3DD1EFF46E7B". Anschließend fügen Sie die folgende Deklaration innerhalb Ihrer Paketklasse hinzu:

   ```csharp
   public const string UIContextGuid = "8B40D5E2-5626-42AE-99EF-3DD1EFF46E7B";
   ```

    Fügen Sie für die Attribute die folgenden Werte hinzu: (Details dieser Attribute werden später erläutert)

   ```csharp
   [ProvideAutoLoad(TestPackage.UIContextGuid)]
   [ProvideUIContextRule(TestPackage.UIContextGuid,
       name: "Test auto load",
       expression: "DotConfig",
       termNames: new[] { "DotConfig" },
       termValues: new[] { "HierSingleSelectionName:.config$" })]
   ```

    Diese Metadaten definieren die neue UIContext GUID (8B40D5E2-5626-42AE-99EF-3DD1EFF46E7B) und einen Ausdruck, der sich auf einen einzelnen Begriff, "DotConfig", bezieht. Der Begriff "DotConfig" wird immer dann als true ausgewertet, wenn die aktuelle\\Auswahl in der aktiven Hierarchie einen Namen hat, der mit dem Muster des regulären Ausdrucks ".config" übereinstimmt (endet mit *.config*). Der Wert (Standard) definiert einen optionalen Namen für die Regel, die für das Debuggen nützlich ist.

    Die Werte des Attributs werden pkgdef hinzugefügt, die während der anschließenden Buildzeit generiert werden.

2. Fügen Sie in der VSCT-Datei für die Befehle des TestPackage den entsprechenden Befehlen das Flag "DynamicVisibility" hinzu:

   ```xml
   <CommandFlag>DynamicVisibility</CommandFlag>
   ```

3. Binden Sie im Abschnitt Visibilities des VSCT die entsprechenden Befehle an die neue UIContext-GUID, die in #1 definiert ist:

   ```xml
   <VisibilityConstraints>
       <VisibilityItem guid="guidTestPackageCmdSet" id="TestId"  context="UIContextGuid"/>
   </VisibilityConstraints>
   ```

4. Fügen Sie im Abschnitt Symbole die Definition des UIContext hinzu:

   ```xml
   <GuidSymbol name="UIContextGuid" value="{8B40D5E2-5626-42AE-99EF-3DD1EFF46E7B}" />
   ```

    Die Kontextmenübefehle für * \*.config-Dateien* sind nur sichtbar, wenn das ausgewählte Element im Projektmappen-Explorer eine *.config-Datei* ist und das Paket erst geladen wird, wenn einer dieser Befehle ausgewählt ist.

   Verwenden Sie als Nächstes einen Debugger, um zu bestätigen, dass das Paket nur geladen wird, wenn Sie dies erwarten. So debuggen Sie TestPackage:

5. Legen Sie einen <xref:Microsoft.VisualStudio.Shell.Package.Initialize%2A> Haltepunkt in der Methode fest.

6. Erstellen Sie das TestPackage, und beginnen Sie mit dem Debuggen.

7. Erstellen Sie ein Projekt oder öffnen Sie es.

8. Wählen Sie eine beliebige Datei mit einer anderen Erweiterung als *.config*aus. Der Haltepunkt sollte nicht getroffen werden.

9. Wählen Sie die *Datei App.Config* aus.

   Das TestPackage wird geladen und stoppt am Haltepunkt.

## <a name="add-more-rules-for-ui-context"></a>Hinzufügen weiterer Regeln für ui Context
 Da es sich bei den UI-Kontextregeln um boolesche Ausdrücke handelt, können Sie eingeschränktere Regeln für einen UI-Kontext hinzufügen. Im obigen UI-Kontext können Sie beispielsweise angeben, dass die Regel nur angewendet wird, wenn eine Projektmappe mit einem Projekt geladen wird. Auf diese Weise werden die Befehle nicht angezeigt, wenn Sie eine *.config-Datei* als eigenständige Datei öffnen, nicht als Teil eines Projekts.

```csharp
[ProvideAutoLoad(TestPackage.UIContextGuid)]
[ProvideUIContextRule(TestPackage.UIContextGuid,
    name: "Test auto load",
    expression: "(SingleProject | MultipleProjects) & DotConfig",
    termNames: new[] { "SingleProject", "MultipleProjects","DotConfig" },
    termValues: new[] { VSConstants.UICONTEXT_SolutionHasSingleProject_string , VSConstants.UICONTEXT_SolutionHasMultipleProjects_string , "HierSingleSelectionName:.config$" })]
```

 Nun bezieht sich der Ausdruck auf drei Begriffe. Die ersten beiden Begriffe ,SingleProject" und "MultipleProjects" beziehen sich auf andere bekannte UI-Kontexte (durch ihre GUIDs). Der dritte Begriff , "DotConfig" ist der regelbasierte UI-Kontext, der weiter oben in diesem Artikel definiert wurde.

## <a name="delayed-activation"></a>Verzögerte Aktivierung
 Regeln können optional "Verzögerung" haben. Die Verzögerung wird in Millisekunden angegeben. Wenn vorhanden, führt die Verzögerung dazu, dass die Aktivierung oder Deaktivierung des UI-Kontexts einer Regel um dieses Zeitintervall verzögert wird. Wenn die Regel vor dem Verzögerungsintervall zurückgeändert wird, geschieht nichts. Dieser Mechanismus kann verwendet werden, um Initialisierungsschritte zu "staggerieren" - insbesondere die einmalige Initialisierung, ohne sich auf Timer zu verlassen oder sich für Benachrichtigungen im Leerlauf zu registrieren.

 Sie können z. B. die Testlastregel für eine Verzögerung von 100 Millisekunden angeben:

```csharp
[ProvideAutoLoad(TestPackage.UIContextGuid)]
[ProvideUIContextRule(TestPackage.UIContextGuid,
    name: "Test auto load",
    expression: "DotConfig",
    termNames: new[] { "DotConfig" },
    termValues: new[] { "HierSingleSelectionName:.config$" },
    delay: 100)]
```

## <a name="term-types"></a>Begriffstypen

Hier sind die verschiedenen Arten von Begriffen, die unterstützt werden:

|Begriff|BESCHREIBUNG|
|-|-|
|nnnnnnnnnn-nnnn-nnnn-nnnn-nnnnnnnnnnnnnn|Die GUID bezieht sich auf einen UI-Kontext. Der Begriff ist immer dann wahr, wenn der UI-Kontext aktiv und andernfalls falsch ist.|
|HierSingleSelectionName:\<Muster>|Der Begriff ist immer dann wahr, wenn die Auswahl in der aktiven Hierarchie ein einzelnes Element ist und der Name des ausgewählten Elements mit dem regulären Ausdruck .Net übereinstimmt, der durch "muster" angegeben wird.|
|UserSettingsStoreQuery:\<Abfrage>|"query" stellt einen vollständigen Pfad in den Speicher der Benutzereinstellungen dar, der zu einem Wert ungleich Null ausgewertet werden muss. Die Abfrage wird beim letzten Schrägstrich in eine "Auflistung" und "propertyName" aufgeteilt.|
|ConfigSettingsStoreQuery:\<Abfrage>|"query" stellt einen vollständigen Pfad in den Konfigurationseinstellungsspeicher dar, der zu einem Wert ungleich Null ausgewertet werden muss. Die Abfrage wird beim letzten Schrägstrich in eine "Auflistung" und "propertyName" aufgeteilt.|
|ActiveProjectFlavor:\<projectTypeGuid>|Der Begriff ist immer dann wahr, wenn das aktuell ausgewählte Projekt aromatisiert (aggregiert) ist und eine Geschmacksanpassung an die angegebene Projekttyp-GUID hat.|
|ActiveEditorContentType:\<contentType>|Der Begriff ist wahr, wenn das ausgewählte Dokument ein Texteditor mit dem angegebenen Inhaltstyp ist. Hinweis: Wenn das ausgewählte Dokument umbenannt wird, wird dieser Begriff erst aktualisiert, wenn die Datei geschlossen und erneut geöffnet wird.|
|ActiveProjectFähigkeit:\<Ausdruck>|Der Begriff ist wahr, wenn aktive Projektfunktionen mit dem bereitgestellten Ausdruck übereinstimmen. Ein Ausdruck kann so etwas wie VB &#124; CSharp sein.|
|SolutionHasProjectCapability:\<Ausdrucks>|Ähnlich wie oben, aber Begriff ist wahr, wenn Lösung hat jedes geladene Projekt, das mit dem Ausdruck übereinstimmt.|
|SolutionHasProjectFlavor:\<projectTypeGuid>|Der Begriff ist immer dann wahr, wenn eine Projektmappe ein Projekt hat, das aromatisiert (aggregiert) ist und eine Geschmacksauflösung hat, die der angegebenen Projekttyp-GUID entspricht.|
|ProjectAddedItem:\<Muster>| Der Begriff ist wahr, wenn eine Datei, die dem "Muster" entspricht, einem Projekt in der geöffneten Soluion hinzugefügt wird.|
|ActiveProjectOutputType:\<outputType>|Der Begriff ist wahr, wenn der Ausgabetyp für aktiveS Projekt genau übereinstimmt.  Der outputType kann eine ganze <xref:Microsoft.VisualStudio.Shell.Interop.__VSPROJOUTPUTTYPE> Zahl oder ein Typ sein.|
|ActiveProjectBuildProperty:\<buildProperty\<>= regex>|Der Begriff ist true, wenn das aktive Projekt die angegebene Buildeigenschaft und den Eigenschaftswert mit dem regex-Filter übereinstimmt. Weitere Informationen zu Buildeigenschaften finden Sie unter [Persistente Daten in MSBuild-Projektdateien.](internals/persisting-data-in-the-msbuild-project-file.md)|
|SolutionHasProjectBuildProperty:\<buildProperty\<>= regex>|Der Begriff ist true, wenn die Projektmappe über ein geladenes Projekt mit der angegebenen Buildeigenschaft verfügt und der Eigenschaftswert mit dem bereitgestellten regex-Filter übereinstimmt.|

## <a name="compatibility-with-cross-version-extension"></a>Kompatibilität mit cross-versionsverlängerung

Regelbasierte UI-Kontexte sind ein neues Feature in Visual Studio 2015 und würden nicht auf frühere Versionen portiert. Wenn sie nicht auf frühere Versionen portiert werden, wird ein Problem mit Erweiterungen/Paketen erstellt, die auf mehrere Versionen von Visual Studio abzielen. Diese Versionen müssten in Visual Studio 2013 und früher automatisch geladen werden, können jedoch von regelbasierten UI-Kontexten profitieren, um zu verhindern, dass sie automatisch in Visual Studio 2015 geladen werden.

Um solche Pakete zu unterstützen, können AutoLoadPackages-Einträge in der Registrierung jetzt ein Flag in seinem Wertfeld bereitstellen, um anzugeben, dass der Eintrag in Visual Studio 2015 und höher übersprungen werden soll. Dies kann durch Hinzufügen einer <xref:Microsoft.VisualStudio.Shell.PackageAutoLoadFlags>Flags-Option zu erfolgen. VSPackages kann nun die Option **SkipWhenUIContextRulesActive** zu ihrem <xref:Microsoft.VisualStudio.Shell.ProvideAutoLoadAttribute> Attribut hinzufügen, um anzugeben, dass der Eintrag in Visual Studio 2015 und höher ignoriert werden soll.
## <a name="extensible-ui-context-rules"></a>Erweiterbare UI-Kontextregeln

Manchmal können Pakete keine statischen UI-Kontextregeln verwenden. Angenommen, Sie verfügen über ein Paket, das die Erweiterbarkeit unterstützt, sodass der Befehlsstatus auf Editortypen basiert, die von importierten MEF-Anbietern unterstützt werden. Der Befehl ist aktiviert, wenn eine Erweiterung vorhanden ist, die den aktuellen Bearbeitungstyp unterstützt. In solchen Fällen kann das Paket selbst keine statische UI-Kontextregel verwenden, da sich die Begriffe je nachdem, welche MEF-Erweiterungen verfügbar sind, ändern würden.

Um solche Pakete zu unterstützen, unterstützen regelbasierte UI-Kontexte einen hartcodierten Ausdruck "*", der angibt, dass alle darunter liegenden Begriffe mit ODER verknüpft werden. Dadurch kann das Masterpaket einen bekannten regelbasierten UI-Kontext definieren und seinen Befehlsstatus an diesen Kontext binden. Danach kann jede MEF-Erweiterung, die für das Masterpaket vorgesehen ist, ihre Begriffe für die unterstützten Editoren hinzufügen, ohne andere Begriffe oder den Masterausdruck zu beeinträchtigen.

Die Konstruktordokumentation <xref:Microsoft.VisualStudio.Shell.ProvideExtensibleUIContextRuleAttribute.%23ctor%2A> zeigt die Syntax für erweiterbare UI-Kontextregeln.
