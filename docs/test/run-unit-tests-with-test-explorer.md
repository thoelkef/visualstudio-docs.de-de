---
title: Ausführen und Debuggen von Komponententests mit dem Test-Explorer
description: Erfahren Sie, wie Sie mit dem Test-Explorer in Visual Studio Tests ausführen. In diesem Artikel wird beschrieben, wie Sie automatische Testläufe nach der Erstellung durchführen, die Testergebnisse anzeigen, die Testliste gruppieren und filtern, Wiedergabelisten erstellen, Tests debuggen und Tastenkombinationen für Tests verwenden.
ms.date: 07/29/2019
ms.topic: conceptual
f1_keywords:
- vs.unittesting.testexplorer.overview
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 11ebe64bf1e3034230a9697fef0c072fc89ef282
ms.sourcegitcommit: 3e74ec49a54e5c3da7631f4466128cdf4384af6b
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 08/01/2019
ms.locfileid: "68711269"
---
# <a name="run-unit-tests-with-test-explorer"></a>Ausführen von Komponententests mit dem Test-Explorer

Verwenden Sie den Test-Explorer zum Ausführen von Komponententests von Visual Studio oder Komponententestprojekten von Drittanbietern. Sie können den Test-Explorer auch dazu verwenden, Tests in Kategorien zu gruppieren, die Testliste zu filtern und Ausführungslisten zu erstellen, zu speichern und auszuführen. Zudem können Sie Tests debuggen und die Leistung und Code Coverage von Tests analysieren.

Visual Studio enthält die Komponententest-Frameworks von Microsoft für sowohl verwalteten als auch systemeigenen Code. Im Test-Explorer kann jedoch auch jedes Komponententest-Framework mit implementiertem Test-Explorer-Adapter ausgeführt werden. Weitere Informationen zum Installieren von Komponententest-Frameworks von Drittanbietern finden Sie unter [Installieren von Frameworks für Komponententests von Drittanbietern](../test/install-third-party-unit-test-frameworks.md).

Im **Test-Explorer** können Tests aus mehreren Testprojekten in einer Projektmappe und aus Testklassen ausgeführt werden, die Teil der Produktionscodeprojekte sind. Für Testprojekte können verschiedene Komponententest-Frameworks verwendet werden. Wenn der zu testende Code für .NET geschrieben wird, kann das Testprojekt in jeder Sprache geschrieben werden, die ebenfalls auf .NET abzielt, unabhängig von der Sprache des Zielcodes. Systemeigene C/C++-Codeprojekte müssen mithilfe eines Komponententest-Frameworks für C++ getestet werden. Weitere Informationen finden Sie unter [Schreiben von Komponententests für C/C++ ](writing-unit-tests-for-c-cpp.md).

## <a name="run-tests-in-test-explorer"></a>Ausführen von Tests im Test-Explorer


Wenn Sie das Testprojekt erstellen, werden die Tests im Test-Explorer angezeigt. Falls der Test-Explorer nicht geöffnet ist, wählen Sie im Visual Studio-Menü nacheinander **Test** , **Fenster**und dann **Test-Explorer**aus.


::: moniker range="vs-2017"
![Komponententest-Explorer](../test/media/ute_failedpassednotrunsummary.png)
::: moniker-end
::: moniker range=">=vs-2019"
![Test-Explorer](../test/media/vs-2019/test-explorer-16-2.png)
::: moniker-end

::: moniker range="vs-2017"
Beim Ausführen, Schreiben und erneuten Ausführen der Tests werden die Ergebnisse vom Test-Explorer in den Standardgruppen **Fehlgeschlagene Tests**, **Bestandene Tests**, **Abgebrochene Tests** und **Nicht ausgeführte Tests**angezeigt. Sie können die Gruppierung der Tests im Test-Explorer ändern.
::: moniker-end
::: moniker range=">=vs-2019"
Während Sie Ihre Tests ausführen, schreiben und erneut ausführen, zeigt der Test-Explorer die Ergebnisse in einer Standardgruppierung Aus **Projekt**, **Namespace** und **Klasse** an. Sie können die Gruppierung der Tests im Test-Explorer ändern.
::: moniker-end

Sie können über die Symbolleiste **Test-Explorer** die meisten Aktionen zum Suchen, Organisieren und Ausführen von Tests ausführen.

::: moniker range="vs-2017"
![Tests von der Test-Explorer-Symbolleiste ausführen](../test/media/ute_toolbar.png)
::: moniker-end
::: moniker range=">=vs-2019"
![Tests von der Test-Explorer-Symbolleiste ausführen](../test/media/vs-2019/test-explorer-toolbar-diagram-16-2.png)
::: moniker-end

### <a name="run-tests"></a>Tests durchführen

::: moniker range="vs-2017"
Sie können alle Tests in der Projektmappe, alle Tests in einer Gruppe oder einen Satz ausgewählter Tests ausführen. Führen Sie einen der folgenden Schritte aus:

- Wählen Sie zum Ausführen aller Tests in einer Projektmappe **Alle ausführen**aus.

- Klicken Sie zum Ausführen aller Tests in einer Standardgruppe auf **Ausführen**, und wählen Sie dann im Menü die Gruppe aus.

- Wählen Sie die einzelnen auszuführenden Tests aus, öffnen Sie das Kontextmenü eines ausgewählten Tests, und wählen Sie dann **Ausgewählte Tests ausführen** aus.

- Wenn einzelne Tests keine Abhängigkeiten haben, die verhindern, dass sie in beliebiger Reihenfolge ausgeführt werden können, sollten Sie parallele Testausführung über die ![UTE&#95;parallelicon&#45;small](../test/media/ute_parallelicon-small.png) -Umschaltfläche auf der Symbolleiste aktivieren. Dadurch lässt sich die Zeit deutlich verkürzen, die zum Ausführen aller Tests erforderlich ist.

Während der Testausführung wird die oben im Fenster **Test-Explorer** angezeigte Leiste **Erfolgreich/Fehlgeschlagen** animiert. Am Ende des Testlaufs wird die Leiste **Erfolgreich/Fehlgeschlagen** grün, wenn alle Tests erfolgreich verlaufen sind, oder rot, wenn ein Test fehlgeschlagen ist.
::: moniker-end
::: moniker range=">=vs-2019"
Sie können alle Tests in der Projektmappe, alle Tests in einer Gruppe oder einen Satz ausgewählter Tests ausführen. Führen Sie einen der folgenden Schritte aus:

- Wählen Sie zum Ausführen aller Tests in einer Projektmappe das Symbol **Alle ausführen** aus.

- Klicken Sie zum Ausführen aller Tests in einer Standardgruppe auf das Symbol **Ausführen**, und wählen Sie dann im Menü die Gruppe aus.

- Wählen Sie die einzelnen auszuführenden Tests aus, öffnen Sie das Kontextmenü eines ausgewählten Tests, und wählen Sie dann **Ausgewählte Tests ausführen** aus.

- Wenn einzelne Tests keine Abhängigkeiten aufweisen, die verhindern, dass sie in beliebiger Reihenfolge ausgeführt werden können, sollten Sie parallele Testausführung über das Eigenschaftenmenü auf der Symbolleiste aktivieren. Dadurch lässt sich die Zeit deutlich verkürzen, die zum Ausführen aller Tests erforderlich ist.
::: moniker-end

### <a name="run-tests-after-every-build"></a>Ausführen von Tests nach jedem Build
::: moniker range="vs-2017"
|Schaltfläche|Beschreibung|
|-|-|
|![Nach Build ausführen](../test/media/ute_runafterbuild_btn.png)|Klicken Sie zum Ausführen der Komponententests nach jedem lokalen Buildvorgang im Standardmenü auf **Test** und anschließend in der Symbolleiste **Test-Explorer** auf **Nach dem Buildvorgang Tests ausführen**.|

> [!NOTE]
> Zum Ausführen von Komponententests nach jedem Buildvorgang benötigen Sie Visual Studio 2017 Enterprise oder Visual Studio 2019. In Visual Studio-2019 ist die Lösung in Community und Professional sowie Enterprise enthalten.
::: moniker-end
::: moniker range=">=vs-2019"
Klicken Sie zum Ausführen der Komponententests nach jedem lokalen Buildvorgang in der Test-Explorer-Symbolleiste auf das Einstellungssymbol, und wählen Sie **Nach dem Buildvorgang Tests ausführen** aus.
::: moniker-end

## <a name="view-test-results"></a>Testergebnisse anzeigen

Beim Ausführen, Schreiben und erneuten Ausführen der Tests werden die Ergebnisse vom Test-Explorer in den Gruppen **Fehlgeschlagene Tests**, **Bestandene Tests**, **Abgebrochene Tests** sowie **Nicht ausgeführte Tests**angezeigt. Im Detailbereich unten im Test-Explorer wird eine Zusammenfassung des Testlaufs angezeigt.

### <a name="view-test-details"></a>Anzeigen von Testdetails

Zum Anzeigen der Details eines einzelnen Tests wählen Sie den jeweiligen Test aus.

::: moniker range="vs-2017"
![Details zur Testausführung](../test/media/ute_testdetails.png)
::: moniker-end
::: moniker range=">=vs-2019"
![Details zur Testausführung](../test/media/vs-2019/test-explorer-detail.png)
::: moniker-end

Im Testdetailbereich werden folgende Informationen angezeigt:

- Quelldateiname und Zeilennummer der Testmethode

- Teststatus

- Ausführungsdauer der Testmethode

Bei einem fehlgeschlagenen Test wird im Detailbereich außerdem Folgendes angezeigt:

- Die vom Komponententest-Framework für den Test zurückgegebene Meldung

- Die Stapelüberwachung zum Zeitpunkt des Testfehlers

### <a name="view-the-source-code-of-a-test-method"></a>Anzeigen des Quellcodes einer Testmethode

Wählen Sie zum Anzeigen des Quellcodes einer Testmethode im Visual Studio-Editor den Test und anschließend im Kontextmenü **Test öffnen** (Tastatur: **F12**) aus.

## <a name="group-and-filter-the-test-list"></a>Gruppieren und Filtern der Testliste

Im Test-Explorer können Sie Tests in vordefinierte Kategorien gruppieren. In den meisten der im Test-Explorer ausführbaren Komponententest-Frameworks können Sie eigene Kategorien und Kategorie/Wert-Paare zum Gruppieren der Tests definieren. Sie können die Testliste auch durch das Vergleichen von Zeichenfolgen mit Testeigenschaften filtern.

### <a name="group-tests-in-the-test-list"></a>Gruppieren von Tests in der Testliste

::: moniker range="vs-2017"
Klicken Sie zum Ändern der Testunterteilung den neben der Schaltfläche **Gruppieren nach** auf den Pfeil nach unten (![Gruppenschaltfläche „Test-Explorer“](../test/media/ute_groupby_btn.png)), und wählen Sie anschließend neue Gruppierungskriterien aus.

![Tests im Test-Explorer nach Kategorie gruppieren](../test/media/ute_groupbycategory.png)
::: moniker-end
::: moniker range=">=vs-2019"
Im Test-Explorer können Sie Tests in eine Hierarchie gruppieren. Die Standardhierarchiegruppierung ist **Projekt**, **Namespace** und dann **Klasse**. Klicken Sie zum Ändern der Testunterteilung auf die Schaltfläche **Gruppieren nach** ![Gruppenschaltfläche „Test-Explorer“](../test/media/ute_groupby_btn.png), und wählen Sie anschließend neue Gruppierungskriterien aus.

![Tests im Test-Explorer nach Kategorie gruppieren](../test/media/vs-2019/test-explorer-groupby-162.png)

Sie können Ihre eigenen Hierarchie- und Gruppenebenen nach **Zustand** und dann **Klasse** definieren, indem Sie beispielsweise „Gruppieren nach“-Optionen in Ihrer bevorzugten Reihenfolge auswählen.

![„Gruppieren nach“, „Zustand“ und dann „Klasse“](../test/media/vs-2019/test-explorer-groupby-state-16-2.png)
::: moniker-end

### <a name="test-explorer-groups"></a>Test-Explorer-Gruppen

::: moniker range="vs-2017"
|Gruppieren|BESCHREIBUNG|
|-|-----------------|
|**Dauer**|Tests werden anhand der Ausführungszeit gruppiert: **Schnell**, **Mittel** und **Langsam**.|
|**Ergebnis**|Tests werden anhand der Ausführungsergebnisse gruppiert: **Fehlgeschlagene Tests**, **übersprungene Tests** und **bestandene Tests**.|
|**Merkmale**|Gruppiert Tests nach von Ihnen definierten Kategorie/Wert-Paaren. Die Syntax zum Angeben von Merkmalskategorien und -werten wird durch das Komponententest-Framework festgelegt.|
|**Projekt**|Gruppiert Tests nach den Namen der Projekte.|
::: moniker-end
::: moniker range=">=vs-2019"
|Gruppieren|BESCHREIBUNG|
|-|-----------------|
|**Dauer**|Gruppiert Tests nach Ausführungszeit: **Schnell**, **Mittel** und **Langsam**.|
|**Zustand**|Tests werden anhand der Ausführungsergebnisse gruppiert: **Fehlgeschlagene Tests**, **Übersprungene Tests**, **Bestandene Tests** und **Nicht ausführen**|
|**Zielframework** | Gruppiert Tests nach dem Framework, das die Projekte als Ziel haben |
|**Namespace**|Gruppiert Tests nach dem enthaltenden Namespace.|
|**Projekt**|Gruppiert Tests nach dem enthaltenden Projekt.|
|**Klasse**|Gruppiert Tests nach der enthaltenden Klasse.|
::: moniker-end

### <a name="group-by-traits"></a>Gruppieren nach Merkmalen

In der Regel handelt es sich bei Merkmalen um Kategoriename/Wert-Paare, ein Merkmal kann jedoch auch eine einzelne Kategorie darstellen. Merkmale können Methoden zugewiesen werden, die im Komponententest-Framework als Testmethoden identifiziert sind. In einem Komponententest-Framework können Merkmalskategorien definiert werden. Außerdem können Sie den Merkmalskategorien Werte hinzufügen, um eigene Kategoriename/Wert-Paare zu definieren. Die Syntax zum Angeben von Merkmalskategorien und -werten wird durch das Komponententest-Framework festgelegt.

**Merkmale im Microsoft-Komponententest-Framework für verwalteten Code**

Im Microsoft-Komponententest-Framework für verwaltete Apps wird ein Merkmalsname/Wert-Paar in einem  <xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestPropertyAttribute> -Attribut definiert. Das Testframework weist zudem folgende vordefinierte Merkmale auf:

|Merkmal|BESCHREIBUNG|
|-|-----------------|
|<xref:Microsoft.VisualStudio.TestTools.UnitTesting.OwnerAttribute>|Die Kategorie "Besitzer" wird vom Komponententest-Framework definiert. Sie müssen einen Zeichenfolgenwert für den Besitzer angeben.|
|<xref:Microsoft.VisualStudio.TestTools.UnitTesting.PriorityAttribute>|Die Kategorie "Priorität" wird vom Komponententest-Framework definiert. Sie müssen einen ganzzahligen Wert für die Priorität angeben.|
|<xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestCategoryAttribute>|Mithilfe des TestCategory-Attributs können Sie eine Kategorie ohne Wert angeben. Bei einer durch das TestCategory-Attribut definierten Kategorie kann es sich auch um die Kategorie eines TestProperty-Attributs handeln.|
|<xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestPropertyAttribute>|Mithilfe des TestProperty-Attributs können Sie Merkmalskategorie/Wert-Paare definieren.|


**Merkmale im Microsoft-Komponententest-Framework für C++**

 Weitere Informationen finden Sie unter [Verwenden des Microsoft-Komponententest-Frameworks für C++](how-to-use-microsoft-test-framework-for-cpp.md).

## <a name="create-custom-playlists"></a>Erstellen benutzerdefinierter Wiedergabelisten

::: moniker range="vs-2017"
Sie können eine Liste mit Tests erstellen und speichern, die als Gruppe ausgeführt oder angezeigt werden sollen. Wenn Sie eine Wiedergabeliste auswählen, werden die Tests in der Liste im Test-Explorer angezeigt. Sie können einen Test zu mehr als einer Wiedergabeliste hinzufügen, und bei Auswahl der Standardwiedergabeliste **Alle Tests** sind alle Tests im Projekt verfügbar.

![Wiedergabeliste auswählen](../test/media/ute_playlist.png)

Wählen Sie zum**Erstellen einer Wiedergabeliste**im Komponententest-Explorer mindestens einen Test aus. Klicken Sie im Kontextmenü auf **Zu Wiedergabeliste hinzufügen** > **Neue Wiedergabeliste**. Speichern Sie die Datei unter dem im Dialogfeld **Neue Wiedergabeliste erstellen** angegebenen Namen und Speicherort.

Wählen Sie zum**Hinzufügen von Tests zu einer Wiedergabeliste**im Komponententest-Explorer mindestens einen Test aus. Wählen Sie im Kontextmenü **Zu Wiedergabeliste hinzufügen** und anschließend die Wiedergabeliste aus, der die Tests hinzugefügt werden sollen.

Wählen Sie zum **Öffnen einer Wiedergabeliste** im Visual Studio-Menü **Test** > **Wiedergabeliste** aus. Anschließend können Sie entweder aus der Liste der zuletzt verwendeten Wiedergabelisten oder die Option **Wiedergabelistendatei öffnen** auswählen, um den Namen und Speicherort der Wiedergabeliste anzugeben.

Wenn einzelne Tests keine Abhängigkeiten haben, die verhindern, dass sie in beliebiger Reihenfolge ausgeführt werden können, sollten Sie parallele Testausführung über die ![UTE&#95;parallelicon&#45;small](../test/media/ute_parallelicon-small.png) -Umschaltfläche auf der Symbolleiste aktivieren. Dadurch lässt sich die Zeit deutlich verkürzen, die zum Ausführen aller Tests erforderlich ist.
::: moniker-end
::: moniker range=">=vs-2019"
Sie können eine Liste mit Tests erstellen und speichern, die als Gruppe ausgeführt oder angezeigt werden sollen. Wenn Sie eine Wiedergabeliste auswählen, werden die Tests in der Liste auf einer neuen Registerkarte im Test-Explorer angezeigt. Sie können einen Test zu mehr als einer Wiedergabeliste hinzufügen.

Wählen Sie zum**Erstellen einer Wiedergabeliste**im Komponententest-Explorer mindestens einen Test aus. Klicken Sie im Kontextmenü auf **Zu Wiedergabeliste hinzufügen** > **Neue Wiedergabeliste**.

![Erstellen einer Wiedergabeliste](../test/media/vs-2019/test-explorer-playlist-16-2.png)

Die Wiedergabeliste wird in einer neuen Registerkarte im Test-Explorer geöffnet. Sie können diese Wiedergabeliste einmal verwenden und dann verwerfen, oder Sie können auf die Schaltfläche **Speichern** in der Symbolleiste des Wiedergabelistenfensters klicken und dann einen Namen und einen Ort zum Speichern der Wiedergabeliste auswählen.

![Die Wiedergabeliste wird in einer separaten Registerkarte im Test-Explorer geöffnet.](../test/media/vs-2019/test-explorer-playlist-tab-16-2.png)

Wählen Sie zum**Hinzufügen von Tests zu einer Wiedergabeliste**im Komponententest-Explorer mindestens einen Test aus. Klicken Sie im Kontextmenü auf **Zu Wiedergabeliste hinzufügen** > **Neue Wiedergabeliste**. 

**Um eine Wiedergabeliste zu öffnen**, wählen Sie das Wiedergabelistensymbol in der Visual Studio-Symbolleiste, und wählen Sie eine zuvor gespeicherte Wiedergabelistendatei aus dem Menü.
::: moniker-end

::: moniker range=">=vs-2019"
### <a name="test-explorer-columns"></a>Test-Explorer-Spalten

Die [Gruppen](#test-explorer-groups) sind auch als Spalten im Test-Explorer verfügbar, wie „Merkmal“, „Stapelverfolgung“, „Fehlermeldung“ und „Vollständig qualifizierter Name“. Die meisten Spalten sind standardmäßig nicht sichtbar, und Sie können festlegen, welche Spalten Sie sehen und in welcher Reihenfolge sie angezeigt werden.

![„Gruppieren nach“, „Zustand“ und dann „Klasse“](../test/media/vs-2019/test-explorer-columns-16-2.png)

### <a name="filter-sort-and-rearrange-test-columns"></a>Filtern, Sortieren und Neuordnen von Testspalten

Spalten können gefiltert, sortiert und neu angeordnet werden. 
* Um bestimmte Merkmale zu filtern, klicken Sie oben in der Spalte „Merkmale“ auf das Filtersymbol.

  ![Spaltenfilter](../test/media/vs-2019/test-explorer-filter-column-16-2.png)

* Um die Reihenfolge der Spalten zu ändern, klicken Sie auf eine Spaltenüberschrift, und ziehen Sie Sie nach links oder rechts.

* Um eine Spalte zu sortieren, klicken Sie auf die Spaltenüberschrift. Es können nicht alle Spalten sortiert werden.

  ![Spaltensortierung](../test/media/vs-2019/test-explorer-sort-column-16-2.png)
::: moniker-end

## <a name="search-and-filter-the-test-list"></a>Durchsuchen und Filtern der Testliste

Sie können die Test-Explorer-Suchfilter auch verwenden, um die Testmethoden einzuschränken, die in Ihren Projekten angezeigt und ausgeführt werden können.

Wenn Sie in das Suchfeld des **Test-Explorers** eine Zeichenfolge eingeben und die **Eingabetaste** drücken, wird die Testliste so gefiltert, dass nur Tests angezeigt werden, deren vollqualifizierte Namen die Zeichenfolge aufweisen.

Filtern nach einem anderen Kriterium:

1. Öffnen Sie die rechts neben dem Suchfeld angezeigte Dropdownliste.

2. Wählen Sie ein neues Kriterium aus.

3. Geben Sie zwischen den Anführungszeichen den Filterwert ein.

::: moniker range="vs-2017"
![Tests im Test-Explorer filtern](../test/media/ute_filtertestlist.png)
::: moniker-end
::: moniker range=">=vs-2019"
![Tests im Test-Explorer filtern](../test/media/vs-2019/test-explorer-search-filter-16-2.png)
::: moniker-end

> [!NOTE]
> Bei Suchvorgängen wird die Groß-/Kleinschreibung nicht beachtet, und die angegebene Zeichenfolge kann einem die oft ausgegebene Befehlszeilen  Teil des Kriteriumswerts entsprechen.

|Qualifizierer|BESCHREIBUNG|
|-|-----------------|
|**Merkmal**|Durchsucht sowohl die Merkmalskategorie als auch den Wert nach Übereinstimmungen. Die Syntax zum Angeben von Merkmalskategorien und -werten wird durch das Komponententest-Framework festgelegt.|
|**Projekt**|Durchsucht die Testprojektnamen nach Übereinstimmungen.|
|**Fehlermeldung**|Durchsucht die von fehlerhaften Asserts zurückgegebenen benutzerdefinierte Fehlermeldungen nach Übereinstimmungen.|
|**Dateipfad**|Durchsucht die vollqualifizierten Dateinamen der Testquelldateien nach Übereinstimmungen.|
|**Vollqualifizierter Name**|Durchsucht die vollqualifizierten Dateinamen von Testnamespaces, Klassen und Methoden nach Übereinstimmungen.|
|**Ausgabe**|Durchsucht die benutzerdefinierten Fehlermeldungen, die als Standardausgabe (stdout) oder Standardfehler (stderr) geschrieben werden. Die Syntax zum Angeben von Ausgabemeldungen wird durch das Komponententest-Framework festgelegt.|
|**Ergebnis**|Sucht in den Kategorienamen des Test-Explorers nach Übereinstimmungen: **Fehlgeschlagene Tests**, **übersprungene Tests** und **bestandene Tests**.|

Verwenden Sie folgende Syntax, um eine Teilmenge von Filterergebnissen auszuschließen :

```
FilterName:"Criteria" -FilterName:"SubsetCriteria"
```

Zum Beispiel gibt `FullName:"MyClass" - FullName:"PerfTest"` alle Tests mit „MyClass“ im Namen zurück, mit Ausnahme der Tests, deren Namen auch „PerfTest“ enthalten.

## <a name="debug-and-analyze-unit-tests"></a>Debugging und Analyse von Komponententests

Mit dem Test-Explorer können Sie Debugsitzungen für Tests starten. Beim schrittweisen Durchlaufen des Codes mit dem Visual Studio-Debugger wechseln Sie nahtlos zwischen den Komponententests und dem zu testenden Projekt hin und zurück. Starten des Debuggens:

1. Legen Sie im Visual Studio-Editor in mindestens einer zu debuggenden Testmethode einen Haltepunkt fest.

    > [!NOTE]
    > Da Testmethoden in jeder die oft ausgegebene Befehlszeilen  Reihenfolge ausgeführt werden können, legen Sie Haltepunkte in allen Testmethoden fest, die Sie debuggen möchten.

2. Wählen Sie im Test-Explorer die Testmethoden und dann im Kontextmenü **Ausgewählte Tests debuggen** aus.

   Weitere Informationen zum Debugger finden Sie unter [Debuggen in Visual Studio](../debugger/debugger-feature-tour.md).

### <a name="diagnose-test-method-performance-issues"></a>Diagnose von Leistungsproblemen bei Testmethoden

Zur Ermittlung der Ursache, weshalb die Ausführung einer Testmethode zu lange dauert, müssen Sie im Test-Explorer die Methode auswählen und anschließend im Kontextmenü auf **Profil für ausgewählten Test erstellen** klicken. Weitere Informationen finden Sie unter [Performance Explorer (Leistungs-Explorer)](../profiling/performance-explorer.md).

### <a name="analyze-unit-test-code-coverage"></a>Analysieren der Codeabdeckung für Komponententests

MIthilfe des Codeabdeckungstools von Visual Studio können Sie die Menge des Produktcodes ermitteln, die tatsächlich von den Komponententests getestet wird. Das Codeabdeckungstool kann für ausgewählte oder alle Tests in einer Projektmappe ausgeführt werden.

Ausführen des Codeabdeckungstools für Testmethoden in einer Projektmappe:

::: moniker range="vs-2017"
1. Wählen Sie in der obersten Menüleiste **Tests** und anschließend **Code Coverage analysieren**aus.

2. Wählen Sie in Untermenü einen der folgenden Befehle aus:

    - Mit**Ausgewählte Tests** werden die im Test-Explorer ausgewählten Testmethoden analysiert.

    - Mit**Alle Tests** werden alle Testmethoden in der Projektmappe analysiert.
::: moniker-end
::: moniker range=">=vs-2019"
* Klicken Sie mit der rechten Maustaste in den Test-Explorer, und wählen Sie **Codeabdeckung für ausgewählte Tests analysieren** aus.
::: moniker-end

Im Fenster **Code Coverage-Ergebnisse** wird der Prozentsatz der durchlaufenen Produktcodeblöcke angezeigt, angeordnet nach Zeile, Funktion, Klasse, Namespace und Modul.

Weitere Informationen finden Sie unter [Bestimmen des Umfangs des zu testenden Codes mithilfe von Code Coverage](../test/using-code-coverage-to-determine-how-much-code-is-being-tested.md).

## <a name="test-shortcuts"></a>Tastenkombinationen für Tests

Tests können im **Test-Explorer** ausgeführt werden, indem Sie mit der rechten Maustaste auf einen Test im Code-Editor und dann auf **Test ausführen** klicken, oder indem Sie die [Standardtastenkombinationen vom Test-Explorer](../ide/default-keyboard-shortcuts-in-visual-studio.md#bkmk_testexplorerGLOBAL) in Visual Studio verwenden. Manche dieser Tastenkombinationen sind vom Kontext abhängig. Das heißt, dass sie Tests basierend auf der Position Ihres Cursors im Code ausführen oder debuggen. Wenn Ihr Cursor sich in einer Testmethode befindet, wird diese Testmethode ausgeführt. Wenn Ihr Cursor sich auf der Klassenebene befindet, werden alle Tests in dieser Klasse ausgeführt. Dies gilt ebenfalls für die Namespaceebene.

|Häufig verwendete Befehle| Tastenkombinationen|
|-|------------------------|
|TestExplorer.DebugAllTestsInContext|**STRG**+**R**, **STRG**+**T**|
|TestExplorer.RunAllTestsInContext|**STRG**+**R**, **T**|

> [!NOTE]
> In einer abstrakten Klasse können Sie keinen Test ausführen, da Tests nur in abstrakten Klassen definiert werden und nicht instanziiert. Zum Ausführen von Tests in abstrakten Klassen müssen Sie eine Klasse erstellen, die von der abstrakten Klasse abgeleitet ist.

## <a name="see-also"></a>Siehe auch

- [Ausführen von Komponententests für Code](../test/unit-test-your-code.md)
- [Ausführen eines Komponententest als 64-Bit-Prozess](../test/run-a-unit-test-as-a-64-bit-process.md)
- [Häufig gestellte Fragen zum Test-Explorer](test-explorer-faq.md)
