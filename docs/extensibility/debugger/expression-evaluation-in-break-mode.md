---
title: "Auswertung von Ausdrücken im Unterbrechungsmodus | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- break mode, expression evaluation
- debugging [Debugging SDK], expression evaluation
- expression evaluation, break mode
ms.assetid: 34fe5b58-15d5-4387-a266-72120f90a4b6
caps.latest.revision: "10"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: cd28633fcb4b8186dae154428e489d51041aa8b2
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/22/2017
---
# <a name="expression-evaluation-in-break-mode"></a>Auswertung von Ausdrücken im Unterbrechungsmodus
Im folgenden wird erläutert, das auftritt, wenn der Debugger im Unterbrechungsmodus und Auswertung von Ausdrücken durchführen muss.  
  
## <a name="expression-evaluation-process"></a>Expression-Evaluierungsprozess  
 Dies sind die grundlegenden Schritte bei der Auswertung eines Ausdrucks:  
  
1.  Ruft die Sitzungs-Debug-Manager (SDM) [IDebugStackFrame2::GetExpressionContext](../../extensibility/debugger/reference/idebugstackframe2-getexpressioncontext.md) beim Abrufen einer Ausdruck-Kontext-Schnittstelle [IDebugExpressionContext2](../../extensibility/debugger/reference/idebugexpressioncontext2.md).  
  
2.  Ruft die SDM dann [IDebugExpressionContext2::ParseText](../../extensibility/debugger/reference/idebugexpressioncontext2-parsetext.md) mit der Zeichenfolge, die analysiert werden.  
  
3.  Wenn ParseText nicht S_OK zurückgibt, wird die Ursache des Fehlers zurückgegeben.  
  
     -Ansonsten-  
  
     Wenn ParseText S_OK zurückgibt, das SDM kann, rufen Sie entweder [IDebugExpression2::EvaluateSync](../../extensibility/debugger/reference/idebugexpression2-evaluatesync.md) oder [IDebugExpression2::EvaluateAsync](../../extensibility/debugger/reference/idebugexpression2-evaluateasync.md) um einen endgültigen Wert aus dem analysierten Ausdruck abzurufen.  
  
    -   Im Fall mit `IDebugExpression2::EvaluateSync`, die bestimmten Rückrufschnittstelle wird verwendet, um den laufenden Prozess der Auswertung zu kommunizieren. Der endgültige Wert wird zurückgegeben, eine [IDebugProperty2](../../extensibility/debugger/reference/idebugproperty2.md) Schnittstelle.  
  
    -   Im Fall mit `IDebugExpression2::EvaluateAsync`, die bestimmten Rückrufschnittstelle wird verwendet, um den laufenden Prozess der Auswertung zu kommunizieren. Nachdem die Auswertung abgeschlossen ist, sendet EvaluateAsync ein [IDebugExpressionEvaluationCompleteEvent2](../../extensibility/debugger/reference/idebugexpressionevaluationcompleteevent2.md) Schnittstelle durch den Rückruf. Mit dieser Ereignisschnittstelle der endgültige Wert abgerufen werden kann, mit [GetResult](../../extensibility/debugger/reference/idebugexpressionevaluationcompleteevent2-getresult.md).  
  
## <a name="see-also"></a>Siehe auch  
 [Aufrufen von Debuggerereignissen](../../extensibility/debugger/calling-debugger-events.md)