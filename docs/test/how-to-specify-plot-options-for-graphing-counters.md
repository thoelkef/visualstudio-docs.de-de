---
title: Plotoptionen zur grafischen Darstellung von Indikatoren für Auslastungstests in Visual Studio
ms.date: 10/19/2016
ms.topic: conceptual
helpviewer_keywords:
- load tests, graphing counters
ms.assetid: 1969c20b-e0eb-48f6-a49f-a9090cd86008
author: gewarren
ms.author: gewarren
manager: douge
ms.prod: visual-studio-dev15
ms.technology: vs-ide-test
ms.openlocfilehash: 7a5f87a83b8c743ae869a700618051e07c8c2e75
ms.sourcegitcommit: 58052c29fc61c9a1ca55a64a63a7fdcde34668a4
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 06/04/2018
ms.locfileid: "34750921"
---
# <a name="how-to-specify-plot-options-for-graphing-counters"></a>Gewusst wie: Angeben von Zeichnungsoptionen zur grafischen Darstellung von Indikatoren

Im Dialogfeld **Zeichnungsoptionen** können Sie die Farbe und die Linienart eines gezeichneten Indikators im Diagramm ändern. Sie können auch den Bereich auf einen bestimmten Wert festlegen oder den Bereich angeben, der auf Grundlage der erfassten Daten automatisch eingestellt werden soll.

![Dialogfeld "Zeichnungsoptionen"](../test/media/ltest_plotoptions.png)

## <a name="to-specify-plotting-options-for-graphs"></a>So geben Sie Zeichnungsoptionen für Diagramme an

1.  Wählen Sie in der Auslastungstest-Analyzer auf der Auslastungstest-Symbolleiste die Option **Diagramme**.

     Dadurch werden Auslastungstestergebnisse in der Diagrammansicht angezeigt.

2.  Klicken Sie in der Legende oder im Diagramm mit der rechten Maustaste auf die Zeile oder die aktuelle Zeichnungslinie des Leistungsindikators, dessen Zeichnungsoption Sie ändern möchten, und wählen Sie dann **Zeichnungsoptionen** aus.

     Das Dialogfeld **Zeichnungsoptionen** wird angezeigt.

3.  Wählen Sie mithilfe der Dropdownliste **Farbe** die Farbe aus, die Sie zum Zeichnen des Leistungsindikators verwenden möchten.

4.  Wählen Sie mithilfe der Dropdownliste **Stil** den Stil aus, den Sie zum Zeichnen des Leistungsindikators verwenden möchten.

5.  Führen Sie einen der folgenden Schritte aus:

     **Bereich automatisch anpassen** (Standardeinstellung) aktivieren

     \- oder –

     Deaktivieren Sie **Bereich automatisch anpassen**, und geben Sie mithilfe der Dropdownliste **Bereich** den Bereich an, den Sie zum Zeichnen des Leistungsindikators verwenden möchten.

6.  Klicken Sie auf **OK**.

     Der Leistungsindikator, dessen Optionen Sie geändert haben, wird im Diagramm mit den von Ihnen angegebenen Änderungen angezeigt.

## <a name="see-also"></a>Siehe auch

- [Analyze Load Test Results in the Graphs View (Analysieren von Auslastungstestergebnissen in der Diagrammansicht)](../test/analyze-load-test-results-in-the-graphs-view.md)
- [Vorgehensweise: Erstellen von benutzerdefinierten Diagrammen](../test/how-to-create-custom-graphs-in-load-test-results.md)
- [Analyze Load Test Results in the Graphs View (Analysieren von Auslastungstestergebnissen in der Diagrammansicht)](../test/analyze-load-test-results-in-the-graphs-view.md)