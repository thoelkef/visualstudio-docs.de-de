---
title: Anzeigen von Zeichen folgen in einer Zeichen folgen Schnellansicht | Microsoft-Dokumentation
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
ms.openlocfilehash: 33e1cbd4b1c754498d7e2bd6c354e874ae8cdad5
ms.sourcegitcommit: 485ffaedb1ade71490f11cf05962add1718945cc
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/16/2019
ms.locfileid: "72450397"
---
# <a name="view-strings-in-a-string-visualizer-in-visual-studio"></a>Anzeigen von Zeichen folgen in einer Zeichen folgen Schnellansicht in Visual Studio

Beim Debuggen in Visual Studio können Sie Zeichen folgen mit der integrierten Zeichen folgen Schnellansicht anzeigen. Die Zeichen folgen Schnellansicht zeigt Zeichen folgen an, die für einen datentip oder ein Debuggerfenster zu lang sind. Sie kann auch helfen, falsch formatierte Zeichen folgen zu identifizieren.

Die integrierte Zeichen folgen Schnellansicht enthält nur-Text-, XML-, HTML-und JSON-Optionen. Sie können auch integrierte schnell Ansichten für einige andere Typen, z. b. [DataSet-, Datentabelle-und DataView-](../debugger/dataset-visualizer-dialog-box.md) Objekte, **in den Fenstern** "Auto" oder "anderes Debuggen" öffnen.

> [!NOTE]
> Informationen zum Überprüfen von XAML-oder WPF-Benutzeroberflächen Elementen in einer Schnellansicht finden Sie unter oder unter [Suchen von XAML-Eigenschaften beim Debuggen](../xaml-tools/inspect-xaml-properties-while-debugging.md) oder [Verwenden der WPF](../debugger/how-to-use-the-wpf-tree-visualizer.md)-Struktur Schnellansicht.

## <a name="open-a-string-visualizer"></a>Öffnen einer Zeichen folgen Schnellansicht

Um die Zeichen folgen Schnellansicht zu öffnen, müssen Sie während des Debuggens angehalten werden. Zeigen Sie auf eine Variable, die einen nur-Text-, XML-, HTML-oder JSON-Zeichen folgen Wert hat, und wählen Sie das Lupensymbol ![visualizericon](../debugger/media/dbg-tips-visualizer-icon.png "Symbol "Schnellansicht"")aus.

![Öffnen einer Zeichen folgen Schnellansicht](../debugger/media/dbg-tips-string-visualizers.png "Öffnen der Zeichen folgen Schnellansicht")

## <a name="view-string-visualizer-data"></a>Anzeigen von Zeichen folgen-Visualisierungs Daten

Im Fenster "Zeichen folgen Schnellansicht" zeigt das **Ausdrucks** Feld die Variable oder den Ausdruck an, auf die Sie zeigen, und das Feld " **Wert** " zeigt den Zeichen folgen Wert an.

Ein leerer **Wert** bedeutet, dass die ausgewählte Schnellansicht die Zeichenfolge nicht erkennen kann. Die **XML** -Schnellansicht zeigt z. b. einen leeren **Wert** für eine Text Zeichenfolge ohne XML-Tags oder eine JSON-Zeichenfolge an.

Um Zeichen folgen anzuzeigen, die von der ausgewählten Schnellansicht nicht erkannt werden können, wählen Sie die **Text**Schnellansicht aus. Die **Text** Schnellansicht zeigt nur-Text an.

### <a name="view-json-string-data"></a>Anzeigen von JSON-Zeichen folgen Daten

Eine wohlgeformte JSON-Zeichenfolge ähnelt der folgenden Abbildung in der JSON-Schnellansicht. Falsch formatierter JSON-Code zeigt möglicherweise ein Fehler Symbol an (oder, falls nicht erkannt). Um den JSON-Fehler zu identifizieren, kopieren Sie die Zeichenfolge, und fügen Sie Sie in ein JSON-linting-Tool wie [JSLint](https://www.jslint.com/)ein.

![JSON-Zeichen folgen Schnellansicht](../debugger/media/dbg-tips-string-visualizer-json.png "JSON-Zeichen folgen Schnellansicht")

### <a name="view-xml-string-data"></a>Anzeigen von XML-Zeichen folgen Daten

Eine wohlgeformte XML-Zeichenfolge ähnelt der folgenden Abbildung in der XML-Schnellansicht. Falsch formatierte XML-Daten können ohne die XML-Tags angezeigt werden, oder wenn Sie nicht erkannt werden.

![XML-Zeichen folgen Schnellansicht](../debugger/media/dbg-string-visualizers-xml.png "XML-Zeichen folgen Schnellansicht")

### <a name="view-html-string-data"></a>Anzeigen von HTML-Zeichen folgen Daten

Eine wohlgeformte HTML-Zeichenfolge wird angezeigt, wenn Sie in einem Browser gerendert wird, wie in der folgenden Abbildung dargestellt. Falsch formatierter HTML-Code kann als Klartext angezeigt werden.

![HTML-Zeichen folgen Schnellansicht](../debugger/media/dbg-string-visualizers-html.png "HTML-Zeichen folgen Schnellansicht")

## <a name="see-also"></a>Siehe auch

- [Erstellen von benutzerdefinierten VisualisierungenC#(, Visual Basic)](../debugger/create-custom-visualizers-of-data.md)
- [Datenvisualisierungen in Visual Studio für Mac](/visualstudio/mac/data-visualizations)