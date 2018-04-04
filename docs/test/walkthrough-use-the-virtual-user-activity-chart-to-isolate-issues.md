---
title: Verwenden des Diagramms für Aktivitäten virtueller Benutzer bei Auslastungstests in Visual Studio | Microsoft-Dokumentation
ms.date: 10/19/2016
ms.topic: article
helpviewer_keywords:
- load tests, virtual user activity chart
- virtual user activity chart, isolating performance issues
ms.assetid: d1c10fb9-cfeb-4e7f-9991-2d1e1103699e
author: gewarren
ms.author: gewarren
manager: ghogen
ms.technology: vs-ide-test
ms.openlocfilehash: f7063775f093b08b859343fbc314399d0cc9fdd4
ms.sourcegitcommit: 900ed1e299cd5bba56249cef8f5cf3981b10cb1c
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 03/19/2018
---
# <a name="walkthrough-using-the-virtual-user-activity-chart-to-isolate-issues"></a>Walkthrough: Using the Virtual User Activity Chart to Isolate Issues

In dieser exemplarischen Vorgehensweise erfahren Sie, wie Sie mit dem Diagramm für Aktivitäten virtueller Benutzer Fehler isolieren, die für einzelne virtuelle Benutzer aufgetreten sind, durch die der Auslastungstest ausgeführt wurde.

 Mit dem Diagramm für Aktivitäten virtueller Benutzer können die Aktivitäten von virtuellen Benutzern dargestellt werden, die dem Auslastungstest zugeordnet sind. Jede Zeile im Diagramm stellt einen einzelnen virtuellen Benutzer dar. Das Diagramm für Aktivitäten virtueller Benutzer gibt genauen Aufschluss über die Aktionen der einzelnen virtuellen Benutzer während des Tests. So können Sie Leistungsprobleme isolieren, indem Sie Muster der Benutzeraktivität anzeigen, Muster laden, fehlgeschlagene oder langsame Tests in Zusammenhang setzen und Anforderungen mit anderen Aktivitäten virtueller Benutzer anzeigen. Das Diagramm für die Aktivitäten virtueller Benutzer ist erst nach dem Ausführen des Auslastungstests verfügbar.

 Im Verlauf dieser exemplarischen Vorgehensweise führen Sie folgende Aufgaben aus:

-   Erfahren Sie, wie Sie die folgenden Tools verwenden, die dem Diagramm für die Aktivitäten der virtuellen Benutzer zugeordnet sind:

    -   Verwenden Sie das Tool **Zoom zum Zeitraum**, um einen bestimmten Zeitraum im Diagramm anzugeben, den Sie analysieren möchten.

    -   Verwenden Sie die Bereiche **Detaillegende** und **Filterergebnisse**, um Filter auf das Diagramm anzuwenden und so Probleme leichter zu isolieren.

-   Analysieren Sie mithilfe des Diagramms für die Aktivitäten der virtuellen Benutzer einen Fehler, der für einen bestimmten virtuellen Benutzer aufgetreten ist, und zeigen Sie die Details zum problematischen Fehlertyp an.

 Weitere Informationen finden Sie unter [Analyzing Virtual User Activity in the Details View (Analysieren der Aktivität virtueller Benutzer in der Detailansicht)](../test/analyze-load-test-virtual-user-activity-in-the-details-view.md).

## <a name="prerequisites"></a>Erforderliche Komponenten

-   Visual Studio Enterprise

-   Schließen Sie diese Verfahren ab:

    -   [Aufzeichnen und Ausführen eines Webleistungstests](http://msdn.microsoft.com/en-us/bd0a82fd-cec0-4861-bc09-e1b0b2d258ef)

    -   [Erstellen und Ausführen eines Auslastungstests](http://msdn.microsoft.com/en-us/7041cbcf-9ab1-4579-98ff-8f296aeaded4)

## <a name="open-the-colorwebapp-solution-created-in-the-previous-walkthroughs"></a>Öffnen der in vorherigen exemplarischen Vorgehensweisen erstellten Projektmappe "ColorWebApp"

### <a name="open-the-solution"></a>Öffnen der Projektmappe

1.  Starten Sie Visual Studio.

2.  Öffnen Sie die Projektmappe "ColorWebApp", die "LoadTest1.loadtest" enthält. Dieser Auslastungstest ergibt sich aus der Durchführung der Schritte in den drei exemplarischen Vorgehensweisen, die am Anfang dieses Themas im Abschnitt zu den erforderlichen Komponenten und Voraussetzungen aufgeführt sind.

     Bei den verbleibenden Schritten in dieser exemplarischen Vorgehensweise wird von einer Webanwendung mit dem Namen "ColorWebApp", einem Webleistungstest mit dem Namen "ColorWebAppTest.webtest" und einem Auslastungstest mit dem Namen "LoadTest1.loadtest" ausgegangen.

## <a name="run-the-load-test"></a>Ausführen des Auslastungstests
 Führen Sie den Auslastungstest aus, um Aktivitätsdaten von virtuellen Benutzern zu sammeln.

### <a name="run-the-load-test-to-collect-virtual-user-activity-data"></a>Ausführen des Auslastungstests, um Aktivitätsdaten von virtuellen Benutzern zu sammeln

-   Klicken Sie auf der Symbolleiste im Auslastungstest-Editor auf die Schaltfläche **Ausführen**. Die Ausführung von "LoadTest1" beginnt.

## <a name="isolate-issues-in-the-virtual-user-activity-chart"></a>Isolieren von Problemen im Diagramm für Aktivitäten virtueller Benutzer

Nach dem Ausführen des Auslastungstests und dem Sammeln der Aktivitätsdaten von virtuellen Benutzern können die Daten in den Auslastungstestergebnissen mithilfe der Detailansicht des Auslastungstest-Analyzers im Diagramm für Aktivitäten virtueller Benutzer angezeigt werden. Außerdem können mithilfe des Diagramms für Aktivitäten virtueller Benutzer Leistungsprobleme im Auslastungstest isoliert werden.

### <a name="to-use-the-virtual-user-activity-chart-in-your-load-test-results"></a>So verwenden Sie das Diagramm für Aktivitäten virtueller Benutzer in den Auslastungstestergebnissen

1.  Nachdem die Ausführung des Auslastungstests abgeschlossen wurde, wird die Seite "Zusammenfassung" für die Auslastungstestergebnisse im Auslastungstest-Analyzer angezeigt. Klicken Sie auf der Symbolleiste auf die Schaltfläche **Diagramme**.

     Die Ansicht "Diagramme" wird angezeigt.

2.  Klicken Sie im Diagramm **Seitenantwortzeit** mit der rechten Maustaste auf eine Stelle neben einem der Symbole für Schwellenwertverletzungen, und wählen Sie die Option **Zu Benutzerdetail wechseln** aus.

    > [!NOTE]
    > Sie können die Schaltfläche **Details** auf der Symbolleiste des Auslastungstest-Editors verwenden, um auch das Diagramm für Benutzeraktivitäten zu öffnen. Wenn Sie jedoch die Option **Zu Benutzerdetail wechseln** verwenden, wird im Diagramm für Aktivitäten virtueller Benutzer automatisch die Ansicht des Teils des Tests vergrößert, auf den Sie im Diagramm mit der rechten Maustaste geklickt haben.

     Die Detailansicht wird angezeigt, wobei im **Diagramm für Aktivitäten virtueller Benutzer** der Zeitraum im Mittelpunkt steht, an dem Schwellenwertverletzungen aufgetreten sind.

     Auf der y-Achse stellen die horizontalen Elemente einzelne virtuelle Benutzer dar. Die x-Achse zeigt die Zeitachse für den Auslastungstestlauf an.

3.  Stellen Sie im Tool **Zoom zum Zeitraum** unter dem **Diagramm für Aktivitäten virtueller Benutzer** die linken und rechten Schieberegler so ein, dass sich beide in der Nähe des Symbols für die Schwellenwertverletzung befinden. Hierdurch wird die Zeitskala im **Diagramm für Aktivitäten virtueller Benutzer** geändert.

4.  Aktivieren Sie in der **Detaillegende** das Kontrollkästchen **(Fehler hervorheben)**. Der virtuelle Benutzer, der die Schwellenwertverletzung verursacht hat, wird hervorgehoben.

5.  Deaktivieren Sie im Bereich **Filterergebnisse** die Kontrollkästchen **Erfolgreiche Ergebnisse anzeigen** und **HttpError**, aber lassen Sie das Kontrollkästchen **ValidationRuleError** aktiviert.

     Im **Diagramm für Aktivitäten virtueller Benutzer** werden nur diejenigen virtuellen Benutzer angezeigt, die mehr als drei Sekunden auf der Seite „Red.aspx“ verbracht haben. Dieser Wert wurde in der vorherigen exemplarischen Vorgehensweise über die Schwellenwertverletzung konfiguriert.

6.  Zeigen Sie mit der Maus auf die horizontale Linie, die den virtuellen Benutzer mit dem Validierungsregelfehler für die Schwellenwertverletzung darstellt.

7.  Eine QuickInfo mit den folgenden Informationen wird angezeigt:

    -   **Benutzer-ID**

    -   **Szenario**

    -   **Test**

    -   **Ergebnis**

    -   **Network**

    -   **Startzeit**

    -   **Dauer**

    -   **Agent**

    -   **Testprotokoll**

8.  Beachten Sie, dass **Testprotokoll** ein Link ist. Klicken Sie auf den Link **Testprotokoll**.

9. Der Webleistungstest "ColorWebTest", der dem Protokoll zugeordnet ist, wird im Webleistungstest-Ergebnisviewer geöffnet. So können Sie isolieren, wo die Schwellenwertverletzungen aufgetreten sind.

     Sie können verschiedene Einstellungen in den Bereichen **Detaillegende** und **Filterergebnisse** verwenden, um Leistungsprobleme und Fehler in den Auslastungstests leichter zu isolieren. Experimentieren Sie mit diesen Einstellungen und mit dem Tool **Zoom zum Zeitraum**, um zu sehen, wie die Daten für virtuelle Benutzer im **Diagramm für Aktivitäten virtueller Benutzer** dargestellt werden.

## <a name="see-also"></a>Siehe auch

- [Analyzing Virtual User Activity in the Details View (Analysieren der Aktivität virtueller Benutzer in der Detailansicht)](../test/analyze-load-test-virtual-user-activity-in-the-details-view.md)
- [Testcontroller und Test-Agents](configure-test-agents-and-controllers-for-load-tests.md)
- [Gewusst wie: Erstellen einer Testeinstellung für einen verteilten Auslastungstest](../test/how-to-create-a-test-setting-for-a-distributed-load-test.md)
- [Installieren und Konfigurieren von Test-Agents](../test/lab-management/install-configure-test-agents.md)
- [Collect Diagnostic Information Using Test Settings (Erfassen von Diagnoseinformationen mithilfe von Testeinstellungen)](../test/collect-diagnostic-information-using-test-settings.md)