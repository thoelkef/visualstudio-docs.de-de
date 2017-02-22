---
title: "Ausf&#252;hren von Komponententests mit dem Test-Explorer | Microsoft Docs"
ms.custom: ""
ms.date: "12/02/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.unittesting.testexplorer.overview"
ms.assetid: 91b167a3-280a-498b-8fc2-f67859a2c64e
caps.latest.revision: 27
caps.handback.revision: 27
ms.author: "mlearned"
manager: "douge"
---
# Ausf&#252;hren von Komponententests mit dem Test-Explorer
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Mithilfe des Test\-Explorers können Sie Komponententests aus Visual Studio oder Testprojekte von Drittanbietern ausführen, Tests in Kategorien gruppieren, die Testliste filtern sowie Testwiedergabelisten erstellen, speichern und ausführen. Zudem können Sie Tests debuggen und die Leistung und Codeabdeckung von Tests analysieren.  
  
##  <a name="BKMK_Contents"></a> Inhalt  
 [Komponententestframeworks und Testprojekte](#BKMK_Unit_test_frameworks_and_test_projects)  
  
 [Ausführen von Tests im Test-Explorer](#BKMK_Run_tests_in_Test_Explorer)  
  
 [Testergebnisse anzeigen](#BKMK_View_test_results)  
  
 [Gruppieren und Filtern der Testliste](#BKMK_Group_and_filter_the_test_list)  
  
 [Erstellen benutzerdefinierter Wiedergabelisten](#BKMK_Create_custom_playlists)  
  
 [Debugging und Analyse von Komponententests](#BKMK_Debug_and_analyze_unit_tests)  
  
 [Externe Ressourcen](#BKMK_External_resources)  
  
##  <a name="BKMK_Unit_test_frameworks_and_test_projects"></a> Komponententestframeworks und Testprojekte  
 Visual Studio enthält die Komponententest\-Frameworks von Microsoft für sowohl verwalteten als auch systemeigenen Code. Im Test\-Explorer kann jedoch auch jedes Komponententest\-Framework mit implementiertem Test\-Explorer\-Adapter ausgeführt werden. Weitere Informationen zum Installieren von Komponententest\-Frameworks von Drittanbietern finden Sie unter [Installieren von Frameworks für Komponententests von Drittanbietern](../test/install-third-party-unit-test-frameworks.md).  
  
 Im Test\-Explorer können Tests aus mehreren Testprojekten in einer Projektmappe und aus Testklassen ausgeführt werden, die Teil der Produktionscodeprojekte sind. Für Testprojekte können verschiedene Komponententest\-Frameworks verwendet werden. Wenn der zu testende Code für .NET Framework geschrieben wird, kann das Testprojekt in jeder ebenfalls auf .NET Framework abzielenden Sprache geschrieben werden, unabhängig von der Sprache des Zielcodes. Systemeigene C\/C\+\+\-Codeprojekte müssen mithilfe eines Komponententest\-Frameworks für C\+\+ getestet werden.  
  
 ![Zurück nach oben](../debugger/media/pcs_backtotop.png "PCS\_BackToTop") [Inhalt](#BKMK_Contents)  
  
##  <a name="BKMK_Run_tests_in_Test_Explorer"></a> Ausführen von Tests im Test\-Explorer  
 [Tests durchführen](#BKMK_Run_tests) **&#124;** [Ausführen von Tests nach jedem Build](#BKMK_Run_tests_after_every_build)  
  
 Wenn Sie das Testprojekt erstellen, werden die Tests im Test\-Explorer angezeigt. Falls der Test\-Explorer nicht geöffnet ist, wählen Sie im Visual Studio\-Menü nacheinander **Test**, **Fenster** und dann **Test\-Explorer** aus.  
  
 ![Komponententest&#45;Explorer](../ide/media/ute_failedpassednotrunsummary.png "UTE\_FailedPassedNotRunSummary")  
  
 Beim Ausführen, Schreiben und erneuten Ausführen der Tests werden die Ergebnisse vom Test\-Explorer in den Standardgruppen **Fehlgeschlagene Tests**, **Bestandene Tests**, **Abgebrochene Tests** und **Nicht ausgeführte Tests** angezeigt. Sie können die Gruppierung der Tests im Test\-Explorer ändern.  
  
 Über die Test\-Explorer\-Symbolleiste können Sie die meisten Aktionen zum Suchen, Organisieren und Ausführen von Tests ausführen.  
  
 ![Tests von der Test&#45;Explorer&#45;Symbolleiste ausführen](../test/media/ute_toolbar.png "UTE\_ToolBar")  
  
 ![Zurück nach oben](../debugger/media/pcs_backtotop.png "PCS\_BackToTop") [Inhalt](#BKMK_Contents)  
  
###  <a name="BKMK_Run_tests"></a> Tests durchführen  
 Sie können alle Tests in der Projektmappe, alle Tests in einer Gruppe oder einen Satz ausgewählter Tests ausführen. Führen Sie einen der folgenden Schritte aus:  
  
-   Wählen Sie zum Ausführen aller Tests in einer Projektmappe **Alle ausführen** aus.  
  
-   Wählen Sie zum Ausführen aller Tests in einer Standardgruppe **Ausführen...** und dann im Menü die Gruppe aus.  
  
-   Wählen Sie die einzelnen auszuführenden Tests aus, öffnen Sie das Kontextmenü eines ausgewählten Tests, und wählen Sie dann **Ausgewählte Tests ausführen** aus.  
  
-   Wenn einzelne Tests keine Abhängigkeiten haben, die verhindern, dass sie in beliebiger Reihenfolge ausgeführt werden können, sollten Sie parallele Testausführung über die ![UTE&#95;parallelicon&#45;small](../test/media/ute_parallelicon-small.png "UTE\_parallelicon\-small")\-Umschaltfläche auf der Symbolleiste aktivieren. Dadurch lässt sich die Zeit deutlich verkürzen, die zum Ausführen aller Tests erforderlich ist.  
  
 Während der Testausführung wird die oben im Fenster "Test\-Explorer" angezeigte Erfolgreich\/Fehler\-Leiste animiert. Am Ende des Testlaufs wird die Erfolgreich\/Fehler\-Leiste grün, wenn alle Tests erfolgreich verlaufen, oder rot, falls ein beliebiger Test fehlschlägt.  
  
 ![Zurück nach oben](../debugger/media/pcs_backtotop.png "PCS\_BackToTop") [Inhalt](#BKMK_Contents)  
  
###  <a name="BKMK_Run_tests_after_every_build"></a> Ausführen von Tests nach jedem Build  
  
> [!WARNING]
>  Das Ausführen von Komponententests nach jedem Buildvorgang wird in Visual Studio Enterprise unterstützt.  
  
|||  
|-|-|  
|![Run after build](../test/media/ute_runafterbuild_btn.png "UTE\_RunAfterBuild\_btn")|Wählen Sie zum Ausführen der Komponententests nach jedem lokalen Buildvorgang im Standardmenü **Test** und dann auf der Test\-Explorer\-Symbolleiste **Nach dem Buildvorgang Tests ausführen** aus.|  
  
 ![Zurück nach oben](../debugger/media/pcs_backtotop.png "PCS\_BackToTop") [Inhalt](#BKMK_Contents)  
  
##  <a name="BKMK_View_test_results"></a> Testergebnisse anzeigen  
 [Anzeigen von Testdetails](#BKMK_View_test_details) **&#124;** [Anzeigen des Quellcodes einer Testmethode](#BKMK_View_the_source_code_of_a_test_method)  
  
 Beim Ausführen, Schreiben und erneuten Ausführen der Tests werden die Ergebnisse vom Test\-Explorer in den Gruppen **Fehlgeschlagene Tests**, **Bestandene Tests**, **Abgebrochene Tests** sowie **Nicht ausgeführte Tests** angezeigt. Im Detailbereich unten im Test\-Explorer wird eine Zusammenfassung des Testlaufs angezeigt.  
  
###  <a name="BKMK_View_test_details"></a> Anzeigen von Testdetails  
 Zum Anzeigen der Details eines einzelnen Tests wählen Sie den jeweiligen Test aus.  
  
 ![Details zur Testausführung](../test/media/ute_testdetails.png "UTE\_TestDetails")  
  
 Im Testdetailbereich werden folgende Informationen angezeigt:  
  
-   Quelldateiname und Zeilennummer der Testmethode  
  
-   Teststatus  
  
-   Ausführungsdauer der Testmethode  
  
 Bei einem fehlgeschlagenen Test wird im Detailbereich außerdem Folgendes angezeigt:  
  
-   Die vom Komponententest\-Framework für den Test zurückgegebene Meldung  
  
-   Die Stapelüberwachung zum Zeitpunkt des Testfehlers  
  
 ![Zurück nach oben](../debugger/media/pcs_backtotop.png "PCS\_BackToTop") [Inhalt](#BKMK_Contents)  
  
###  <a name="BKMK_View_the_source_code_of_a_test_method"></a> Anzeigen des Quellcodes einer Testmethode  
 Zum Anzeigen des Quellcodes einer Testmethode im Visual Studio\-Editor wählen Sie den Test und anschließend im Kontextmenü **Test öffnen** \(Tastatur: F12\) aus.  
  
 ![Zurück nach oben](../debugger/media/pcs_backtotop.png "PCS\_BackToTop") [Inhalt](#BKMK_Contents)  
  
##  <a name="BKMK_Group_and_filter_the_test_list"></a> Gruppieren und Filtern der Testliste  
 [Gruppieren der Testliste](#BKMK_Grouping_the_test_list) **&#124;** [Gruppieren nach Merkmalen](#BKMK_Group_by_traits) **&#124;** [Durchsuchen und Filtern der Testliste](#BKMK_Search_and_filter_the_test_list)  
  
 Im Test\-Explorer können Sie Tests in vordefinierte Kategorien gruppieren. In den meisten der im Test\-Explorer ausführbaren Komponententest\-Frameworks können Sie eigene Kategorien und Kategorie\/Wert\-Paare zum Gruppieren der Tests definieren. Sie können die Testliste auch durch das Vergleichen von Zeichenfolgen mit Testeigenschaften filtern.  
  
###  <a name="BKMK_Grouping_the_test_list"></a> Gruppieren der Testliste  
 Zum Ändern der Testunterteilung wählen Sie den neben der Schaltfläche **Gruppieren nach** angezeigten Pfeil nach unten ![Gruppenschaltfläche "Test&#45;Explorer"](../test/media/ute_groupby_btn.png "UTE\_GroupBy\_btn") und anschließend neue Gruppierungskriterien aus.  
  
 ![Tests im Test&#45;Explorer nach Kategorie gruppieren](../test/media/ute_groupbycategory.png "UTE\_GroupByCategory")  
  
### Test\-Explorer\-Gruppen  
  
|Gruppieren|Beschreibung|  
|----------------|------------------|  
|**Dauer**|Die Tests werden nach Ausführungszeit gruppiert: **Schnell**, **Mittel** und **Langsam**.|  
|**Ergebnis**|Die Tests werden nach Ausführungsergebnis gruppiert: **Fehlgeschlagene Tests**, **Übersprungene Tests** und **Bestandene Tests**.|  
|**Merkmale**|Gruppiert Tests nach von Ihnen definierten Kategorie\/Wert\-Paaren. Die Syntax zum Angeben von Merkmalskategorien und \-werten wird durch das Komponententest\-Framework festgelegt.|  
|**Projekt**|Gruppiert Tests nach den Namen der Projekte.|  
  
 ![Zurück nach oben](../debugger/media/pcs_backtotop.png "PCS\_BackToTop") [Inhalt](#BKMK_Contents)  
  
###  <a name="BKMK_Group_by_traits"></a> Gruppieren nach Merkmalen  
 In der Regel handelt es sich bei Merkmalen um Kategoriename\/Wert\-Paare, ein Merkmal kann jedoch auch eine einzelne Kategorie darstellen. Merkmale können Methoden zugewiesen werden, die im Komponententest\-Framework als Testmethoden identifiziert sind. In einem Komponententest\-Framework können Merkmalskategorien definiert werden. Außerdem können Sie den Merkmalskategorien Werte hinzufügen, um eigene Kategoriename\/Wert\-Paare zu definieren. Die Syntax zum Angeben von Merkmalskategorien und \-werten wird durch das Komponententest\-Framework festgelegt.  
  
 **Merkmale im Microsoft\-Komponententest\-Framework für verwalteten Code**  
  
 Im Microsoft\-Komponententest\-Framework für verwaltete Apps wird ein Merkmalsname\/Wert\-Paar in einem <xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestPropertyAttribute>\-Attribut definiert. Das Testframework weist zudem folgende vordefinierte Merkmale auf:  
  
|Merkmal|Beschreibung|  
|-------------|------------------|  
|<xref:Microsoft.VisualStudio.TestTools.UnitTesting.OwnerAttribute>|Die Kategorie "Besitzer" wird vom Komponententest\-Framework definiert. Sie müssen einen Zeichenfolgenwert für den Besitzer angeben.|  
|<xref:Microsoft.VisualStudio.TestTools.UnitTesting.PriorityAttribute>|Die Kategorie "Priorität" wird vom Komponententest\-Framework definiert. Sie müssen einen ganzzahligen Wert für die Priorität angeben.|  
|<xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestCategoryAttribute>|Mithilfe des TestCategory\-Attributs können Sie eine Kategorie ohne Wert angeben. Bei einer durch das TestCategory\-Attribut definierten Kategorie kann es sich auch um die Kategorie eines TestProperty\-Attributs handeln.|  
|<xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestPropertyAttribute>|Mithilfe des TestProperty\-Attributs können Sie Merkmalskategorie\/Wert\-Paare definieren.|  
  
 **Merkmale im Microsoft\-Komponententest\-Framework für C\+\+**  
  
 Verwenden Sie zum Definieren eines Merkmals das `TEST_METHOD_ATTRIBUTE`\-Makro. Beispiel – Definieren eines Merkmals mit dem Namen `TEST_MY_TRAIT`:  
  
```cpp  
#define TEST_MY_TRAIT(traitValue) TEST_METHOD_ATTRIBUTE(L"MyTrait", traitValue)  
```  
  
 Verwenden des definierten Merkmals in den Komponententests:  
  
```  
BEGIN_TEST_METHOD_ATTRIBUTE(Method1)  
    TEST_OWNER(L"OwnerName")  
    TEST_PRIORITY(1)  
    TEST_MY_TRAIT(L"thisTraitValue")  
END_TEST_METHOD_ATTRIBUTE()  
  
TEST_METHOD(Method1)  
{     
    Logger::WriteMessage("In Method1");  
    Assert::AreEqual(0, 0);  
}  
```  
  
### C\+\+\-Merkmalsattributmakros  
  
|Makro|Beschreibung|  
|-----------|------------------|  
|`TEST_METHOD_ATTRIBUTE(attributeName, attributeValue)`|Verwenden Sie zum Definieren eines Merkmals das TEST\_METHOD\_ATTRIBUTE\-Makro.|  
|`TEST_OWNER(ownerAlias)`|Verwenden Sie das vordefinierte Merkmal "Besitzer", um einen Besitzer der Testmethode anzugeben.|  
|`TEST_PRIORITY(priority)`|Verwenden Sie das vordefinierte Merkmal "Priorität", um den Testmethoden relative Prioritäten zuzuweisen.|  
  
 ![Zurück nach oben](../debugger/media/pcs_backtotop.png "PCS\_BackToTop") [Inhalt](#BKMK_Contents)  
  
###  <a name="BKMK_Search_and_filter_the_test_list"></a> Durchsuchen und Filtern der Testliste  
 Verwenden Sie Test\-Explorer\-Filter, um die Testmethoden einzuschränken, die in Ihren Projekten angezeigt und ausgeführt werden können.  
  
 Wenn Sie im Suchfeld des Test\-Explorers eine Zeichenfolge eingeben und die EINGABETASTE drücken, wird die Liste so gefiltert, dass nur Tests angezeigt werden, deren vollqualifizierter Name die Zeichenfolge aufweist.  
  
 Filtern nach einem anderen Kriterium:  
  
1.  Öffnen Sie die rechts neben dem Suchfeld angezeigte Dropdownliste.  
  
2.  Wählen Sie ein neues Kriterium aus.  
  
3.  Geben Sie zwischen den Anführungszeichen den Filterwert ein.  
  
 ![Tests im Test&#45;Explorer filtern](../test/media/ute_filtertestlist.png "UTE\_FilterTestList")  
  
> [!NOTE]
>  Bei Suchvorgängen wird die Groß\-\/Kleinschreibung nicht beachtet, und die angegebene Zeichenfolge kann einem die oft ausgegebene Befehlszeilen  Teil des Kriteriumswerts entsprechen.  
  
|Qualifizierer|Beschreibung|  
|-------------------|------------------|  
|**Merkmal**|Durchsucht sowohl die Merkmalskategorie als auch den Wert nach Übereinstimmungen. Die Syntax zum Angeben von Merkmalskategorien und \-werten wird durch das Komponententest\-Framework festgelegt.|  
|**Projekt**|Durchsucht die Testprojektnamen nach Übereinstimmungen.|  
|**Fehlermeldung**|Durchsucht die von fehlerhaften Asserts zurückgegebenen benutzerdefinierte Fehlermeldungen nach Übereinstimmungen.|  
|**Dateipfad**|Durchsucht die vollqualifizierten Dateinamen der Testquelldateien nach Übereinstimmungen.|  
|**Vollqualifizierter Name**|Durchsucht die vollqualifizierten Dateinamen von Testnamespaces, Klassen und Methoden nach Übereinstimmungen.|  
|**Ausgabe**|Durchsucht die benutzerdefinierten Fehlermeldungen, die als Standardausgabe \(stdout\) oder Standardfehler \(stderr\) geschrieben werden. Die Syntax zum Angeben von Ausgabemeldungen wird durch das Komponententest\-Framework festgelegt.|  
|**Ergebnis**|Durchsucht die Test\-Explorer\-Kategorienamen nach Übereinstimmungen: **Fehlgeschlagene Tests**, **Abgebrochene Tests** und **Bestandene Tests**.|  
  
 Verwenden Sie folgende Syntax, um eine Teilmenge von Filterergebnissen auszuschließen :  
  
```  
FilterName:"Criteria" -FilterName:"SubsetCriteria"  
```  
  
 Beispiel:  
  
```  
FullName:"MyClass" - FullName:"PerfTest"  
```  
  
 Gibt alle Tests mit "MyClass" im Namen zurück, mit Ausnahme der Tests, deren Namen auch "PerfTest" enthalten.  
  
 ![Zurück nach oben](../debugger/media/pcs_backtotop.png "PCS\_BackToTop") [Inhalt](#BKMK_Contents)  
  
##  <a name="BKMK_Create_custom_playlists"></a> Erstellen benutzerdefinierter Wiedergabelisten  
 Sie können eine Liste mit Tests erstellen und speichern, die als Gruppe ausgeführt oder angezeigt werden sollen. Wenn Sie eine Wiedergabeliste auswählen, werden die Tests in der Liste im Test\-Explorer angezeigt. Sie können einen Test zu mehr als einer Wiedergabeliste hinzufügen, und bei Auswahl der Standardwiedergabeliste **Alle Tests** sind alle Tests im Projekt verfügbar.  
  
 ![Wiedergabeliste auswählen](../test/media/ute_playlist.png "UTE\_Playlist")  
  
 Wählen Sie zum **Erstellen einer Wiedergabeliste** im Komponententest\-Explorer mindestens einen Test aus. Wählen Sie im Kontextmenü **Neue Wiedergabeliste** und dann **Zu Wiedergabeliste hinzufügen** aus. Speichern Sie die Datei unter dem im Dialogfeld **Neue Wiedergabeliste erstellen** angegebenen Namen und Speicherort.  
  
 Wählen Sie zum **Hinzufügen von Tests zu einer Wiedergabeliste** im Komponententest\-Explorer mindestens einen Test aus. Wählen Sie im Kontextmenü **Zu Wiedergabeliste hinzufügen** und anschließend die Wiedergabeliste aus, der die Tests hinzugefügt werden sollen.  
  
 Wählen Sie zum **Öffnen einer Wiedergabeliste** im Visual Studio\-Menü "Test" aus. Anschließend können Sie entweder aus der Liste der zuletzt verwendeten Wiedergabelisten oder die Option "Wiedergabelistendatei öffnen" auswählen, um den Namen und Speicherort der Wiedergabeliste anzugeben.  
  
 Wenn einzelne Tests keine Abhängigkeiten haben, die verhindern, dass sie in beliebiger Reihenfolge ausgeführt werden können, sollten Sie parallele Testausführung über die ![UTE&#95;parallelicon&#45;small](../test/media/ute_parallelicon-small.png "UTE\_parallelicon\-small")\-Umschaltfläche auf der Symbolleiste aktivieren. Dadurch lässt sich die Zeit deutlich verkürzen, die zum Ausführen aller Tests erforderlich ist.  
  
 ![Zurück nach oben](../debugger/media/pcs_backtotop.png "PCS\_BackToTop") [Inhalt](#BKMK_Contents)  
  
##  <a name="BKMK_Debug_and_analyze_unit_tests"></a> Debugging und Analyse von Komponententests  
 [Debugging von Komponententests](#BKMK_Debug_unit_tests) **&#124;** [Diagnose von Leistungsproblemen bei Testmethoden](#BKMK_Diagnose_test_method_performance_issues) **&#124;** [Analysieren der Codeabdeckung für Komponententests](#BKMK_Analyzeunit_test_code_coverage)  
  
###  <a name="BKMK_Debug_unit_tests"></a> Debugging von Komponententests  
 Mit dem Test\-Explorer können Sie Debugsitzungen für Tests starten. Beim schrittweisen Durchlaufen des Codes mit dem Visual Studio\-Debugger wechseln Sie nahtlos zwischen den Komponententests und dem zu testenden Projekt hin und zurück. Starten des Debuggens:  
  
1.  Legen Sie im Visual Studio\-Editor in mindestens einer zu debuggenden Testmethode einen Haltepunkt fest.  
  
    > [!NOTE]
    >  Da Testmethoden in jeder die oft ausgegebene Befehlszeilen  Reihenfolge ausgeführt werden können, legen Sie Haltepunkte in allen Testmethoden fest, die Sie debuggen möchten.  
  
2.  Wählen Sie im Test\-Explorer die Testmethoden und dann im Kontextmenü **Ausgewählte Tests debuggen** aus.  
  
 Weitere Informationen zum Debugger finden Sie unter [Debuggen in Visual Studio](../debugger/debugging-in-visual-studio.md).  
  
 ![Zurück nach oben](../debugger/media/pcs_backtotop.png "PCS\_BackToTop") [Inhalt](#BKMK_Contents)  
  
###  <a name="BKMK_Diagnose_test_method_performance_issues"></a> Diagnose von Leistungsproblemen bei Testmethoden  
 Um die Ursache zu ermitteln, weshalb die Ausführung einer Testmethode zu lange dauert, wählen Sie im Komponententest\-Explorer die Methode und anschließend im Kontextmenü "Profil" aus. Siehe [Verwenden von Profilerstellungstools](../profiling/performance-explorer.md).  
  
###  <a name="BKMK_Analyzeunit_test_code_coverage"></a> Analysieren der Codeabdeckung für Komponententests  
  
> [!NOTE]
>  Die Codeabdeckung für Komponententest ist nur in Visual Studio Enterprise verfügbar.  
  
 MIthilfe des Codeabdeckungstools von Visual Studio können Sie die Menge des Produktcodes ermitteln, die tatsächlich von den Komponententests getestet wird. Das Codeabdeckungstool kann für ausgewählte oder alle Tests in einer Projektmappe ausgeführt werden.  
  
 Ausführen des Codeabdeckungstools für Testmethoden in einer Projektmappe:  
  
1.  Wählen Sie im Visual Studio\-Menü **Tests** und anschließend **Codeabdeckung analysieren** aus.  
  
2.  Wählen Sie in Untermenü einen der folgenden Befehle aus:  
  
    -   Mit **Ausgewählte Tests** werden die im Test\-Explorer ausgewählten Testmethoden analysiert.  
  
    -   Mit **Alle Tests** werden alle Testmethoden in der Projektmappe analysiert.  
  
 Im Fenster "Codeabdeckungsergebnisse " wird der Prozentsatz der durchlaufenen Produktcodeblöcke angezeigt, angeordnet nach Zeile, Funktion, Klasse, Namespace und Modul.  
  
 Weitere Informationen finden Sie unter [Bestimmen des Umfangs des zu testenden Codes mithilfe von Codeabdeckung](../test/using-code-coverage-to-determine-how-much-code-is-being-tested.md).  
  
 ![Zurück nach oben](../debugger/media/pcs_backtotop.png "PCS\_BackToTop") [Inhalt](#BKMK_Contents)  
  
##  <a name="BKMK_External_resources"></a> Externe Ressourcen  
  
###  <a name="BKMK_Guidance"></a> Empfehlungen  
 [Tests für fortlaufende Übermittlung mit Visual Studio 2012 – Kapitel 2: Komponententests – Interne Tests](http://go.microsoft.com/fwlink/?LinkID=255188)  
  
## Siehe auch  
 [Komponententest für Code](../test/unit-test-your-code.md)   
 [Ausführen eines Komponententest als 64\-Bit\-Prozess](../test/run-a-unit-test-as-a-64-bit-process.md)