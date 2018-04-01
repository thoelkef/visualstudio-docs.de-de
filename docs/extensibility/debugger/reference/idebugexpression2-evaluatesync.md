---
title: IDebugExpression2::EvaluateSync | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- IDebugExpression2::EvaluateSync
helpviewer_keywords:
- IDebugExpression2::EvaluateSync
ms.assetid: 88964915-dce3-4005-b4f3-9f37415e41e4
caps.latest.revision: 15
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload:
- vssdk
ms.openlocfilehash: 2d17e31f3282727386654b0d1913fd00424c3c0a
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/22/2017
---
# <a name="idebugexpression2evaluatesync"></a>IDebugExpression2::EvaluateSync
Diese Methode wertet den Ausdruck synchron auf.  
  
## <a name="syntax"></a>Syntax  
  
```cpp  
HRESULT EvaluateSync(   
   EVALFLAGS             dwFlags,  
   DWORD                 dwTimeout,  
   IDebugEventCallback2* pExprCallback,  
   IDebugProperty2**     ppResult  
);  
```  
  
```csharp  
int EvaluateSync(  
   enum_EVALFLAGS       dwFlags,   
   uint                 dwTimeout,   
   IDebugEventCallback2 pExprCallback,   
   out IDebugProperty2  ppResult  
);  
```  
  
#### <a name="parameters"></a>Parameter  
 `dwFlags`  
 [in] Eine Kombination aus Flags aus der [EVALFLAGS](../../../extensibility/debugger/reference/evalflags.md) -Enumeration, die Auswertung von Ausdrücken zu steuern.  
  
 `dwTimeout`  
 [in] Maximale Zeit in Millisekunden, bis vor der Rückgabe dieser Methode. Verwendung `INFINITE` zum unendlichen Warten angibt.  
  
 `pExprCallback`  
 [in] Dieser Parameter ist immer ein null-Wert.  
  
 `ppResult`  
 [out] Gibt die [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md) -Objekt, das das Ergebnis der Auswertung von Ausdrücken enthält.  
  
## <a name="return-value"></a>Rückgabewert  
 Im Erfolgsfall gibt `S_OK`; andernfalls wird ein Fehlercode zurückgegeben. Einige typische Fehlercodes sind:  
  
|Fehler|Beschreibung|  
|-----------|-----------------|  
|E_EVALUATE_BUSY_WITH_EVALUATION|Derzeit einem anderen Ausdruck ausgewertet wird, und gleichzeitige ausdrucksauswertung wird nicht unterstützt.|  
|E_EVALUATE_TIMEOUT|Timeout bei der Auswertung.|  
  
## <a name="remarks"></a>Hinweise  
 Für die synchrone Auswertung ist es nicht notwendig, zum Senden eines Ereignisses wieder zu Visual Studio nach dem Abschluss der Auswertung.  
  
## <a name="example"></a>Beispiel  
 Im folgende Beispiel wird gezeigt, wie diese Methode für eine einfache implementiert `CExpression` Objekt, implementiert die [IDebugExpression2](../../../extensibility/debugger/reference/idebugexpression2.md) Schnittstelle.  
  
```cpp  
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
  
## <a name="see-also"></a>Siehe auch  
 [IDebugExpression2](../../../extensibility/debugger/reference/idebugexpression2.md)   
 [EVALFLAGS](../../../extensibility/debugger/reference/evalflags.md)   
 [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md)   
 [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)