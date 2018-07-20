---
title: Zeichenfolgen in einen Zeichenfolgen-Schnellansicht anzeigen | Microsoft-Dokumentation
ms.custom: ''
ms.date: 07/11/2017
ms.technology: vs-ide-debug
ms.topic: reference
f1_keywords:
- vs.debug.stringviewer
dev_langs:
- CSharp
- VB
- FSharp
- C++
- JScript
- SQL
helpviewer_keywords:
- string visualizer
- visualizers, string
ms.assetid: 080fd8f1-72b0-461f-8451-3c84d5dc51df
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: ca6e4519a85659b36e5cf6baebaadd1d1c626f1a
ms.sourcegitcommit: 0e5289414d90a314ca0d560c0c3fe9c88cb2217c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/19/2018
ms.locfileid: "39151033"
---
# <a name="view-strings-in-a-string-visualizer-in-visual-studio"></a>Anzeigen von Zeichenfolgen in einen Zeichenfolgen-Schnellansicht in Visual Studio
Während Sie Debuggen, können Sie eine Zeichenfolgen-Schnellansicht anzeigen Zeichenfolgen öffnen, die in einem Datenfenster Trinkgeld- oder -Debugger anzeigen zu lang sind. In vielen Fällen können die Schnellansicht falsch formatierte Zeichenfolgen zu identifizieren.

Die Schnellansichten für integrierte Standardzeichenfolge umfassen nur-Text, XML, HTML und JSON. Einigen andere Typen wie WPF-Objekte, die im Debugger angezeigt werden, wie Windows die **"Auto"** Fenster können Sie auch Schnellansichten öffnen.

## <a name="open-a-string-visualizer"></a>Öffnen Sie eine Zeichenfolgen-Schnellansicht

Klicken Sie zum Anzeigen einer nur-Text, XML, HTML oder JSON-Zeichenfolge auf das Lupensymbol ![VisualizerIcon](../debugger/media/dbg-tips-visualizer-icon.png "Schnellansicht Symbol") beim Zeigen auf eine Variable, die einen Zeichenfolgenwert enthält. Sie müssen im Debugger, um das Lupensymbol finden Sie unter angehalten werden.

![Öffnen Sie eine Zeichenfolgen-Schnellansicht](../debugger/media/dbg-tips-string-visualizers.png "OpenStringVisualizer")

## <a name="view-string-data"></a>Anzeigen von Zeichenfolgendaten

Die **Ausdruck** Feld in der Zeichenfolgen-Schnellansicht zeigt die aktuelle Variable oder einen Ausdruck, der Sie Normalzustand im Debugger.

Die **Wert** Feld zeigt den Zeichenfolgenwert. Die Text-Schnellansicht zeigt den nur-Text.

Ein leerer **Wert** gibt an, dass die bestimmte Schnellansicht die String-Datentyp nicht erkennen kann. Die XML-Schnellansicht zeigt z. B. ein leerer **Wert** für eine einfache Textzeichenfolge (mit keinen XML-Tags) oder einer JSON-Zeichenfolge formatierte. Wenn Sie eine nicht erkennbare Zeichenfolge in einer Schnellansicht anzeigen möchten, verwenden Sie die Text-Schnellansicht.

### <a name="view-json-string-data"></a>JSON-Zeichenfolge-Daten anzeigen

Eine wohlgeformte JSON-Zeichenfolge wird ähnlich der folgenden Abbildung in der JSON-Schnellansicht angezeigt. Falsch formatiertes JSON möglicherweise ein Fehlersymbol (oder leer, wenn nicht erkannte) angezeigt. Wenn ein Fehlersymbol angezeigt wird, kopieren Sie die JSON-Zeichenfolge in ein JSON-Linting-Tool wie z. B. [JSLint](https://www.jslint.com/) zu den JSON-Fehler zu ermitteln.

![JSON-Zeichenfolgen-Schnellansicht](../debugger/media/dbg-tips-string-visualizer-json.png "JSON-Zeichenfolgen-Schnellansicht")

### <a name="view-xml-string-data"></a>XML-Zeichenfolge-Daten anzeigen

Wohlgeformte XML-Zeichenfolge wird im XML-Visualizer in der folgenden Abbildung ähneln. Falsch formatierte XML kann ohne die XML-Tags (oder leer, wenn nicht erkannte) angezeigt werden.

![XML-Zeichenfolgen-Schnellansicht](../debugger/media/dbg-string-visualizers-xml.png "XML-Zeichenfolgen-Schnellansicht")

### <a name="view-html-string-data"></a>Zeichenfolgendaten HTML anzeigen

Eine gut formatierte HTML-Zeichenfolge sieht in etwa wie die Ansicht, dass angezeigt wird, wenn die Zeichenfolge in einem Browser gerendert wird wie in der folgenden Abbildung dargestellt. Fehlerhaftes HTML möglicherweise als nur-Text angezeigt.

![HTML-Zeichenfolgen-Schnellansicht](../debugger/media/dbg-string-visualizers-html.png "HTML-Zeichenfolgen-Schnellansicht")

## <a name="see-also"></a>Siehe auch  
 [Erstellen Sie benutzerdefinierter Schnellansichten (c#, Visual Basic)](../debugger/create-custom-visualizers-of-data.md)