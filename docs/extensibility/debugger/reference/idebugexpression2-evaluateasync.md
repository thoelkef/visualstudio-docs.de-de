---
title: IDebugExpression2::EvaluateAsync | Microsoft-Dokumentation
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
ms.openlocfilehash: e7906e1f1daa0b473473abd28417a2db1c9b7f98
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/23/2018
ms.locfileid: "49912824"
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
 [in] Eine Kombination von Flags aus der [EVALFLAGS](../../../extensibility/debugger/reference/evalflags.md) -Enumeration, die Auswertung des Ausdrucks steuern.  
  
 `pExprCallback`  
 [in] Dieser Parameter ist immer ein null-Wert.  
  
## <a name="return-value"></a>Rückgabewert  
 Wenn erfolgreich, wird `S_OK`; gibt andernfalls einen Fehlercode zurück. Ein typischer Fehlercode ist:  
  
|Fehler|Beschreibung|  
|-----------|-----------------|  
|E_EVALUATE_BUSY_WITH_EVALUATION|Derzeit einem anderen Ausdruck ausgewertet wird, und gleichzeitige ausdrucksauswertung wird nicht unterstützt.|  
  
## <a name="remarks"></a>Hinweise  
 Diese Methode sollte zurückgeben, sofort nach dem Start der Auswertung von Ausdrücken. Wenn der Ausdruck erfolgreich ausgewertet wird, eine [IDebugExpressionEvaluationCompleteEvent2](../../../extensibility/debugger/reference/idebugexpressionevaluationcompleteevent2.md) gesendet werden müssen, um die [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md) Ereignisrückruf wie angegeben über [Anfügen ](../../../extensibility/debugger/reference/idebugprogram2-attach.md) oder [Anfügen](../../../extensibility/debugger/reference/idebugengine2-attach.md).  
  
## <a name="example"></a>Beispiel  
 Das folgende Beispiel zeigt, wie Sie die Implementierung dieser Methode für eine einfache `CExpression` Objekt, das implementiert die [IDebugExpression2](../../../extensibility/debugger/reference/idebugexpression2.md) Schnittstelle.  
  
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