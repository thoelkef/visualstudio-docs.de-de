---
title: Analysieren von Auslastungstestfehlern mit dem Indikatorenfenster in Visual Studio
ms.date: 10/19/2016
ms.topic: conceptual
helpviewer_keywords:
- Load Test Analyzer, counters panel
ms.assetid: 981b4f1e-505a-4078-a06d-58ae17d996b4
author: gewarren
ms.author: gewarren
manager: douge
ms.prod: visual-studio-dev15
ms.technology: vs-ide-test
ms.openlocfilehash: e37b39d504059491318913f6eb1345d73ef3074b
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/26/2018
---
# <a name="how-to-analyze-errors-using-the-counters-panel"></a>How to: Analyze Errors Using the Counters Panel

Das Indikatorenfenster wird in der Diagrammansicht und die Tabellenansicht im Auslastungstest-Analyzer angezeigt, während ein Auslastungstest ausgeführt wird, oder wenn Sie ein Auslastungstestergebnis analysieren. Weitere Informationen finden Sie unter [Analyze Load Test Results in the Graphs View (Analysieren von Auslastungstestergebnissen in der Diagrammansicht)](../test/analyze-load-test-results-in-the-graphs-view.md), [Analyze Load Test Results and Errors in the Tables View (Analysieren von Auslastungstestergebnissen und -fehlern in der Tabellenansicht)](../test/analyze-load-test-results-and-errors-in-the-tables-view.md) und [How to: Access Load Test Results for Analysis (Vorgehensweise: Zugreifen auf Auslastungstestergebnisse für die Analyse)](../test/how-to-access-load-test-results-for-analysis.md).

 Der Knoten **Fehler** im Indikatorenfenster enthält alle Fehler, die während des Auslastungstests erkannt wurden. Der Knoten "Fehler" enthält mehrere spezifische Unterkategorie-Fehlerknoten für andere Arten von Fehlern, z.B. **Ausnahmen** und **HTTP-Fehler**.

 ![Fehlerknoten des Indikatorenfensters](../test/media/ltest_errornode.png "LTest_ErrorNode")

## <a name="to-analyze-errors-in-the-counters-panel"></a>So analysieren Sie Fehler im Indikatorenfenster

1.  Wählen Sie nach Abschluss eines Auslastungstests oder nach dem Laden eines Testergebnisses auf der Symbolleiste des Auslastungstest-Analyzers entweder **Diagramme** oder **Tabellen** aus.

     Im Fenster **Indikatoren** wird entweder die Diagrammansicht oder die Tabellenansicht verwendet.

2.  Falls das Indikatorenfenster nicht angezeigt wird, klicken Sie auf der Symbolleiste auf **Indikatorenfenster anzeigen**.

3.  Erweitern Sie den Knoten **Fehler**, und wählen Sie die zu analysierende Fehlerkategorie oder Fehlerunterkategorie aus.

4.  Klicken Sie mit der rechten Maustaste auf den Fehler, und wählen Sie eine der folgenden Optionen aus:

    -   **Indikator im Diagramm anzeigen**: Der Fehler wird der Diagrammansicht hinzugefügt und im ausgewählten Diagramm hervorgehoben. Weitere Informationen finden Sie unter [How to: Add and Delete Counters on Graphs (Vorgehensweise: Hinzufügen und Löschen von Indikatoren in Diagrammen)](../test/how-to-add-and-delete-counters-on-graphs-in-load-test-results.md).

    -   **Indikator in Legende anzeigen**: Der Fehler wird der Legende hinzugefügt und hervorgehoben. Weitere Informationen finden Sie unter [Using the Graphs View Legend to Analyze Load Tests (Verwenden der Legende der Diagrammansicht zum Analysieren von Auslastungstests)](../test/use-the-graphs-view-legend-to-analyze-load-tests.md).

    -   **Diagramm hinzufügen**:

    1.  Das Dialogfeld **Diagrammnamen eingeben** wird angezeigt.

    2.  Geben Sie im Textfeld **Diagrammname** den Namen des neuen Diagramms ein, und klicken Sie anschließend auf **OK**.

    3.  Optional: Klicken Sie erneut mit der rechten Maustaste auf den Fehler, und klicken Sie auf **Indikator im Diagramm anzeigen**.

         Weitere Informationen finden Sie unter [How to: Create Custom Graphs (Vorgehensweise: Erstellen benutzerdefinierter Diagramme)](../test/how-to-create-custom-graphs-in-load-test-results.md).

5.  (Optional) Wenn Sie einen Fehler im Ergebnis eines abgeschlossenen Auslastungstests analysieren, können Sie beim Anzeigen der Diagramme die Zoomfunktionen verwenden. Weitere Informationen finden Sie unter [Vorgehensweise: Vergrößern eines Diagrammbereichs](../test/how-to-zoom-in-on-a-region-of-the-graph-in-load-test-results.md).

    > [!TIP]
    > Wenn während des Auslastungstestlaufs Fehler erkannt wurden, wird ein Fehlerlink mit der Anzahl gefundener Fehler auf der Statusleiste des Auslastungstest-Analyzers angezeigt. Sie können auf den Link klicken, um alle Fehler in der Tabelle **Fehler** der Tabellenansicht anzuzeigen.

## <a name="see-also"></a>Siehe auch

- [Verwenden des Indikatorbereichs in der Diagrammansicht und Tabellenansicht](../test/counters-panel-in-load-test-analyzer.md)
- [Analyze Load Test Results (Analysieren von Auslastungstestergebnissen)](../test/analyze-load-test-results-using-the-load-test-analyzer.md)