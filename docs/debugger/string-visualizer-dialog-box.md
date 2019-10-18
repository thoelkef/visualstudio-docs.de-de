---
title: Dialogfeld ' Zeichen folgen Schnellansicht ' | Microsoft-Dokumentation
ms.date: 10/10/2018
ms.custom: seoapril2019
ms.topic: reference
f1_keywords:
- vs.debug.stringviewer
dev_langs:
- CSharp
- VB
- FSharp
- C++
- JavaScript
helpviewer_keywords:
- string visualizer
- visualizers, string
ms.assetid: 080fd8f1-72b0-461f-8451-3c84d5dc51df
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 10e7e50ffc0cb61bd036bef65c554e8147eecc09
ms.sourcegitcommit: 485ffaedb1ade71490f11cf05962add1718945cc
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/16/2019
ms.locfileid: "72430830"
---
# <a name="string-visualizer-dialog-box"></a>Dialogfeld „Zeichenfolgen-Schnellansicht“

Beim Debuggen in Visual Studio können Sie Zeichen folgen mit der integrierten Zeichen folgen Schnellansicht anzeigen. Die Zeichen folgen Schnellansicht zeigt Zeichen folgen an, die für einen datentip oder ein Debuggerfenster zu lang sind. Sie kann auch helfen, falsch formatierte Zeichen folgen zu identifizieren.

Die integrierte Zeichen folgen Schnellansicht enthält nur-Text-, XML-, HTML-und JSON-Optionen. Sie können auch integrierte schnell Ansichten für einige andere Typen, z. b. [DataSet-, Datentabelle-und DataView-](../debugger/dataset-visualizer-dialog-box.md) Objekte, **in den Fenstern** "Auto" oder "anderes Debuggen" öffnen.

> [!NOTE]
> Informationen zum Überprüfen von XAML-oder WPF-Benutzeroberflächen Elementen in einer Schnellansicht finden Sie unter oder unter [Suchen von XAML-Eigenschaften beim Debuggen](../xaml-tools/inspect-xaml-properties-while-debugging.md) oder [Verwenden der WPF](../debugger/how-to-use-the-wpf-tree-visualizer.md)-Struktur Schnellansicht.

Um die Zeichen folgen Schnellansicht zu öffnen, müssen Sie während des Debuggens angehalten werden. Zeigen Sie auf eine Variable, die einen nur-Text-, XML-, HTML-oder JSON-Zeichen folgen Wert hat, und wählen Sie das Lupensymbol ![visualizericon](../debugger/media/dbg-tips-visualizer-icon.png "Symbol "Schnellansicht"")aus.

## <a name="uielement-list"></a>UIElement-Liste

Feld **Ausdruck** zeigt die Variable oder den Ausdruck an, auf die Sie zeigen.

**Wertfeld** zeigt den Zeichen folgen Wert an. Ein leerer **Wert** bedeutet, dass die ausgewählte Schnellansicht die Zeichenfolge nicht erkennen kann. Die **XML** -Schnellansicht zeigt z. b. einen leeren **Wert** für eine Text Zeichenfolge ohne XML-Tags oder eine JSON-Zeichenfolge an. Um Zeichen folgen anzuzeigen, die von der ausgewählten Schnellansicht nicht erkannt werden können, wählen Sie stattdessen die **Text** Schnellansicht aus. Die **Text** Schnellansicht zeigt nur-Text an.

### <a name="json-string-data"></a>JSON-Zeichen folgen Daten

Eine wohlgeformte JSON-Zeichenfolge ähnelt der folgenden Abbildung in der JSON-Schnellansicht. Falsch formatierter JSON-Code zeigt möglicherweise ein Fehler Symbol an (oder, falls nicht erkannt). Um den JSON-Fehler zu identifizieren, kopieren Sie die Zeichenfolge, und fügen Sie Sie in ein JSON-linting-Tool wie [JSLint](https://www.jslint.com/)ein.

![JSON-Zeichen folgen Schnellansicht](../debugger/media/dbg-tips-string-visualizer-json.png "JSON-Zeichen folgen Schnellansicht")

### <a name="xml-string-data"></a>XML-Zeichen folgen Daten

Eine wohlgeformte XML-Zeichenfolge ähnelt der folgenden Abbildung in der XML-Schnellansicht. Falsch formatierte XML-Daten können ohne die XML-Tags angezeigt werden, oder wenn Sie nicht erkannt werden.

![XML-Zeichen folgen Schnellansicht](../debugger/media/dbg-string-visualizers-xml.png "XML-Zeichen folgen Schnellansicht")

### <a name="html-string-data"></a>HTML-Zeichen folgen Daten

Eine wohlgeformte HTML-Zeichenfolge wird angezeigt, wenn Sie in einem Browser gerendert wird, wie in der folgenden Abbildung dargestellt. Falsch formatierter HTML-Code kann als Klartext angezeigt werden.

![HTML-Zeichen folgen Schnellansicht](../debugger/media/dbg-string-visualizers-html.png "HTML-Zeichen folgen Schnellansicht")

## <a name="see-also"></a>Siehe auch

- [Erstellen von benutzerdefinierten VisualisierungenC#(, Visual Basic)](../debugger/create-custom-visualizers-of-data.md)
- [Datenvisualisierungen in Visual Studio für Mac](/visualstudio/mac/data-visualizations)