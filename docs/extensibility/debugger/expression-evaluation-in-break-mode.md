---
title: Ausdrucksauswertung im Unterbrechungsmodus | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- break mode, expression evaluation
- debugging [Debugging SDK], expression evaluation
- expression evaluation, break mode
ms.assetid: 34fe5b58-15d5-4387-a266-72120f90a4b6
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 852b4284bbbf59ce8f3964d98f0464e583f1444f
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/25/2019
ms.locfileid: "55028672"
---
# <a name="expression-evaluation-in-break-mode"></a>Ausdrucksauswertung im Unterbrechungsmodus
Der folgende Abschnitt beschreibt den Prozess, der auftritt, wenn der Debugger im Unterbrechungsmodus befindet und muss die Auswertung von Ausdrücken durchzuführen.  
  
## <a name="expression-evaluation-process"></a>Ausdruck Evaluierungsprozesses  
 Es folgen die grundlegenden Schritte bei der Auswertung eines Ausdrucks:  
  
1.  Ruft die Sitzungs-Debug-Manager (SDM) [IDebugStackFrame2::GetExpressionContext](../../extensibility/debugger/reference/idebugstackframe2-getexpressioncontext.md) zum Abrufen einer Ausdruck-Kontext-Schnittstelle [IDebugExpressionContext2](../../extensibility/debugger/reference/idebugexpressioncontext2.md).  
  
2.  Klicken Sie dann aufruft, das SDM [IDebugExpressionContext2::ParseText](../../extensibility/debugger/reference/idebugexpressioncontext2-parsetext.md) mit der Zeichenfolge analysiert werden.  
  
3.  Falls ParseText S_OK zurückgegeben wird, wird die Ursache des Fehlers zurückgegeben.  
  
     – andernfalls:  
  
     Wenn ParseText S_OK zurückgibt, das SDM kann, rufen Sie entweder [IDebugExpression2::EvaluateSync](../../extensibility/debugger/reference/idebugexpression2-evaluatesync.md) oder [IDebugExpression2::EvaluateAsync](../../extensibility/debugger/reference/idebugexpression2-evaluateasync.md) um einen endgültigen Wert aus den analysierten Ausdruck abzurufen.  
  
    -   Bei Verwendung `IDebugExpression2::EvaluateSync`, die bestimmten Rückrufschnittstelle kommuniziert der Auswertung des laufenden Prozesses. Der endgültige Wert wird zurückgegeben, eine [IDebugProperty2](../../extensibility/debugger/reference/idebugproperty2.md) Schnittstelle.  
  
    -   Bei Verwendung `IDebugExpression2::EvaluateAsync`, die bestimmten Rückrufschnittstelle kommuniziert der Auswertung des laufenden Prozesses. Nachdem die Auswertung abgeschlossen ist, sendet EvaluateAsync ein [IDebugExpressionEvaluationCompleteEvent2](../../extensibility/debugger/reference/idebugexpressionevaluationcompleteevent2.md) Schnittstelle über den Rückruf. Mit dieser Ereignisschnittstelle, der endgültige Wert in den Ergebnissen [GetResult](../../extensibility/debugger/reference/idebugexpressionevaluationcompleteevent2-getresult.md).  
  
## <a name="see-also"></a>Siehe auch  
 [Aufrufen von debuggerereignissen](../../extensibility/debugger/calling-debugger-events.md)