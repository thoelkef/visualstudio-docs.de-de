---
title: "Eine Anhalteanforderung steht an | Microsoft Docs"
ms.custom: ""
ms.date: "11/17/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vbc30947"
  - "bc30947"
helpviewer_keywords: 
  - "BC30947"
ms.assetid: 6bc4df1b-e833-47c7-9568-9ced67a2af5d
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Eine Anhalteanforderung steht an
Im Visual Studio\-Debugger gibt ein Ausdruck einen Prozeduraufruf an, aber es liegt eine Anforderung zum Anhalten des Threads vor.  
  
 Der Debugger versucht nicht, eine Prozedur in einem Thread aufzurufen, der nicht aktiv ist.  
  
 **Fehler\-ID:** BC30947  
  
### So beheben Sie diesen Fehler  
  
-   Bestimmen Sie nach Möglichkeit die Quelle der Anforderung zum Anhalten des Threads, damit Sie das Anhalten verhindern können.  
  
-   Beenden Sie das Debuggen, und starten Sie den Debugvorgang neu.  
  
## Siehe auch  
 [Debuggen in Visual Studio](../debugger/debugging-in-visual-studio.md)   
 [How to: Start Execution](http://msdn.microsoft.com/de-de/b0fe0ce5-900e-421f-a4c6-aa44ddae453c)   
 [How to: Stop Debugging or Stop Execution](http://msdn.microsoft.com/de-de/03c68f95-aa96-481b-990e-467e065453a5)   
 [Code Stepping Overview](http://msdn.microsoft.com/de-de/8791dac9-64d1-4bb9-b59e-8d59af1833f9)   
 [Ausdrücke in Visual Basic](../Topic/Expressions%20in%20Visual%20Basic.md)