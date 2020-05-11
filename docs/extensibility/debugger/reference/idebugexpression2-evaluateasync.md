---
title: IDebugExpression2::EvaluateAsync | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugExpression2::EvaluateAsync
helpviewer_keywords:
- IDebugExpression2::EvaluateAsync
ms.assetid: 848fe6cb-0759-42f2-890b-d2b551c527d6
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 2cd1eba56f8e3c5a1a779acc3330790e9ba2bc96
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/06/2020
ms.locfileid: "80729752"
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

## <a name="parameters"></a>Parameter
`dwFlags`\
[in] Eine Kombination von Flags aus der EVALFLAGS-Enumeration, die die Ausdrucksauswertung steuern. [EVALFLAGS](../../../extensibility/debugger/reference/evalflags.md)

`pExprCallback`\
[in] Dieser Parameter ist immer ein NULL-Wert.

## <a name="return-value"></a>Rückgabewert
Wenn erfolgreich, `S_OK`kehrt zurück; andernfalls wird ein Fehlercode zurückgegeben. Ein typischer Fehlercode ist:

|Fehler|BESCHREIBUNG|
|-----------|-----------------|
|E_EVALUATE_BUSY_WITH_EVALUATION|Ein anderer Ausdruck wird derzeit ausgewertet, und die gleichzeitige Ausdrucksauswertung wird nicht unterstützt.|

## <a name="remarks"></a>Bemerkungen
Diese Methode sollte sofort nach dem Start der Ausdrucksauswertung zurückgegeben werden. Wenn der Ausdruck erfolgreich ausgewertet wurde, muss ein [IDebugExpressionEvaluationCompleteEvent2](../../../extensibility/debugger/reference/idebugexpressionevaluationcompleteevent2.md) an den [IDebugEventCallback2-Ereignisrückruf](../../../extensibility/debugger/reference/idebugeventcallback2.md) gesendet werden, wie über [Attach](../../../extensibility/debugger/reference/idebugprogram2-attach.md) oder [Attach](../../../extensibility/debugger/reference/idebugengine2-attach.md)bereitgestellt.

## <a name="example"></a>Beispiel
Das folgende Beispiel zeigt, wie diese `CExpression` Methode für ein einfaches Objekt implementiert wird, das die [IDebugExpression2-Schnittstelle](../../../extensibility/debugger/reference/idebugexpression2.md) implementiert.

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

## <a name="see-also"></a>Weitere Informationen
- [IDebugExpression2](../../../extensibility/debugger/reference/idebugexpression2.md)
- [IDebugExpressionEvaluationCompleteEvent2](../../../extensibility/debugger/reference/idebugexpressionevaluationcompleteevent2.md)
- [EVALFLAGS](../../../extensibility/debugger/reference/evalflags.md)
- [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md)
