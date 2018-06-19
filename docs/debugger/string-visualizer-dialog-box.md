---
title: Zeichenfolgen in einen Zeichenfolgen-Schnellansicht anzeigen | Microsoft Docs
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
ms.openlocfilehash: a3a0575b02422bf83dd560d3eae5724b0a50d3f3
ms.sourcegitcommit: 3d10b93eb5b326639f3e5c19b9e6a8d1ba078de1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/18/2018
ms.locfileid: "31476974"
---
# <a name="view-strings-in-a-string-visualizer-in-visual-studio"></a>Anzeigen von Zeichenfolgen in einen Zeichenfolgen-Schnellansicht in Visual Studio
Während des Debuggens, können Sie eine Zeichenfolgen-Schnellansicht zum Anzeigen von Zeichenfolgen öffnen, die zur Ansicht in einem Daten-QuickInfo oder die Debugger-Fenster zu lang sind. In vielen Fällen können die Schnellansicht falsch formatierte Zeichenfolgen zu identifizieren.

Die Schnellansichten für integrierte Standardzeichenfolge umfassen nur-Text, XML, HTML und JSON. Einigen andere Typen, wie z. B. WPF-Objekte, die im Debugger angezeigt werden, wie Windows die **"Auto"** Fenster können Sie auch Schnellansichten öffnen.

## <a name="open-a-string-visualizer"></a>Öffnen Sie eine Zeichenfolgen-Schnellansicht

Klicken Sie zum Anzeigen einer nur-Text, XML, HTML oder JSON-Zeichenfolge auf das Lupensymbol ![VisualizerIcon](../debugger/media/dbg-tips-visualizer-icon.png "Schnellansicht Symbol") beim mit dem Mauszeiger auf eine Variable, die einen Zeichenfolgenwert enthält. Sie müssen im Debugger auf das Lupensymbol finden Sie unter angehalten werden.

![Öffnen Sie eine Zeichenfolgen-Schnellansicht](../debugger/media/dbg-tips-string-visualizers.png "OpenStringVisualizer")

## <a name="view-string-data"></a>Anzeigen von Zeichenfolgendaten

Die **Ausdruck** Feld in den Zeichenfolgen-Schnellansicht zeigt die aktuelle Variable oder ein Ausdruck, die Sie über bewegt wird im Debugger.

Die **Wert** Feld zeigt den Zeichenfolgenwert. Die Text-Schnellansicht zeigt den nur-Text.

Ein leerer **Wert** gibt an, dass die bestimmte Schnellansicht String-Datentyp nicht erkennen kann. Die XML-Schnellansicht zeigt z. B. eine leere **Wert** für eine einfache Textzeichenfolge (mit keinen XML-Tags) oder einer JSON-Zeichenfolge formatierte. Wenn Sie eine nicht erkennbare Zeichenfolge in einer Schnellansicht anzeigen möchten, verwenden Sie die Text-Schnellansicht.

### <a name="view-json-string-data"></a>Ansichtsdaten JSON-Zeichenfolge

Eine wohlgeformte JSON-Zeichenfolge wird ähnlich der folgenden Abbildung in der JSON-Schnellansicht angezeigt. Falsch formatierte JSON möglicherweise ein Fehlersymbol (oder leer, wenn unbekannte) angezeigt.

![JSON-Zeichenfolgen-Schnellansicht](../debugger/media/dbg-tips-string-visualizer-json.png "JSON-Zeichenfolgen-Schnellansicht")

### <a name="view-xml-string-data"></a>XML-Zeichenfolge-Anzeigedaten

Eine wohlgeformte XML-Zeichenfolge wird ähnlich der folgenden Abbildung in der XML-Schnellansicht angezeigt. Falsch formatierte XML kann ohne die XML-Tags (oder leer, wenn unbekannte) angezeigt werden.

![XML-Zeichenfolgen-Schnellansicht](../debugger/media/dbg-string-visualizers-xml.png "XML-Zeichenfolgen-Schnellansicht")

### <a name="view-html-string-data"></a>HTML-Ansicht von Zeichenfolgendaten

Eine wohlgeformte HTML-Zeichenfolge wird ähnlich der Ansicht angezeigt, wenn die Zeichenfolge in einem Browser gerendert wird wie in der folgenden Abbildung dargestellt angezeigt. Fehlerhaftes HTML möglicherweise als nur-Text angezeigt.

![HTML-Zeichenfolgen-Schnellansicht](../debugger/media/dbg-string-visualizers-html.png "HTML-Zeichenfolgen-Schnellansicht")

## <a name="see-also"></a>Siehe auch  
 [Erstellen Sie benutzerdefinierte Schnellansichten (c#, Visual Basic)](../debugger/create-custom-visualizers-of-data.md)