---
title: IDebugExpression2::EvaluateSync | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugExpression2::EvaluateSync
helpviewer_keywords:
- IDebugExpression2::EvaluateSync
ms.assetid: 88964915-dce3-4005-b4f3-9f37415e41e4
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 306ed6af2a0a0b8fdb4525a112e680e289e6e6df
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/06/2020
ms.locfileid: "80729675"
---
# <a name="idebugexpression2evaluatesync"></a>IDebugExpression2::EvaluateSync
Diese Methode wertet den Ausdruck synchron aus.

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

## <a name="parameters"></a>Parameter
`dwFlags`\
[in] Eine Kombination von Flags aus der EVALFLAGS-Enumeration, die die Ausdrucksauswertung steuern. [EVALFLAGS](../../../extensibility/debugger/reference/evalflags.md)

`dwTimeout`\
[in] Maximale Wartezeit in Millisekunden, bevor von dieser Methode zurückgegeben wird. Verwenden `INFINITE` Sie diese Verwendung, um auf unbestimmte Zeit zu warten.

`pExprCallback`\
[in] Dieser Parameter ist immer ein NULL-Wert.

`ppResult`\
[out] Gibt das [IDebugProperty2-Objekt](../../../extensibility/debugger/reference/idebugproperty2.md) zurück, das das Ergebnis der Ausdrucksauswertung enthält.

## <a name="return-value"></a>Rückgabewert
Wenn erfolgreich, `S_OK`kehrt zurück; andernfalls wird ein Fehlercode zurückgegeben. Einige typische Fehlercodes sind:

|Fehler|BESCHREIBUNG|
|-----------|-----------------|
|E_EVALUATE_BUSY_WITH_EVALUATION|Ein anderer Ausdruck wird derzeit ausgewertet, und die gleichzeitige Ausdrucksauswertung wird nicht unterstützt.|
|E_EVALUATE_TIMEOUT|Zeitfürst bei der Auswertung.|

## <a name="remarks"></a>Bemerkungen
Für die synchrone Auswertung ist es nicht erforderlich, ein Ereignis nach Abschluss der Auswertung an Visual Studio zurückzusenden.

## <a name="example"></a>Beispiel
Das folgende Beispiel zeigt, wie diese `CExpression` Methode für ein einfaches Objekt implementiert wird, das die [IDebugExpression2-Schnittstelle](../../../extensibility/debugger/reference/idebugexpression2.md) implementiert.

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

## <a name="see-also"></a>Weitere Informationen
- [IDebugExpression2](../../../extensibility/debugger/reference/idebugexpression2.md)
- [EVALFLAGS](../../../extensibility/debugger/reference/evalflags.md)
- [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md)
- [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)
