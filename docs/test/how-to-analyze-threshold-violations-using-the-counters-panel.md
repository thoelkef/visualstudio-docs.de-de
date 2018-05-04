---
title: Schwellenwertverletzungen in Auslastungstests in Visual Studio
ms.date: 10/19/2016
ms.topic: conceptual
helpviewer_keywords:
- load tests, threshold violations
ms.assetid: 0126d7b7-0538-4ea9-9046-6556654b3b9d
author: gewarren
ms.author: gewarren
manager: douge
ms.prod: visual-studio-dev15
ms.technology: vs-ide-test
ms.openlocfilehash: 483a591e190efa557ffff42c958c18171269e7ea
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/26/2018
---
# <a name="how-to-analyze-threshold-violations-using-the-counters-panel-in-load-test-analyzer"></a>Gewusst wie: Analysieren von Schwellenwertverletzungen mit dem Indikatorbereich im Auslastungstest-Analyzer

Das Indikatorenfenster wird in der Diagrammansicht und die Tabellenansicht im Auslastungstest-Analyzer angezeigt, während ein Auslastungstest ausgeführt wird, oder wenn Sie ein Auslastungstestergebnis analysieren. Weitere Informationen finden Sie unter [Analyze Load Test Results in the Graphs View (Analysieren von Auslastungstestergebnissen in der Diagrammansicht)](../test/analyze-load-test-results-in-the-graphs-view.md), [Analyze Load Test Results and Errors in the Tables View (Analysieren von Auslastungstestergebnissen und -fehlern in der Tabellenansicht)](../test/analyze-load-test-results-and-errors-in-the-tables-view.md) und [How to: Access Load Test Results for Analysis (Vorgehensweise: Zugreifen auf Auslastungstestergebnisse für die Analyse)](../test/how-to-access-load-test-results-for-analysis.md).

 Schwellenwertverletzungen sind bestimmten Leistungsindikatoren zugeordnet und weisen darauf hin, dass der Leistungsindikator einen festgelegten Schwellenwert über- oder unterschritten hat. Schwellenwertverletzungen werden im Indikatorenfenster durch Symbole dargestellt.

 ![Knoten „Computer“ des Indikatorenfensters](../test/media/ltest_compnode.png "LTest_CompNode")

 Das Symbol für eine Schwellenwertverletzung wird vom Strukturknoten, in dem sich der fehlerhafte Indikator befindet, zur Stammebene verteilt. Das Symbol weist den Benutzer auf Verletzungen von Indikatoren hin, die möglicherweise nicht in der Struktur sichtbar sind, wenn diese nicht erweitert wurde. Ein Beispiel für das Symbol ist in der vorherigen Abbildung im Indikatorenfenster im Knoten **Computer** dargestellt.

 Folgende Symbole werden verwendet:

 ![Keine Schwellenwertverletzungen](../test/media/icon_ltest_1.gif "Icon_LTest_1") Keine Schwellenwertverletzungen

 ![Eine kritische Schwellenwertverletzung im letzten Intervall](../test/media/icon_ltest_2.gif "Icon_LTest_2") Eine kritische Schwellenwertverletzung im letzten Intervall

 ![Eine kritische Schwellenwertverletzung im vorherigen Intervall](../test/media/icon_ltest_3.gif "Icon_LTest_3") Eine kritische Schwellenwertverletzung im vorherigen Intervall

 ![Eine Warnschwellenwertverletzung im letzten Intervall](../test/media/icon_ltest_4.gif "Icon_LTest_4") Eine Warnschwellenwertverletzung im letzten Intervall

 ![Eine Warnschwellenwertverletzung im vorherigen Intervall](../test/media/icon_ltest_5.gif "Icon_LTest_5") Eine Warnschwellenwertverletzung im vorherigen Intervall

## <a name="to-analyze-threshold-violations-in-the-counters-panel"></a>So analysieren Sie Schwellenwertverletzungen im Indikatorenfenster

1.  Wählen Sie nach Abschluss eines Auslastungstests oder nach dem Laden eines Testergebnisses auf der Symbolleiste des Auslastungstest-Analyzers entweder **Diagramme** oder **Tabellen** aus.

     Im Indikatorenfenster wird entweder die Diagrammansicht oder die Tabellenansicht angezeigt.

2.  Falls das Indikatorenfenster nicht angezeigt wird, klicken Sie auf der Symbolleiste auf **Indikatorenfenster anzeigen**.

     Alle Knoten, die Schwellenwertverletzungen enthalten, schließen eines der oben aufgeführten Symbole ein.

3.  Erweitern Sie den Knoten, der ein Schwellenwertsymbol enthält, z.B. den Knoten **Computer**, wie in der vorherigen Abbildung „Knoten ‚Computer‘ im Indikatorenfenster mit Schwellenwertverletzung“ dargestellt wird. Erweitern Sie den Knoten weiterhin, bis Sie den Leistungsindikator mit der Schwellenwertverletzung erreichen. Die vorhergehende Abbildung zeigt dies beispielsweise für die fehlerhafte Instanz von **Microsoft Virtual Machine Failed Bus Network Adapter** (Netzwerkkarte für Microsoft Virtual Machine-Bus).

4.  (Optional) klicken Sie mit der rechten Maustaste auf den Leistungsindikator mit der Schwellenwertverletzung, und wählen Sie eine der folgenden Optionen aus:

    -   **Indikator im Diagramm anzeigen**: In der Diagrammansicht wird der Leistungsindikator hinzugefügt und im ausgewählten Diagramm hervorgehoben. Weitere Informationen finden Sie unter [How to: Add and Delete Counters on Graphs (Vorgehensweise: Hinzufügen und Löschen von Indikatoren in Diagrammen)](../test/how-to-add-and-delete-counters-on-graphs-in-load-test-results.md).

        > [!NOTE]
        > Symbole für Schwellenwertverletzungen können auch im Diagramm in der Diagrammansicht angezeigt werden. Das Schwellenwertsymbol wird im Diagramm neben dem Datenpunkt angezeigt, bei dem die Schwellenwertverletzung aufgetreten ist. Klicken Sie hierzu auf die Dropdownschaltfläche **Legende anzeigen**, und wählen Sie dann **Schwellenwertverletzungen im Diagramm anzeigen** aus.

    -   **Indikator in Legende anzeigen**: In der Legende wird der Leistungsindikator hinzugefügt und ausgewählt. Weitere Informationen finden Sie unter [Using the Graphs View Legend to Analyze Load Tests (Verwenden der Legende der Diagrammansicht zum Analysieren von Auslastungstests)](../test/use-the-graphs-view-legend-to-analyze-load-tests.md).

    -   **Diagramm hinzufügen**:

    1.  Das Dialogfeld **Diagrammnamen eingeben** wird angezeigt.

    2.  Geben Sie im Textfeld **Diagrammname** einen Namen für das neue Diagramm ein, und klicken Sie anschließend auf **OK**.

    3.  (Optional) Klicken Sie mit der rechten Maustaste erneut auf den Leistungsindikator, und wählen Sie **Indikator im Diagramm anzeigen** aus.

         Weitere Informationen finden Sie unter [How to: Create Custom Graphs (Vorgehensweise: Erstellen benutzerdefinierter Diagramme)](../test/how-to-create-custom-graphs-in-load-test-results.md).

5.  (Optional) Wenn Sie die Schwellenwertverletzung in einem abgeschlossenen Auslastungstestergebnis analysieren, können Sie die Zoomfunktionen in der Diagrammansicht verwenden. Weitere Informationen finden Sie unter [Vorgehensweise: Vergrößern eines Diagrammbereichs](../test/how-to-zoom-in-on-a-region-of-the-graph-in-load-test-results.md).

    > [!TIP]
    > Wurden während des Auslastungstests Schwellenwertverletzungen ermittelt, wird auf der Statusleiste des Auslastungstest-Analyzers der Link "Schwellenwertverletzungen" einschließlich der Anzahl der Verletzungen angezeigt. Sie können auf den Link klicken, um alle Schwellenwertverletzungen in der Tabelle **Schwellenwerte** der Tabellenansicht anzuzeigen.

## <a name="see-also"></a>Siehe auch

- [Verwenden des Indikatorbereichs in der Diagrammansicht und Tabellenansicht](../test/counters-panel-in-load-test-analyzer.md)
- [Analyze Load Test Results (Analysieren von Auslastungstestergebnissen)](../test/analyze-load-test-results-using-the-load-test-analyzer.md)