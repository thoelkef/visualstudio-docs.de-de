---
title: Analysieren der Aktivität virtueller Benutzer bei Auslastungstests in Visual Studio
ms.date: 10/03/2016
ms.topic: conceptual
f1_keywords:
- vs.test.load.monitor.activitychart
helpviewer_keywords:
- virtual user activity chart
- load test, virtual user activity chart
ms.assetid: 63f4bd42-3cfb-4eee-af68-e8334976539e
author: gewarren
ms.author: gewarren
manager: douge
ms.prod: visual-studio-dev15
ms.technology: vs-ide-test
ms.openlocfilehash: c91cd1a2ea721743c289b6664ddd0a76ceedbc4f
ms.sourcegitcommit: 58052c29fc61c9a1ca55a64a63a7fdcde34668a4
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 06/04/2018
ms.locfileid: "34750837"
---
# <a name="analyzing-load-test-virtual-user-activity-in-the-details-view-of-the-load-test-analyzer"></a>Analyzing Load Test Virtual User Activity in the Details View of the Load Test Analyzer

**Diagramm für Aktivitäten virtueller Benutzer**

 ![Diagramm für Aktivitäten virtueller Benutzer](../test/media/virtual_actchart.png)

 In der Detailansicht wird das Diagramm für Aktivitäten virtueller Benutzer angezeigt, das zur visuellen Analyse der Aktivitäten verwendet wird, die die einzelnen virtuellen Benutzer während des Auslastungstests ausgeführt haben. Im Diagramm für Aktivitäten virtueller Benutzer können Sie Benutzeraktivitäts- und Auslastungsmuster erkennen, fehlgeschlagene oder langsame Tests in Zusammenhang setzen und Anforderungen bei anderen Aktivitäten virtueller Benutzer anzeigen. Anhand des Diagramms für die Aktivitäten virtueller Benutzer können Sie auch Spitzen in der CPU-Auslastung und Tiefstände bei den Anforderungen pro Sekunde erkennen und nachvollziehen, welche Tests oder Seiten während der Spitzen und Tiefstände ausgeführt wurden.

> [!NOTE]
> Bevor Sie den Auslastungstest ausführen, für den Sie das Diagramm für Aktivitäten virtueller Benutzer verwenden möchten, müssen Sie mithilfe des Auslastungstest-Editors überprüfen, ob die Eigenschaft **Speicher für Details der zeitlichen Steuerung** auf **AllIndividualDetails** festgelegt ist. Weitere Informationen finden Sie unter [How to: Configure Collecting Full Details to Enable the Virtual User Activity Chart (Vorgehensweise: Konfigurieren der Erfassung aller Details zur Verwendung des Diagramms für Aktivitäten virtueller Benutzer)](../test/how-to-configure-load-tests-to-collect-full-details.md).

 **Bereich „Detaillegende“**

 ![Detaillegendenbereich](../test/media/ltest_detailslegend.png)

 Der Bereich "Detaillegende" wird im Diagramm für Aktivitäten virtueller Benutzer angezeigt. Im Bereich "Detaillegende" können Sie Tests, Seiten und Transaktionen auf Grundlage unterschiedlicher Kriterien herausfiltern. Sie können z. B. bestimmte Tests aus der Ansicht bzw. alle erfolgreich verlaufenen Tests oder Tests entfernen, die aufgrund bestimmter Fehler fehlgeschlagen sind. Sie können auch alle Tests entfernen, für die keine Protokolle verfügbar sind.

 Sie können fehlgeschlagene Tests markieren, woraufhin alle fehlgeschlagenen Tests rot hervorgehoben werden. Sie können auch Tests hervorheben, für die Testprotokolle vorhanden sind. Tests mit Protokollen erhalten die Farbe Grün.

 **Bereich „Filterergebnisse“**

 ![Filterergebnisbereich](../test/media/ltest_filterresults.png)

 Der Bereich "Filterergebnisse" wird im Diagramm für Aktivitäten virtueller Benutzer angezeigt. Im Bereich "Filterergebnisse" können Sie Ergebnisse wie folgt filtern:

-   **Nur Ergebnisse mit Protokollen anzeigen**: zeigt nur Testergebnisse an, denen Testprotokolle zugeordnet sind.

-   **Erfolgreiche Ergebnisse anzeigen**: zeigt erfolgreiche Ergebnisse an.

-   **Ergebnisse mit Fehlern anzeigen**: zeigt Ergebnisse mit Fehlern an, die beim Debuggen hilfreich sein können.

## <a name="tasks"></a>Aufgaben

|Aufgaben|Verwandte Themen|
|-----------|-----------------------|
|**Konfigurieren des Auslastungstests für die Verwendung des Diagramms für die Aktivitäten virtueller Benutzer:** Vor der Ausführung eines Auslastungstests, in dem Sie die Daten zu Aktivitäten virtueller Benutzer anzeigen möchten, müssen zunächst die Eigenschafteneinstellungen für den Auslastungstest konfiguriert werden.|-   [Vorgehensweise: Konfigurieren der Erfassung aller Details zur Verwendung des Diagramms für Aktivitäten virtueller Benutzer](../test/how-to-configure-load-tests-to-collect-full-details.md)|
|**Ausführen des Auslastungstests:** Nachdem Sie einen Auslastungstest erstellt und ihn so konfiguriert haben, dass Daten zu den Aktivitäten virtueller Benutzer gesammelt werden, müssen Sie den Test vollständig ausführen, um das Diagramm für die Aktivitäten virtueller Benutzer anzuzeigen.||
|**Anzeigen der Auslastungstestergebnisse, die Daten zu den Aktivitäten virtueller Benutzer enthalten:** Nach dem Erstellen, Konfigurieren und vollständigen Ausführen des Auslastungstests können Sie die Aktivitätsdaten virtueller Benutzer im entsprechenden Diagramm anzeigen.|-   [Analyze Load Test Results (Analysieren von Auslastungstestergebnissen)](../test/analyze-load-test-results-using-the-load-test-analyzer.md)<br />-   [How to: Analyze What Virtual Users Are Doing During a Load Test (Vorgehensweise: Analysieren der Aktivitäten virtueller Benutzer während eines Auslastungstests)](../test/how-to-analyze-virtual-user-activity-during-a-load-test.md)|
|**Isolieren von Leistungsproblemen in Auslastungstests:** Mithilfe des Diagramms für Aktivitäten virtueller Benutzer können Leistungsprobleme im Auslastungstest isoliert werden.|-   [Walkthrough: Using the Virtual User Activity Chart to Isolate Issues (Exemplarische Vorgehensweise: Verwenden des Diagramms für Aktivitäten virtueller Benutzer zum Isolieren von Problemen)](../test/walkthrough-use-the-virtual-user-activity-chart-to-isolate-issues.md)|

## <a name="see-also"></a>Siehe auch

- [Analyze Load Test Results (Analysieren von Auslastungstestergebnissen)](../test/analyze-load-test-results-using-the-load-test-analyzer.md)
- [Analyze Load Test Results and Errors in the Tables View (Analysieren von Auslastungstestergebnissen und -fehlern in der Tabellenansicht)](../test/analyze-load-test-results-and-errors-in-the-tables-view.md)