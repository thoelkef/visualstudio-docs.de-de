---
title: 'Gewusst wie: Testen und Debuggen einer Schnellansicht | Microsoft-Dokumentation'
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- visualizers, testing
- visualizers, debugging
- debugging [Visual Studio], visualizers
ms.assetid: 5cc12ce8-c819-48e4-b487-98d403001b28
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 2a0d2fdcd0685b83f63e9354b96146c1c869b355
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/22/2019
ms.locfileid: "72732405"
---
# <a name="how-to-test-and-debug-a-visualizer"></a>Gewusst wie: Testen und Debuggen einer Schnellansicht
Wenn Sie eine Schnellansicht erstellt haben, müssen Sie sie debuggen und testen.

Eine Möglichkeit zum Testen einer Schnellansicht besteht darin, sie in Visual Studio zu installieren und über das Debuggerfenster aufzurufen. (Weitere Informationen finden [Sie unter Gewusst wie: Installieren einer](../debugger/how-to-install-a-visualizer.md)Schnellansicht.) Wenn Sie dies tun, müssen Sie eine zweite Instanz von Visual Studio verwenden, um die Schnellansicht anzufügen und zu debuggen, die in der ersten Instanz des Debuggers ausgeführt wird.

Sie können eine Schnellansicht auch einfacher debuggen, indem die Schnellansicht von einem Testtreiber ausgeführt wird. Die Schnellansicht-APIs erlauben die einfache Erstellung eines solchen Treibers, der *Schnellansicht-Entwicklungshost* genannt wird.

### <a name="to-create-a-visualizer-development-host"></a>So erstellen Sie einen Entwicklungshost für eine Schnellansicht

1. Fügen Sie in der Klasse auf Debuggerseite eine statische Methode ein, die ein <xref:Microsoft.VisualStudio.DebuggerVisualizers.VisualizerDevelopmentHost>-Objekt erstellt und dessen Show-Methode aufruft:

    ```csharp
    public static void TestShowVisualizer(object objectToVisualize)
    {
        VisualizerDevelopmentHost myHost = new VisualizerDevelopmentHost(objectToVisualize, typeof(DebuggerSide));
        myHost.ShowVisualizer();
    }
    ```

    Die zur Erstellung des Hosts verwendeten Parameter umfassen das in der Schnellansicht (`objectToVisualize`) angezeigte Datenobjekt und den Typ der debuggerseitigen Klasse.

2. Fügen Sie die folgende Anweisung hinzu, um `TestShowVisualizer` aufzurufen. Wenn Sie eine Schnellansicht in einer Klassenbibliothek erstellt haben, müssen Sie eine ausführbare Datei erstellen, um die Klassenbibliothek aufzurufen, und folgende Anweisung in die ausführbare Datei einfügen:

    ```csharp
    DebuggerSide.TestShowVisualizer(myString);
    ```

    Ein ausführeres Beispiel finden Sie unter Exemplarische Vorgehensweise [: Schreiben einer Schnellansicht C#in ](../debugger/walkthrough-writing-a-visualizer-in-csharp.md).

## <a name="see-also"></a>Siehe auch
- [Exemplarische Vorgehensweise: Schreiben einer Schnellansicht in C#](../debugger/walkthrough-writing-a-visualizer-in-csharp.md)
- [Gewusst wie: Installieren einer Schnellansicht](../debugger/how-to-install-a-visualizer.md)
- [Erstellen benutzerdefinierter Schnellansichten](../debugger/create-custom-visualizers-of-data.md)
