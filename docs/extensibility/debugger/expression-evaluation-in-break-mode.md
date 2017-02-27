---
title: "Auswertung von Ausdr&#252;cken im Unterbrechungsmodus | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Unterbrechungsmodus Auswertung von Ausdrücken"
  - "Debuggen die Auswertung von Ausdrücken [Debugging-SDK]"
  - "Auswertung von Ausdrücken, im Unterbrechungsmodus"
ms.assetid: 34fe5b58-15d5-4387-a266-72120f90a4b6
caps.latest.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 10
---
# Auswertung von Ausdr&#252;cken im Unterbrechungsmodus
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Im Folgenden beschreibt den Prozess, der auftritt, wenn sich der Debugger im Unterbrechungsmodus befindet und Ausdrucksauswertung werden muss.  
  
## Ausdrucksauswertungs\-Prozess  
 Im Folgenden sind die grundlegenden Schritte, die beim Laden eines Ausdrucks beteiligt sind, ergeben:  
  
1.  Die Aufrufe Debuggen [IDebugStackFrame2::GetExpressionContext](../../extensibility/debugger/reference/idebugstackframe2-getexpressioncontext.md) des Managers der Sitzung \(SDM\) zum Abrufen einer Ausdruckskontext Oberfläche, [IDebugExpressionContext2](../../extensibility/debugger/reference/idebugexpressioncontext2.md).  
  
2.  Das SDM ruft dann [IDebugExpressionContext2::ParseText](../../extensibility/debugger/reference/idebugexpressioncontext2-parsetext.md) mit der zu analysierenden an Zeichenfolge.  
  
3.  Wenn ParseText nicht S\_OK zurückgibt, wird der Grund für den Fehler zurückgegeben.  
  
     Andernfalls \-  
  
     Wenn ParseText S\_OK zurückgibt, kann das SDM entweder [IDebugExpression2::EvaluateSync](../../extensibility/debugger/reference/idebugexpression2-evaluatesync.md) oder [IDebugExpression2::EvaluateAsync](../../extensibility/debugger/reference/idebugexpression2-evaluateasync.md) aufrufen, um ein endgültiger Wert aus dem analysierten Ausdruck abzurufen.  
  
    -   Bei der Verwendung von `IDebugExpression2::EvaluateSync`, wird die angegebene Rückrufschnittstelle verwendet, um den laufenden Prozess der Auswertung zu übermitteln.  Der endgültige Wert wird in einer [IDebugProperty2](../../extensibility/debugger/reference/idebugproperty2.md)\-Schnittstelle zurückgegeben.  
  
    -   Bei der Verwendung von `IDebugExpression2::EvaluateAsync`, wird die angegebene Rückrufschnittstelle verwendet, um den laufenden Prozess der Auswertung zu übermitteln.  Wenn die Auswertung abgeschlossen ist, sendet EvaluateAsync eine [IDebugExpressionEvaluationCompleteEvent2](../../extensibility/debugger/reference/idebugexpressionevaluationcompleteevent2.md)\-Schnittstelle vom Rückruf.  Mit dieser Ereignisschnittstelle kann der endgültige Wert mit [GetResult](../../extensibility/debugger/reference/idebugexpressionevaluationcompleteevent2-getresult.md)abgerufen werden.  
  
## Siehe auch  
 [Aufrufen von Debugger\-Ereignissen](../../extensibility/debugger/calling-debugger-events.md)