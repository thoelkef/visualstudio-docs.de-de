---
title: "IDebugExpression2::EvaluateAsync | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugExpression2::EvaluateAsync"
helpviewer_keywords: 
  - "IDebugExpression2::EvaluateAsync"
ms.assetid: 848fe6cb-0759-42f2-890b-d2b551c527d6
caps.latest.revision: 15
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 15
---
# IDebugExpression2::EvaluateAsync
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Diese Methode wertet den Ausdruck asynchron aus.  
  
## Syntax  
  
```cpp#  
HRESULT EvaluateAsync (   
   EVALFLAGS             dwFlags,  
   IDebugEventCallback2* pExprCallback  
);  
```  
  
```c#  
int EvaluateAsync(  
   enum_EVALFLAGS       dwFlags,   
   IDebugEventCallback2 pExprCallback  
);  
```  
  
#### Parameter  
 `dwFlags`  
 \[in\]  Eine Kombination von Flags aus der [EVALFLAGS](../../../extensibility/debugger/reference/evalflags.md)\-Enumeration, die Ausdrucksauswertung steuern.  
  
 `pExprCallback`  
 \[in\]  Dieser Parameter ist immer ein NULL\-Wert.  
  
## Rückgabewert  
 Bei Erfolg gibt `S_OK`zurück. Andernfalls wird ein Fehlercode zurückgegeben.  Ein typischer Fehlercode ist:  
  
|Fehler|Beschreibung|  
|------------|------------------|  
|E\_EVALUATE\_BUSY\_WITH\_EVALUATION|Ein anderer Ausdruck wird nur ausgewertet, und gleichzeitige Ausdrucksauswertung wird nicht unterstützt.|  
  
## Hinweise  
 Diese Methode sollte sofort zurückkehren, nachdem sie die Ausdrucksauswertung gestartet wurde.  Wenn der Ausdruck erfolgreich ausgewertet wird, muss [IDebugExpressionEvaluationCompleteEvent2](../../../extensibility/debugger/reference/idebugexpressionevaluationcompleteevent2.md) an den Rückruf [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md)\-Ereignis gesendet werden, wie durch [Anfügen](../../../extensibility/debugger/reference/idebugprogram2-attach.md) oder [Anfügen](../../../extensibility/debugger/reference/idebugengine2-attach.md)angegeben.  
  
## Beispiel  
 Im folgenden Beispiel wird veranschaulicht, wie diese Methode für ein einfaches `CExpression`\-Objekt implementiert, das die [IDebugExpression2](../../../extensibility/debugger/reference/idebugexpression2.md)\-Schnittstelle implementiert.  
  
```cpp#  
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
  
## Siehe auch  
 [IDebugExpression2](../../../extensibility/debugger/reference/idebugexpression2.md)   
 [IDebugExpressionEvaluationCompleteEvent2](../../../extensibility/debugger/reference/idebugexpressionevaluationcompleteevent2.md)   
 [EVALFLAGS](../../../extensibility/debugger/reference/evalflags.md)   
 [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md)