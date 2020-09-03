---
title: Ausdrucks Auswertung im Umbruch Modus | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- break mode, expression evaluation
- debugging [Debugging SDK], expression evaluation
- expression evaluation, break mode
ms.assetid: 34fe5b58-15d5-4387-a266-72120f90a4b6
caps.latest.revision: 11
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 362e50e20519c358564d13ba169f706fe384ca5c
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "68152757"
---
# <a name="expression-evaluation-in-break-mode"></a>Ausdrucksauswertung im Unterbrechungsmodus
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Im folgenden wird der Prozess beschrieben, der auftritt, wenn sich der Debugger im Break-Modus befindet und die Ausdrucks Auswertung durchführen muss.  
  
## <a name="expression-evaluation-process"></a>Ausdrucks Auswertungsprozess  
 Dabei handelt es sich um die grundlegenden Schritte zum Auswerten eines Ausdrucks:  
  
1. Der Sitzungs-Debug-Manager (SDM) ruft [IDebugStackFrame2:: getexpressioncontext](../../extensibility/debugger/reference/idebugstackframe2-getexpressioncontext.md) auf, um eine Ausdrucks Kontext Schnittstelle ( [IDebugExpressionContext2](../../extensibility/debugger/reference/idebugexpressioncontext2.md)) zu erhalten.  
  
2. Der SDM ruft dann [IDebugExpressionContext2::P arsec-Text](../../extensibility/debugger/reference/idebugexpressioncontext2-parsetext.md) mit der zu erteilenden Zeichenfolge auf.  
  
3. Wenn "Parametertext" S_OK nicht zurückgibt, wird der Grund für den Fehler zurückgegeben.  
  
     sonst  
  
     Wenn "Parametertext" S_OK zurückgibt, kann die SDM dann entweder " [IDebugExpression2:: evaluatesync](../../extensibility/debugger/reference/idebugexpression2-evaluatesync.md) " oder " [IDebugExpression2:: evaluateasync](../../extensibility/debugger/reference/idebugexpression2-evaluateasync.md) " aufrufen, um einen endgültigen Wert aus dem analysierten Ausdruck abzurufen.  
  
    - Bei Verwendung von `IDebugExpression2::EvaluateSync` wird die angegebene Rückruf Schnittstelle verwendet, um den fortlaufenden Prozess der Auswertung zu kommunizieren. Der endgültige Wert wird in einer [IDebugProperty2](../../extensibility/debugger/reference/idebugproperty2.md) -Schnittstelle zurückgegeben.  
  
    - Bei Verwendung von `IDebugExpression2::EvaluateAsync` wird die angegebene Rückruf Schnittstelle verwendet, um den fortlaufenden Prozess der Auswertung zu kommunizieren. Wenn die Auswertung fertig ist, sendet evaluateasync eine [IDebugExpressionEvaluationCompleteEvent2](../../extensibility/debugger/reference/idebugexpressionevaluationcompleteevent2.md) -Schnittstelle über den Rückruf. Mit dieser Ereignis Schnittstelle kann der endgültige Wert mit [GetResult](../../extensibility/debugger/reference/idebugexpressionevaluationcompleteevent2-getresult.md)abgerufen werden.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Aufrufen von Debuggerereignissen](../../extensibility/debugger/calling-debugger-events.md)
