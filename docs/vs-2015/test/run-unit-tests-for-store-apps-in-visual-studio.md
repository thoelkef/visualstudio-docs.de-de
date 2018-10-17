---
title: Ausführen von Komponententests für Store-Apps in Visual Studio | Microsoft-Dokumentation
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 5a6f5b32-bfce-4a63-81e9-02d54c592539
caps.latest.revision: 14
author: alexhomer1
ms.author: gewarren
manager: robinr
ms.openlocfilehash: cba96af95aaab2416d12a3791df2165f2f8d4102
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/12/2018
ms.locfileid: "49228507"
---
# <a name="run-unit-tests-for-store-apps-in-visual-studio"></a>Ausführen von Komponententests für Store-Apps in Visual Studio
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

In diesem Thema wird beschrieben, wie Sie Komponententests mithilfe des Test-Explorers in Microsoft Visual Studio ausführen.  
  
> [!NOTE]
>  In den Themen in diesem Abschnitt wird die Funktionalität von Visual Studio Express für Windows 8 beschrieben. Visual Studio Community, Enterprise und Professional stellen zusätzliche Funktionen für Komponententests bereit.  
>   
>  -   Sie können ein beliebiges Drittanbieter- oder Open Source-Framework für Komponententests verwenden, mit dem ein Add-On-Adapter für den Microsoft-Test-Explorer erstellt wurde. Sie können außerdem Codeabdeckungsinformationen für Ihre Tests analysieren und anzeigen.  
> -   Führen Sie Ihre Tests nach jedem Build aus. Sie können zudem Microsoft Fakes verwenden, ein Isolationsframework für verwalteten Code, mit dem Sie Ihre Tests auf den eigenen Code ausrichten können, indem Sie Testcode für System- und Drittanbieterfunktionalität ersetzen.  
>   
>  Weitere Informationen finden Sie unter [Komponententest für Code](../test/unit-test-your-code.md) in der MSDN Library.  
  
##  <a name="BKMK_In_this_topic"></a> In diesem Thema  
 [Komponententestframeworks und Testprojekte](#BKMK_Unit_test_frameworks_and_test_projects)  
  
 [Ausführen von Tests im Test-Explorer](#BKMK_Running_tests_in_Test_Explorer)  
  
-   [Ausführen von Tests](#BKMK_Running_tests)  
  
 [Anzeigen von Testergebnissen](#BKMK_Viewing_test_results)  
  
-   [Anzeigen von Testdetails](#BKMK_Viewing_test_details)  
  
-   [Anzeigen des Quellcodes einer Testmethode](#BKMK_Viewing_the_source_code_of_a_test_method)  
  
 [Organisieren der Testliste](#BKMK_Organizing_the_test_list)  
  
-   [Gruppieren von Tests](#BKMK_Grouping_tests)  
  
-   [Suchen und Filtern der Testliste](#BKMK_Searching_and_filtering_the_test_list)  
  
 [Debuggen von Komponententests](#BKMK_Debugging_unit_tests)  
  
##  <a name="BKMK_Unit_test_frameworks_and_test_projects"></a> Komponententestframeworks und Testprojekte  
 Visual Studio Express für Windows Store-Apps schließt die Microsoft-Unittest-Frameworks für verwalteten und nativen C++-Code ein. Im Test-Explorer können Tests aus mehreren Testprojekten in einer Projektmappe und aus Testklassen ausgeführt werden, die Teil der Produktionscodeprojekte sind. Testprojekte können sich aus jeder beliebigen Kombination von Visual C++- oder Visual C#- und Visual Basic-Komponententest-Frameworks zusammensetzen. Wenn der zu testende Code für .NET Framework geschrieben wird, kann das Testprojekt in jeder .NET Framework-Sprache geschrieben sein, unabhängig von der Sprache des Zielcodes. Systemeigene C/C++-Codeprojekte müssen mithilfe eines Komponententest-Frameworks für C++ getestet werden.  
  
##  <a name="BKMK_Running_tests_in_Test_Explorer"></a> Ausführen von Tests im Test-Explorer  
 Wenn Sie das Testprojekt erstellen, werden die Tests im Test-Explorer angezeigt. Falls der Test-Explorer nicht geöffnet ist, wählen Sie im Visual Studio-Menü nacheinander **Test** , **Fenster**und dann **Test-Explorer**aus.  
  
 ![Komponententest-Explorer](../ide/media/ute-failedpassednotrunsummary.png "UTE_FailedPassedNotRunSummary")  
  
 Beim Ausführen, Schreiben und erneuten Ausführen der Tests werden die Ergebnisse vom Test-Explorer in den Standardgruppen **Fehlgeschlagene Tests**, **Bestandene Tests**, **Abgebrochene Tests** und **Nicht ausgeführte Tests**angezeigt. Sie können die Gruppierung der Tests im Test-Explorer ändern.  
  
 Über die Test-Explorer-Symbolleiste können Sie die meisten Aktionen zum Suchen, Organisieren und Ausführen von Tests ausführen.  
  
 ![Tests von der Test-Explorer-Symbolleiste ausführen](../test/media/ute-toolbar.png "UTE_ToolBar")  
  
###  <a name="BKMK_Running_tests"></a> Ausführen von Tests  
 Sie können alle Tests in der Projektmappe, alle Tests in einer Gruppe oder einen Satz ausgewählter Tests ausführen. Führen Sie einen der folgenden Schritte aus:  
  
-   Wählen Sie zum Ausführen aller Tests in einer Projektmappe **Alle ausführen**aus.  
  
-   Wählen Sie zum Ausführen aller Tests in einer Standardgruppe **Ausführen...** und dann im Menü die Gruppe aus.  
  
-   Wählen Sie die einzelnen auszuführenden Tests aus, öffnen Sie das Kontextmenü für einen ausgewählten Test, und wählen Sie dann **Ausgewählte Tests ausführen** aus.  
  
 Während der Testausführung wird die oben im Fenster "Test-Explorer" angezeigte Erfolgreich/Fehler-Leiste animiert. Am Ende des Testlaufs wird die Erfolgreich/Fehler-Leiste grün, wenn alle Tests erfolgreich verlaufen, oder rot, falls ein beliebiger Test fehlschlägt.  
  
##  <a name="BKMK_Viewing_test_results"></a> Anzeigen von Testergebnissen  
 Beim Ausführen, Schreiben und erneuten Ausführen der Tests werden die Ergebnisse vom Test-Explorer in den Gruppen **Fehlgeschlagene Tests**, **Bestandene Tests**, **Abgebrochene Tests** sowie **Nicht ausgeführte Tests**angezeigt. Im Detailbereich unten im Test-Explorer wird eine Zusammenfassung des Testlaufs angezeigt.  
  
###  <a name="BKMK_Viewing_test_details"></a> Anzeigen von Testdetails  
 Zum Anzeigen der Details eines einzelnen Tests wählen Sie den jeweiligen Test aus.  
  
 Im Testdetailbereich werden folgende Informationen angezeigt:  
  
-   Quelldateiname und Zeilennummer der Testmethode  
  
-   Teststatus  
  
-   Ausführungsdauer der Testmethode  
  
 Bei einem fehlgeschlagenen Test wird im Detailbereich außerdem Folgendes angezeigt:  
  
-   Die vom Komponententest-Framework für den Test zurückgegebene Meldung  
  
-   Die Stapelüberwachung zum Zeitpunkt des Testfehlers  
  
###  <a name="BKMK_Viewing_the_source_code_of_a_test_method"></a> Anzeigen des Quellcodes einer Testmethode  
 Um den Quellcode für eine Testmethode im Visual Studio-Editor anzuzeigen, wählen Sie zunächst den Test und dann **Test öffnen** im Kontextmenü (Tastatur: F12) aus.  
  
##  <a name="BKMK_Organizing_the_test_list"></a> Organisieren der Testliste  
  
###  <a name="BKMK_Grouping_tests"></a> Gruppieren von Tests  
 Standardmäßig werden im Test-Explorer die Tests als untergeordnete Knoten von **Fehlerhafte Tests**, **Bestandene Tests**, **Abgebrochene Tests** und **Übersprungene Tests** angezeigt.  
  
|||  
|-|-|  
|![Gruppenschaltfläche „Test-Explorer“](../test/media/ute-groupby-btn.png "UTE_GroupBy_btn")|Um die Tests nach der Dauer ihrer Ausführung zu gruppieren, öffnen Sie die Liste **Gruppieren nach** und wählen **Dauer** aus. Wählen Sie **Testergebnis** aus, um zur ursprünglichen Gruppierung zu wechseln.|  
  
###  <a name="BKMK_Searching_and_filtering_the_test_list"></a> Suchen und Filtern der Testliste  
 Wenn Sie über viele Tests verfügen, können Sie im Test-Explorer-Suchfeld eine Eingabe vornehmen, um die Liste entsprechend der angegebenen Zeichenfolge zu filtern. Sie können den Filter auf bestimmte Typen von Zeichenfolgen einschränken, indem Sie vor der Eingabe der Suchzeichenfolge in der Filterliste eine Auswahl vornehmen.  
  
 ![Suchfilterkategorien](../test/media/ute-searchfilter.png "UTE_SearchFilter")  
  
##  <a name="BKMK_Debugging_unit_tests"></a> Debuggen von Komponententests  
 Mit dem Test-Explorer können Sie Debugsitzungen für Tests starten. Beim schrittweisen Durchlaufen des Codes mit dem Visual Studio-Debugger wechseln Sie nahtlos zwischen den Komponententests und dem zu testenden Projekt hin und zurück. Starten des Debuggens:  
  
1.  Legen Sie im Visual Studio-Editor in mindestens einer zu debuggenden Testmethode einen Haltepunkt fest.  
  
    > [!NOTE]
    >  Da Testmethoden in jeder die oft ausgegebene Befehlszeilen  Reihenfolge ausgeführt werden können, legen Sie Haltepunkte in allen Testmethoden fest, die Sie debuggen möchten.  
  
2.  Wählen Sie im Test-Explorer die Testmethoden aus, und wählen Sie dann im Kontextmenü **Ausgewählte Tests debuggen** aus.  
  
 Weitere Informationen zum Debugger finden Sie unter [Debugging in Visual Studio](../debugger/debugging-in-visual-studio.md).



