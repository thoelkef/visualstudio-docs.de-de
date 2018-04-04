---
title: Analysieren von Verletzungen der Schwellenwertregeln in Auslastungstests in Visual Studio | Microsoft-Dokumentation
ms.date: 10/19/2016
ms.topic: article
f1_keywords:
- vs.test.load.monitor.threshholdresult
helpviewer_keywords:
- load tests, thresholds
- threshold violations
- threshold counts
- load tests, threshold violations
- load test results, analyzing threshold violations
- thresholds in load tests
ms.assetid: 969ed346-cf2e-4d48-82b3-edb3e075e1c0
author: gewarren
ms.author: gewarren
manager: ghogen
ms.technology: vs-ide-test
ms.openlocfilehash: 761d277612242cc4b14b0a24d1a2ac7663b2b152
ms.sourcegitcommit: 900ed1e299cd5bba56249cef8f5cf3981b10cb1c
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 03/19/2018
---
# <a name="analyzing-threshold-rule-violations-in-load-tests-using-the-load-test-analyzer"></a>Analyzing Threshold Rule Violations in Load Tests Using the Load Test Analyzer

Schwellenwertregeln sind bestimmten Leistungsindikatoren zugeordnet. Verletzungen weisen darauf hin, dass ein Leistungsindikator einen festgelegten Wert über- oder unterschritten hat. Wenn Sie einen Auslastungstest ausführen, können auftretende Verletzungen der zuvor festgelegten Schwellenwertregeln analysiert werden.

Wenn Verletzungen aufgetreten sind, wird ein **Schwellenwertverletzungen**-Link in der Statusleiste des Auslastungstest-Analyzers angezeigt und die Anzahl der aufgetretenen Verletzungen wird angegeben. Klicken Sie auf den Link, um die Schwellenwertverletzungs-Tabelle anzuzeigen. Die Schwellenwertverletzungen können auch im Fenster **Indikatoren** und im Diagramm angezeigt werden.

## <a name="view-threshold-violations-in-the-table"></a>Anzeigen von Schwellenwertverletzungen in der Tabelle

 In der Schwellenwertverletzungs-Tabelle werden die ersten 1.000 Verletzungen angezeigt. Die Tabelle enthält folgende Spalten:

|Spalte|description|In der Standardeinstellung angezeigt|
|------------|-----------------|------------------------|
|zeit|Der Zeitpunkt während des Auslastungstests, an dem die Verletzung auftrat|Ja|
|Computer|Der Name des getesteten Computers, auf dem die Verletzung auftrat **Hinweis**: Dies ist wichtig, wenn Sie Auslastungstests auf Rigs ausführen.|Ja|
|Kategorie|Die Kategorie des Leistungsindikators, dessen Schwellenwert verletzt wurde|Ja|
|Zähler|Der Name des Leistungsindikators, dessen Schwellenwert verletzt wurde|Ja|
|Instanz|Die Instanz des Leistungsindikators, dessen Schwellenwert verletzt wurde|Ja|
|Meldung|Eine Meldung mit einer Beschreibung der Schwellenwertverletzung Beispiel: **Der Wert 5 überschreitet den kritischen Schwellenwert 0**.|Ja|

> [!NOTE]
> Sie können die Tabelle sortieren, indem Sie die Spaltenüberschriften auswählen.

 Weitere Informationen finden Sie unter [Analyze Load Test Results and Errors in the Tables View (Analysieren von Auslastungstestergebnissen und -fehlern in der Tabellenansicht)](../test/analyze-load-test-results-and-errors-in-the-tables-view.md).

## <a name="view-threshold-violations-in-the-counters-panel"></a>Anzeigen von Schwellenwertverletzungen im Indikatorenfenster

 Schwellenwertverletzungen können im **Indikatorenfenster** in der Struktur angezeigt werden, in der die Leistungsindikatoren für den Auslastungstest aufgeführt sind. Schwellenwertverletzungen werden im **Indikatorenfenster** durch Symbole dargestellt. Folgende Symbole werden verwendet:

 Folgende Symbole werden verwendet:

 ![Keine Schwellenwertverletzungen](../test/media/icon_ltest_1.gif "Icon_LTest_1") Keine Schwellenwertverletzungen

 ![Eine kritische Schwellenwertverletzung im letzten Intervall](../test/media/icon_ltest_2.gif "Icon_LTest_2") Eine kritische Schwellenwertverletzung im letzten Intervall

 ![Eine kritische Schwellenwertverletzung im vorherigen Intervall](../test/media/icon_ltest_3.gif "Icon_LTest_3") Eine kritische Schwellenwertverletzung im vorherigen Intervall

 ![Eine Warnschwellenwertverletzung im letzten Intervall](../test/media/icon_ltest_4.gif "Icon_LTest_4") Eine Warnschwellenwertverletzung im letzten Intervall

 ![Eine Warnschwellenwertverletzung im vorherigen Intervall](../test/media/icon_ltest_5.gif "Icon_LTest_5") Eine Warnschwellenwertverletzung im vorherigen Intervall

 Optional können Schwellenwertverletzungen auch im Diagramm angezeigt werden. Das Schwellenwertsymbol wird im Diagramm neben dem Datenpunkt angezeigt, bei dem die Schwellenwertverletzung aufgetreten ist.

 In der Indikatorstruktur werden Symbole für Schwellenwertverletzungen von den einzelnen Indikatorknoten auf den Stammknoten übertragen. So werden Sie auf Verletzungen von Indikatoren hingewiesen, die möglicherweise nicht in der Struktur sichtbar sind, wenn diese nicht erweitert wurde.

 Weitere Informationen finden Sie unter [Using the Counters Panel in Graphs View and Tables View (Verwenden des Indikatorenfensters in der Diagrammansicht und Tabellenansicht)](../test/counters-panel-in-load-test-analyzer.md).

## <a name="view-threshold-violations-on-the-graph"></a>Anzeigen von Schwellenwertverletzungen im Diagramm

 Schwellenwertverletzungen können im Diagramm angezeigt werden. Wie im **Indikatorenfenster** werden Schwellenwertverletzungen im Diagramm durch Symbole dargestellt. Die Symbole werden im Diagramm neben den Datenpunkten angezeigt, an denen die Schwellenwertverletzung auftrat. Wenn eine Schwellenwertverletzung für einen Indikator auftritt, der nicht im Diagramm angezeigt wird, können Sie den Indikator dem Diagramm hinzufügen, indem Sie ihn aus dem **Indikatorenfenster** in das Diagramm ziehen.

 Weitere Informationen finden Sie unter [Analyze Load Test Results in the Graphs View (Analysieren von Auslastungstestergebnissen in der Diagrammansicht)](../test/analyze-load-test-results-in-the-graphs-view.md).

## <a name="see-also"></a>Siehe auch

- [Festlegen von Indikatorensätzen und Schwellenwertregeln für Computer in einem Auslastungstest](../test/specify-counter-sets-and-threshold-rules-for-load-testing.md)
- [Analyze Load Test Results (Analysieren von Auslastungstestergebnissen)](../test/analyze-load-test-results-using-the-load-test-analyzer.md)
- [Analyze Load Test Results and Errors in the Tables View (Analysieren von Auslastungstestergebnissen und -fehlern in der Tabellenansicht)](../test/analyze-load-test-results-and-errors-in-the-tables-view.md)