---
title: Vergrößern von Diagrammen für Auslastungstestergebnisse in Visual Studio | Microsoft-Dokumentation
ms.date: 10/19/2016
ms.topic: conceptual
f1_keywords:
- vs.test.load.monitor.graphzoom
helpviewer_keywords:
- graphs, analyzing load tests
- load tests, zooming with graphs
ms.assetid: 729b4c30-4bc3-4698-91b3-17a676897443
author: gewarren
ms.author: gewarren
manager: douge
ms.technology: vs-ide-test
ms.openlocfilehash: 9e2379161051c821af07b6da5b102177178a0d7f
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/16/2018
---
# <a name="how-to-zoom-in-on-a-region-of-the-graph-in-load-test-results"></a>Gewusst wie: Vergrößern eines Diagrammbereichs in Auslastungstestergebnissen

Nach einem abgeschlossenen Auslastungstest können Sie die Zoomleisten zum Vergrößern und Anzeigen eines Bereichs im Diagramm verwenden. Durch das Vergrößern können Sie genauere Details der Daten anzeigen, die bei einem Auslastungstestlauf generiert wurden.

> [!NOTE]
> Die Vergrößerungsfunktion ist nur verfügbar, wenn Sie das Ergebnis eines abgeschlossenen Auslastungstests analysieren. Beim Überprüfen der Ergebnisse eines laufenden Tests ist sie nicht verfügbar.

 Das Zoomsteuerelement wird nur dann im Auslastungstest-Analyzer angezeigt, wenn Sie ein Auslastungstestergebnis im Zoommodus anzeigen. Der Zoommodus wird in der Diagrammansicht aktiviert, wenn ein Auslastungstest abgeschlossen wurde oder ein zuvor ausgeführter Auslastungstest geladen wird. Die Zoomsteuerelemente können in den Diagrammen mit der Option "Zoomsteuerelemente anzeigen" auf der Symbolleiste ein- oder ausgeblendet werden.

 Der Zoom für die horizontale x-Achse kann angepasst werden, um bestimmte Zeiträume während des Auslastungstests zu analysieren. Der Zoom für die vertikale y-Achse kann angepasst werden, um bestimmte Wertebereiche für die im Diagramm enthaltenen Indikatoren zu analysieren.

 Die Zoomsteuerelemente für die horizontale Zeitskala und den vertikalen Wertebereich können mit der Maus eingestellt werden. Das Steuerelement für die horizontale Zeitskala kann auch mit den NACH-RECHTS- und NACH-LINKS-TASTEN eingestellt werden. Beim Einstellen des Zoomsteuerelements mit den Pfeiltasten kann der Fensterbereich um jeweils 1 Samplingintervall verstellt werden. Wenn Sie die Pfeiltasten zusammen mit der UMSCHALTTASTE verwenden, werden Anpassungen in Schritten von 10 Samplingintervallen vorgenommen werden.

 Um das Zoomsteuerelement mit den Pfeiltasten einzustellen, legen Sie zunächst den Fokus mit der TAB-TASTE auf das Zoomsteuerelement fest. Wenn der linke Schieberegler den Fokus hat, verschieben die Pfeiltasten die Startgrenze des Zoomfensters um ein Intervall nach links oder rechts. Wenn der mittlere Schieberegler den Fokus hat, können Sie mit den Pfeiltasten im Zoomfenster einen Bildlauf um ein Samplingintervall nach links bzw. rechts durchführen, ohne die Größe des Zoomfensters zu ändern. Mit dem rechten Schieberegler wird das Ende des Bereichs im Zoomfenster um ein Samplingintervall verschoben, sodass der Bereich erweitert oder reduziert wird.

 Um die horizontalen und vertikalen Zoomsteuerelemente auf die Anzeige der vollständigen Zeitskala und Wertebereiche zurückzusetzen, können Sie die Optionen **Horizontal verkleinern**, **Vertikal verkleinern** oder **Beide verkleinern** im Popupmenü des Diagramms verwenden.

> [!TIP]
> Mit dem Symbolleistenbefehl **Horizontale Zoomsteuerelemente synchronisieren** kann die automatische horizontale Zoomsynchronisierung aktiviert bzw. deaktiviert werden. Wenn die Synchronisierung aktiviert ist, gelten alle Zoomeinstellungen, die Sie für ein Diagramm vornehmen, auch für alle anderen Diagramme in der Diagrammansicht.

 ![Zoomsteuerelement der Diagrammansicht](../test/media/ltest_zoomcontrol.png "LTest_ZoomControl") Zoomsteuerelement der Diagrammansicht

 In der obigen Abbildung wurde das Diagramm "Getestetes System" vergrößert, um Schwellenwertverletzungen zu untersuchen. Die Schwellenwertverletzungen wurden mit dem Befehl **Schwellenwertverletzungen im Diagramm anzeigen** in der Dropdownliste **Diagrammoptionen** auf der Symbolleiste aktiviert.

 Weitere Informationen finden Sie unter [Analyze Load Test Results in the Graphs View (Analysieren von Auslastungstestergebnissen in der Diagrammansicht)](../test/analyze-load-test-results-in-the-graphs-view.md).

## <a name="displaying-graphs"></a>Anzeigen von Diagrammen
 Bevor Sie die Anzeige eines Diagramms durch Vergrößern bzw. Verkleinern oder einen Bildlauf ändern, führen Sie die folgende Prozedur zum Anzeigen von Diagrammen aus.

### <a name="to-display-graphs"></a>So zeigen Sie Diagramme an

1.  Führen Sie einen Auslastungstest bis zum Ende aus.

2.  Klicken Sie nach Abschluss des Auslastungstestlaufs im Dialogfeld zur Anzeige der Ergebnisse im Speicher für Auslastungstestergebnisse auf **Ja**.

     \- oder –

     Zeigen Sie die Details eines zuvor ausgeführten Auslastungstests an. Weitere Informationen finden Sie unter [How to: Access Load Test Results for Analysis (Vorgehensweise: Zugreifen auf Auslastungstestergebnisse für die Analyse)](../test/how-to-access-load-test-results-for-analysis.md).

3.  Klicken Sie auf **Diagramme**, wenn die Diagramme nicht angezeigt werden.

4.  Wenn keine Zoomleisten angezeigt werden, klicken Sie auf **Zoomsteuerelemente anzeigen**.

     Zwei Zoomleisten sind für jedes Diagramm verfügbar. Die Zoomleiste, durch die die vertikale Skala gesteuert wird, wird links vom Diagramm angezeigt. Die Zoomleiste, durch die horizontale Skala gesteuert wird, wird unterhalb des Diagramms angezeigt.

     Jede Zoomleiste verfügt über zwei Handles. Ein Handle ist eine rechteckige Fläche an beiden Enden der Zoomleiste.

## <a name="zooming-and-scrolling"></a>Zoomen und Durchführen eines Bildlaufs
 Wenn mehrere Diagramme angezeigt werden, können Sie sie synchronisieren, sodass derselbe Bereich des Auslastungstestlaufs angezeigt wird.

### <a name="to-synchronize-zooming-and-scrolling"></a>So synchronisieren Sie das Zoomen und Durchführen eines Bildlaufs

1.  Klicken Sie in der Auslastungstestanalyse auf **Horizontale Zoomsteuerelemente synchronisieren**.

     Wenn die Schaltfläche Horizontale Zoomsteuerelemente synchronisieren aktiviert ist und Sie in der Zeitskala eines einzelnen Diagramms zoomen und einen Bildlauf ausführen, wird auch für die Zeitskala der übrigen Diagramme ein Zoom- und Bildlaufvorgang ausgeführt.

2.  Klicken Sie erneut auf "Horizontale Zoomsteuerelemente synchronisieren".

     Wenn die Schaltfläche Horizontale Zoomsteuerelemente synchronisieren nicht aktiviert ist und Sie in der Zeitskala eines einzelnen Diagramms zoomen und einen Bildlauf ausführen, wirkt sich dies nur auf dieses Diagramm aus.

### <a name="to-zoom-and-scroll-to-a-region-of-the-graph"></a>So zoomen und führen Sie einen Bildlauf für einen Bereich des Diagramms aus

1.  Ziehen Sie auf der Zoomleiste unterhalb eines Diagramms den linken Handle nach rechts.

     Dadurch wird der letzte Teil des Testlaufs vergrößert. Entsprechend werden frühere Teile des Testlaufs vergrößert, wenn Sie den rechten Handle nach links ziehen.

2.  Um die Ansicht eines bestimmten Bereichs zu vergrößern, schieben Sie beide Handles zur Mitte eines Diagramms.

     Je näher die beiden Handles beieinander liegen, desto kürzere und detailliertere Segmente des Auslastungstests werden bei zunehmender Vergrößerung angezeigt.

     Klicken Sie auf den mittleren Bereich der Zoomleiste, und ziehen Sie ihn, um einen Bildlauf zu einer bestimmten Stelle im Auslastungstest auszuführen.

### <a name="to-zoom-to-a-region-of-the-graph-by-choosing-and-dragging"></a>So zoomen Sie durch Klicken und Ziehen zu einem Diagrammbereich

1.  Klicken Sie auf ein Diagramm an einem Ende des Zoombereichs.

2.  Ziehen Sie den Mauszeiger ans andere Ende des Zoombereichs.

3.  Lassen Sie die Maustaste los.

     Dadurch wird der Bereich vergrößert, den Sie durch Klicken und Ziehen definiert haben.

 Im folgenden Verfahren wird beschrieben, wie schnell eine Ansicht verkleinert wird, ohne dass die Enden der Zoomleiste angepasst werden müssen.

### <a name="to-zoom-out"></a>So verkleinern Sie die Ansicht

1.  Klicken Sie mit der rechten Maustaste auf ein vergrößertes Diagramm.

2.  Wählen Sie im Kontextmenü **Horizontal verkleinern** aus.

     Die Ansicht wird verkleinert und enthält den gesamten Auslastungstestlauf.

## <a name="see-also"></a>Siehe auch

- [Analyze Load Test Results in the Graphs View (Analysieren von Auslastungstestergebnissen in der Diagrammansicht)](../test/analyze-load-test-results-in-the-graphs-view.md)
- [Analyze Load Test Results (Analysieren von Auslastungstestergebnissen)](../test/analyze-load-test-results-using-the-load-test-analyzer.md)
- [How to: Add and Delete Counters on Graphs (Vorgehensweise: Hinzufügen und Löschen von Indikatoren in Diagrammen)](../test/how-to-add-and-delete-counters-on-graphs-in-load-test-results.md)