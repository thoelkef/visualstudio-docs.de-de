---
title: "Schrittweise Ausf&#252;hrung in den Unterbrechungsmodus | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Unterbrechungsmodus ausführen in Einzelschritten"
  - "Ausführen in Einzelschritten, im Unterbrechungsmodus"
  - "Debuggen [Debugging-SDK], schrittweise Ausführung im Unterbrechungsmodus"
ms.assetid: b08dc8ee-6c63-4462-a097-6f525cfbb35a
caps.latest.revision: 7
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 7
---
# Schrittweise Ausf&#252;hrung in den Unterbrechungsmodus
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Im Folgenden beschreibt den Prozess, der auftritt, wenn sich der Debugger im Unterbrechungsmodus befindet und über Code werden muss:  
  
## Bitten Prozess  
  
1.  Aufruf [IDebugProgram2::Schritt](../../extensibility/debugger/reference/idebugprogram2-step.md) mit [STEPKIND](../../extensibility/debugger/reference/stepkind.md) und [STEPUNIT](../../extensibility/debugger/reference/stepunit.md)\-Argumenten zum Erstellen eines Schritts durchzuführen.  
  
2.  Wenn der Schritt abgeschlossen ist, senden Sie [IDebugStepCompleteEvent2](../../extensibility/debugger/reference/idebugstepcompleteevent2.md) als aufhörendes Ereignis.  
  
## Siehe auch  
 [Aufrufen von Debugger\-Ereignissen](../../extensibility/debugger/calling-debugger-events.md)