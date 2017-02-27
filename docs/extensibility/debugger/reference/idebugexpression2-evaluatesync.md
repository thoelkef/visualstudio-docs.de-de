---
title: "IDebugExpression2::EvaluateSync | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugExpression2::EvaluateSync"
helpviewer_keywords: 
  - "IDebugExpression2::EvaluateSync"
ms.assetid: 88964915-dce3-4005-b4f3-9f37415e41e4
caps.latest.revision: 15
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 15
---
# IDebugExpression2::EvaluateSync
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Diese Methode wertet den Ausdruck synchron aus.  
  
## Syntax  
  
```cpp#  
HRESULT EvaluateSync(   
   EVALFLAGS             dwFlags,  
   DWORD                 dwTimeout,  
   IDebugEventCallback2* pExprCallback,  
   IDebugProperty2**     ppResult  
);  
```  
  
```c#  
int EvaluateSync(  
   enum_EVALFLAGS       dwFlags,   
   uint                 dwTimeout,   
   IDebugEventCallback2 pExprCallback,   
   out IDebugProperty2  ppResult  
);  
```  
  
#### Parameter  
 `dwFlags`  
 \[in\]  Eine Kombination von Flags aus der [EVALFLAGS](../../../extensibility/debugger/reference/evalflags.md)\-Enumeration, die Ausdrucksauswertung steuern.  
  
 `dwTimeout`  
 \[in\]  Maximale Zeit in Millisekunden, bevor der Rückgabe dieser Methode zu warten.  `INFINITE` verwenden, um unbegrenzt zu warten.  
  
 `pExprCallback`  
 \[in\]Dieser Parameter ist immer ein NULL\-Wert.  
  
 `ppResult`  
 \[out\]  Gibt das [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)\-Objekt zurück, das das Ergebnis der Ausdrucksauswertung enthält.  
  
## Rückgabewert  
 Bei Erfolg gibt `S_OK`zurück. Andernfalls wird ein Fehlercode zurückgegeben.  Einige typische Fehlercodes sind:  
  
|Fehler|Beschreibung|  
|------------|------------------|  
|E\_EVALUATE\_BUSY\_WITH\_EVALUATION|Ein anderer Ausdruck wird nur ausgewertet, und gleichzeitige Ausdrucksauswertung wird nicht unterstützt.|  
|E\_EVALUATE\_TIMEOUT|Auswertung ein Timeout aufgetreten ist.|  
  
## Hinweise  
 Für synchrone Auswertung ist es nicht erforderlich, ein Ereignis in Visual Studio bei Beendigung der Auswertung zu senden.  
  
## Beispiel  
 Im folgenden Beispiel wird veranschaulicht, wie diese Methode für ein einfaches `CExpression`\-Objekt implementiert, das die [IDebugExpression2](../../../extensibility/debugger/reference/idebugexpression2.md)\-Schnittstelle implementiert.  
  
```cpp#  
HRESULT CExpression::EvaluateSync(EVALFLAGS dwFlags,  
                                  DWORD dwTimeout,  
                                  IDebugEventCallback2* pExprCallback,  
                                  IDebugProperty2** ppResult)  
{  
    // Set the aborted state to FALSE.    
    m_bAborted = FALSE;    
    // Delegate the evaluation to EvalExpression.    
    return EvalExpression(TRUE, ppResult);    
}  
  
HRESULT CExpression::EvalExpression(BOOL bSynchronous,  
                                    IDebugProperty2** ppResult)  
{  
    HRESULT hr;  
  
    // Get the value of an environment variable.  
    PCSTR pszVal = m_pEnvBlock->GetEnv(m_pszVarName);  
    // Create and initialize a CEnvVar object with the retrieved value.  
    // CEnvVar implements the IDebugProperty2 interface.  
    CComObject<CEnvVar> *pEnvVar;  
    CComObject<CEnvVar>::CreateInstance(&pEnvVar);  
    pEnvVar->Init(m_pszVarName, pszVal, m_pDoc);  
  
    if (pszVal) {  
        // Check for synchronous evaluation.  
        if (bSynchronous) {  
            // Set and AddRef the result, IDebugProperty2 interface.  
            *ppResult = pEnvVar;  
            (*ppResult)->AddRef();  
            hr = S_OK;  
        } else {  
            //For asynchronous evaluation, send an evaluation complete event.  
            CExprEvalEvent *pExprEvent = new CExprEvalEvent(this, pEnvVar);  
            pExprEvent->SendEvent(m_pExprCallback, NULL, NULL, NULL);  
        }  
    } else {  
        // If a valid value is not retrieved, return E_FAIL.  
        hr = E_FAIL;  
    }  
    return hr;  
}  
```  
  
## Siehe auch  
 [IDebugExpression2](../../../extensibility/debugger/reference/idebugexpression2.md)   
 [EVALFLAGS](../../../extensibility/debugger/reference/evalflags.md)   
 [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md)   
 [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)