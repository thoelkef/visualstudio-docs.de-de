---
title: Zeichenfolgen in einen Zeichenfolgen-Schnellansicht anzeigen | Microsoft-Dokumentation
ms.date: 04/08/2019
ms.topic: conceptual
dev_langs:
- CSharp
- VB
- FSharp
- C++
- JavaScript
helpviewer_keywords:
- string visualizer
- visualizers, string
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: ffd19dccb69d3ae05a84ae49a280ff49c14f2809
ms.sourcegitcommit: 53aa5a413717a1b62ca56a5983b6a50f7f0663b3
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/18/2019
ms.locfileid: "59367308"
---
# <a name="view-strings-in-a-string-visualizer-in-visual-studio"></a>Anzeigen von Zeichenfolgen in einen Zeichenfolgen-Schnellansicht in Visual Studio

Während des Debuggens in Visual Studio können Sie Zeichenfolgen mit der integrierten Zeichenfolgen-Schnellansicht anzeigen. Die Zeichenfolgen-Schnellansicht zeigt Zeichenfolgen, die für ein Trinkgeld- oder -Debugger-Fenster von Daten zu lang sind. Sie können auch Sie falsch formatierte Zeichenfolgen zu identifizieren.

Die integrierte String-Schnellansicht enthält nur-Text, XML, HTML und JSON-Optionen. Sie können auch integrierte Schnellansichten für einigen andere Typen wie z. B. Öffnen [DataSet-, DataTable- und DataView](../debugger/dataset-visualizer-dialog-box.md) Objekte, aus der **"Auto"** oder anderen Debuggerfenster.

> [!NOTE]
> Wenn Sie XAML oder WPF-UI-Elemente in einer Schnellansicht überprüfen müssen, finden Sie unter oder [Überprüfen von XAML-Eigenschaften während des Debuggens](../debugger/inspect-xaml-properties-while-debugging.md) oder [Gewusst wie: Verwenden Sie die WPF-Strukturschnellansicht](../debugger/how-to-use-the-wpf-tree-visualizer.md).

## <a name="open-a-string-visualizer"></a>Öffnen Sie eine Zeichenfolgen-Schnellansicht

Um die Zeichenfolgen-Schnellansicht zu öffnen, müssen Sie während des Debuggens angehalten werden. Zeigen Sie auf eine Variable mit einem nur-Text, XML, HTML oder JSON-string-Wert, und wählen das Lupensymbol ![VisualizerIcon](../debugger/media/dbg-tips-visualizer-icon.png "Schnellansicht Symbol").

![Öffnen Sie eine Zeichenfolgen-Schnellansicht](../debugger/media/dbg-tips-string-visualizers.png "öffnen Zeichenfolgen-Schnellansicht")

## <a name="view-string-visualizer-data"></a>Ansichtsdaten für Zeichenfolge-Schnellansicht

Im Schnellansichtsfenster Zeichenfolge die **Ausdruck** Feld zeigt, Variable oder einen Ausdruck, Sie sind mit der Maus, und die **Wert** Feld zeigt den Zeichenfolgenwert.

Ein leerer **Wert** bedeutet, dass die ausgewählte Schnellansicht die Zeichenfolge nicht erkennen kann. Z. B. die **XML-Visualizer** zeigt eine leere **Wert** für eine Textzeichenfolge mit keine XML-Tags oder einer JSON-Zeichenfolge.

Um Zeichenfolgen anzuzeigen, die die ausgewählte Schnellansicht nicht erkennen kann, wählen die **Text-Schnellansicht**. Die **Text-Schnellansicht** zeigt nur-Text.

### <a name="view-json-string-data"></a>JSON-Zeichenfolge-Daten anzeigen

Eine wohlgeformte JSON-Zeichenfolge wird ähnlich der folgenden Abbildung in der JSON-Schnellansicht angezeigt. Falsch formatiertes JSON möglicherweise ein Fehlersymbol (oder leer, wenn nicht erkannte) angezeigt. Um die JSON-Fehler zu identifizieren, kopieren Sie die Zeichenfolge in ein JSON-Linting-Tool wie z. B. [JSLint](https://www.jslint.com/).

![JSON-Zeichenfolgen-Schnellansicht](../debugger/media/dbg-tips-string-visualizer-json.png "JSON-Zeichenfolgen-Schnellansicht")

### <a name="view-xml-string-data"></a>XML-Zeichenfolge-Daten anzeigen

Eine wohlgeformte XML-Zeichenfolge wird ähnlich der folgenden Abbildung in der XML-Schnellansicht angezeigt. Falsch formatierte XML möglicherweise ohne die XML-Tags, oder ist leer angezeigt, wenn nicht erkannte.

![XML-Zeichenfolgen-Schnellansicht](../debugger/media/dbg-string-visualizers-xml.png "XML-Zeichenfolgen-Schnellansicht")

### <a name="view-html-string-data"></a>Zeichenfolgendaten HTML anzeigen

Eine gut formatierte HTML-Zeichenfolge angezeigt wird, als ob in einem Browser gerendert wird, wie in der folgenden Abbildung dargestellt. Fehlerhaftes HTML möglicherweise als nur-Text angezeigt.

![HTML-Zeichenfolgen-Schnellansicht](../debugger/media/dbg-string-visualizers-html.png "HTML-Zeichenfolgen-Schnellansicht")

## <a name="see-also"></a>Siehe auch

- [Erstellen Sie benutzerdefinierter Schnellansichten (c#, Visual Basic)](../debugger/create-custom-visualizers-of-data.md)
- [Datenvisualisierungen in Visual Studio für Mac](/visualstudio/mac/data-visualizations)