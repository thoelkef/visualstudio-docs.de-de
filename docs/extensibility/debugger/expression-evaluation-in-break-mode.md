---
title: Ausdrucksauswertung im Unterbrechungsmodus | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- break mode, expression evaluation
- debugging [Debugging SDK], expression evaluation
- expression evaluation, break mode
ms.assetid: 34fe5b58-15d5-4387-a266-72120f90a4b6
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: bc09fc43bd9f0edea4f6dc32e5f37c387c045796
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/06/2020
ms.locfileid: "80738719"
---
# <a name="expression-evaluation-in-break-mode"></a>Ausdrucksauswertung im Unterbrechungsmodus
Im folgenden Abschnitt wird der Prozess beschrieben, der auftritt, wenn sich der Debugger im Unterbrechungsmodus befindet und eine Ausdrucksauswertung durchführen muss.

## <a name="expression-evaluation-process"></a>Ausdrucksauswertungsprozess
 Im Folgenden sind die grundlegenden Schritte zur Bewertung eines Ausdrucks zu finden:

1. Der Sitzungsdebug-Manager (SDM) ruft [IDebugStackFrame2::GetExpressionContext](../../extensibility/debugger/reference/idebugstackframe2-getexpressioncontext.md) auf, um eine Expressioncontext-Schnittstelle, [IDebugExpressionContext2](../../extensibility/debugger/reference/idebugexpressioncontext2.md), abzuruft.

2. Das SDM ruft dann [IDebugExpressionContext2::ParseText](../../extensibility/debugger/reference/idebugexpressioncontext2-parsetext.md) mit der zu analysierenden Zeichenfolge auf.

3. Wenn ParseText S_OK nicht zurückgibt, wird der Grund für den Fehler zurückgegeben.

     -sonst-

     Wenn ParseText S_OK zurückgibt, kann das SDM entweder [IDebugExpression2::EvaluateSync](../../extensibility/debugger/reference/idebugexpression2-evaluatesync.md) oder [IDebugExpression2::EvaluateAsync](../../extensibility/debugger/reference/idebugexpression2-evaluateasync.md) aufrufen, um einen endgültigen Wert aus dem analysierten Ausdruck abzurufen.

    - Bei `IDebugExpression2::EvaluateSync`verwendung von kommuniziert die angegebene Rückrufschnittstelle den laufenden Prozess der Auswertung. Der endgültige Wert wird in einer [IDebugProperty2-Schnittstelle](../../extensibility/debugger/reference/idebugproperty2.md) zurückgegeben.

    - Bei `IDebugExpression2::EvaluateAsync`verwendung von kommuniziert die angegebene Rückrufschnittstelle den laufenden Prozess der Auswertung. Sobald die Auswertung abgeschlossen ist, sendet EvaluateAsync eine [IDebugExpressionEvaluationCompleteEvent2-Schnittstelle](../../extensibility/debugger/reference/idebugexpressionevaluationcompleteevent2.md) über den Rückruf. Mit dieser Ereignisschnittstelle ergibt sich der endgültige Wert mit [GetResult](../../extensibility/debugger/reference/idebugexpressionevaluationcompleteevent2-getresult.md).

## <a name="see-also"></a>Weitere Informationen
- [Aufrufen von Debuggerereignissen](../../extensibility/debugger/calling-debugger-events.md)
