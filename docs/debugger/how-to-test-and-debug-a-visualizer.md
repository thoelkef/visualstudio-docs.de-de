---
title: "Gewusst wie: Testen und Debuggen einer Schnellansicht | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "FSharp"
  - "VB"
  - "CSharp"
  - "C++"
helpviewer_keywords: 
  - "Debuggen [Visual Studio], Schnellansichten"
  - "Schnellansichten, Debuggen"
  - "Schnellansichten, Testen"
ms.assetid: 5cc12ce8-c819-48e4-b487-98d403001b28
caps.latest.revision: 15
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 15
---
# Gewusst wie: Testen und Debuggen einer Schnellansicht
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Wenn Sie eine Schnellansicht erstellt haben, müssen Sie sie debuggen und testen.  
  
 Eine Möglichkeit zum Testen einer Schnellansicht besteht darin, sie in Visual Studio zu installieren und über das Debuggerfenster aufzurufen. \(Siehe [Gewusst wie: Installieren einer Schnellansicht](../debugger/how-to-install-a-visualizer.md).\) Dabei müssen Sie eine zweite Instanz von Visual Studio verwenden, um die Schnellansicht anzufügen und zu debuggen, die in der ersten Instanz des Debuggers ausgeführt wird.  
  
 Sie können eine Schnellansicht auch einfacher debuggen, indem die Schnellansicht von einem Testtreiber ausgeführt wird.  Die Schnellansicht\-APIs erlauben die einfache Erstellung eines solchen Treibers, der *Schnellansicht\-Entwicklungshost* genannt wird.  
  
### So erstellen Sie einen Entwicklungshost für eine Schnellansicht  
  
1.  Fügen Sie in der Klasse auf Debuggerseite eine statische Methode ein, die ein <xref:Microsoft.VisualStudio.DebuggerVisualizers.VisualizerDevelopmentHost>\-Objekt erstellt und dessen Show\-Methode aufruft:  
  
    ```  
    public static void TestShowVisualizer(object objectToVisualize)  
    {  
       VisualizerDevelopmentHost myHost = new VisualizerDevelopmentHost(objectToVisualize, typeof(DebuggerSide));  
       myHost.ShowVisualizer();  
    }  
    ```  
  
     Die zur Erstellung des Hosts verwendeten Parameter umfassen das in der Schnellansicht \(`objectToVisualize`\) angezeigte Datenobjekt und den Typ der debuggerseitigen Klasse.  
  
2.  Fügen Sie die folgende Anweisung hinzu, um `TestShowVisualizer` aufzurufen.  Wenn Sie eine Schnellansicht in einer Klassenbibliothek erstellt haben, müssen Sie eine ausführbare Datei erstellen, um die Klassenbibliothek aufzurufen, und folgende Anweisung in die ausführbare Datei einfügen:  
  
    ```  
    DebuggerSide.TestShowVisualizer(myString);  
    ```  
  
     Ein ausführlicheres Beispiel finden Sie unter [Exemplarische Vorgehensweise: Schreiben einer Schnellansicht in C\#](../debugger/walkthrough-writing-a-visualizer-in-csharp.md).  
  
## Siehe auch  
 [Exemplarische Vorgehensweise: Schreiben einer Schnellansicht in C\#](../debugger/walkthrough-writing-a-visualizer-in-csharp.md)   
 [Gewusst wie: Installieren einer Schnellansicht](../debugger/how-to-install-a-visualizer.md)   
 [Schnellansichten](../debugger/create-custom-visualizers-of-data.md)