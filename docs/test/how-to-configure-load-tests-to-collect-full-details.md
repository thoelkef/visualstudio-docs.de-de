---
title: Erfassen aller Details für virtuelle Benutzer für Auslastungstests in Visual Studio | Microsoft-Dokumentation
ms.date: 10/19/2016
ms.topic: article
helpviewer_keywords:
- load tests, virtual user activity chart, configuring
- virtual user activity chart, configuring
ms.assetid: cb22e43b-af4d-4e09-9389-3c3fa00786f7
author: gewarren
ms.author: gewarren
manager: ghogen
ms.technology: vs-ide-test
ms.openlocfilehash: b410c91ff2b6c57b86c7fe377df4bf31173f9384
ms.sourcegitcommit: 900ed1e299cd5bba56249cef8f5cf3981b10cb1c
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 03/19/2018
---
# <a name="how-to-configure-load-tests-to-collect-full-details-to-enable-virtual-user-activity-in-test-results"></a>Gewusst wie: Konfigurieren von Auslastungstests zum Erfassen aller Details, um Aktivitäten virtueller Benutzer in Testergebnissen zu ermöglichen

Um das Diagramm für Aktivitäten virtueller Benutzer für den Auslastungstest zu verwenden, müssen Sie den Auslastungstest so konfigurieren, dass vollständige Details gesammelt werden. Um den Auslastungstest entsprechend zu konfigurieren, wählen Sie die Einstellung **Alle einzelnen Details** für die dem Auslastungstest zugeordnete Eigenschaft **Speicher für Details der zeitlichen Steuerung** aus. In diesem Modus werden im Auslastungstest ausführliche Informationen zu allen Tests, Seiten und Transaktionen gesammelt.

 Wenn Sie ein Projekt von einer früheren Version des Visual Studio-Auslastungstests aktualisieren, verwenden Sie die Schritte in der folgenden Prozedur, um eine vollständige Detailauflistung zu aktivieren.

 Die Einstellung **Alle einzelnen Details** für die Eigenschaft **Speicher für Details der zeitlichen Steuerung** kann auf eine beliebige der folgenden Optionen festgelegt werden:

-   **Alle einzelnen Details:** Sammelt und speichert einzelne Zeitsteuerungsdaten für alle Tests, Transaktionen und Seiten, die während des Tests ausgegeben werden.

    > [!NOTE]
    > Die Option **Alle einzelnen Details** muss aktiviert werden, um Informationen zu virtuellen Benutzerdaten in den Auslastungstestergebnissen zu aktivieren.

-   **Keine:** Es werden keine einzelnen Details zur zeitlichen Steuerung erfasst. Die Durchschnittswerte sind jedoch nach wie vor verfügbar.

-   **Nur Statistik**: speichert einzelne Zeitsteuerungsdaten, jedoch nur als prozentuale Daten. Dadurch werden Speicherplatzressourcen gespart.

## <a name="to-configure-the-timing-details-storage-property-in-a-load-test"></a>So konfigurieren Sie die Speichereigenschaft für Zeitsteuerungsdetails in einem Auslastungstest

1.  Öffnen Sie im Auslastungstest-Editor einen Auslastungstest.

2.  Erweitern Sie den Knoten **Laufzeiteinstellungen** im Auslastungstest.

3.  Wählen Sie die Laufzeiteinstellungen, die Sie konfigurieren möchten, z.B. **Run Settings1[Active]** (Laufzeiteinstellungen1[Aktiv]).

4.  Öffnen Sie das Eigenschaftenfenster. Klicken Sie im Menü **Ansicht** auf **Eigenschaftenfenster**.

5.  Wählen Sie unter der Kategorie **Ergebnisse** die Eigenschaft **Speicher für Details der zeitlichen Steuerung**, und wählen Sie **Alle einzelnen Details** aus.

     Nachdem Sie die Einstellung **Alle einzelnen Details** für die Eigenschaft **Speicher für Details der zeitlichen Steuerung** konfiguriert haben, können Sie den Auslastungstest ausführen und das Diagramm für die Aktivitäten virtueller Benutzer anzeigen. Weitere Informationen finden Sie unter [How to: Analyze What Virtual Users Are Doing During a Load Test (Vorgehensweise: Analysieren der Aktivitäten virtueller Benutzer während eines Auslastungstests)](../test/how-to-analyze-virtual-user-activity-during-a-load-test.md).

## <a name="see-also"></a>Siehe auch

- [Analyzing Virtual User Activity in the Details View (Analysieren der Aktivität virtueller Benutzer in der Detailansicht)](../test/analyze-load-test-virtual-user-activity-in-the-details-view.md)
- [Exemplarische Vorgehensweise: Verwenden des Diagramms für Aktivitäten virtueller Benutzer zum Isolieren von Problemen](../test/walkthrough-use-the-virtual-user-activity-chart-to-isolate-issues.md)