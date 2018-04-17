---
title: IDebugExpression2::EvaluateAsync | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IDebugExpression2::EvaluateAsync
helpviewer_keywords:
- IDebugExpression2::EvaluateAsync
ms.assetid: 848fe6cb-0759-42f2-890b-d2b551c527d6
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 13364d94f33eca33bf71b7077c19b9da54298ed7
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/16/2018
---
# <a name="idebugexpression2evaluateasync"></a>IDebugExpression2::EvaluateAsync
Diese Methode wertet den Ausdruck asynchron aus.  
  
## <a name="syntax"></a>Syntax  
  
```cpp  
HRESULT EvaluateAsync (   
   EVALFLAGS             dwFlags,  
   IDebugEventCallback2* pExprCallback  
);  
```  
  
```csharp  
int EvaluateAsync(  
   enum_EVALFLAGS       dwFlags,   
   IDebugEventCallback2 pExprCallback  
);  
```  
  
#### <a name="parameters"></a>Parameter  
 `dwFlags`  
 [in] Eine Kombination aus Flags aus der [EVALFLAGS](../../../extensibility/debugger/reference/evalflags.md) -Enumeration, die Auswertung von Ausdrücken zu steuern.  
  
 `pExprCallback`  
 [in] Dieser Parameter ist immer ein null-Wert.  
  
## <a name="return-value"></a>Rückgabewert  
 Im Erfolgsfall gibt `S_OK`; andernfalls wird ein Fehlercode zurückgegeben. Ein typische Fehlercode lautet:  
  
|Fehler|Beschreibung|  
|-----------|-----------------|  
|E_EVALUATE_BUSY_WITH_EVALUATION|Derzeit einem anderen Ausdruck ausgewertet wird, und gleichzeitige ausdrucksauswertung wird nicht unterstützt.|  
  
## <a name="remarks"></a>Hinweise  
 Diese Methode sollte zurückgeben, sofort, nachdem sie die Auswertung von Ausdrücken gestartet wurde. Wenn der Ausdruck erfolgreich ausgewertet wird, ein [IDebugExpressionEvaluationCompleteEvent2](../../../extensibility/debugger/reference/idebugexpressionevaluationcompleteevent2.md) gesendet werden muss, um die [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md) Ereignisrückruf bereitgestellt durch [Anfügen ](../../../extensibility/debugger/reference/idebugprogram2-attach.md) oder [Anfügen](../../../extensibility/debugger/reference/idebugengine2-attach.md).  
  
## <a name="example"></a>Beispiel  
 Im folgende Beispiel wird gezeigt, wie diese Methode für eine einfache implementiert `CExpression` Objekt, implementiert die [IDebugExpression2](../../../extensibility/debugger/reference/idebugexpression2.md) Schnittstelle.  
  
```cpp  
HRESULT CExpression::EvaluateAsync(EVALFLAGS dwFlags,  
                                   IDebugEventCallback2* pExprCallback)  
{  
    // Set the aborted state to FALSE  
    // in case the user tries to redo the evaluation after aborting.  
    m_bAborted = FALSE;  
    // Post the WM_EVAL_EXPR message in the message queue of the current thread.  
    // This starts the expression evaluation on a background thread.  
    PostThreadMessage(GetCurrentThreadId(), WM_EVAL_EXPR, 0, (LPARAM) this);  
    return S_OK;  
}  
```  
  
## <a name="see-also"></a>Siehe auch  
 [IDebugExpression2](../../../extensibility/debugger/reference/idebugexpression2.md)   
 [IDebugExpressionEvaluationCompleteEvent2](../../../extensibility/debugger/reference/idebugexpressionevaluationcompleteevent2.md)   
 [EVALFLAGS](../../../extensibility/debugger/reference/evalflags.md)   
 [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md)