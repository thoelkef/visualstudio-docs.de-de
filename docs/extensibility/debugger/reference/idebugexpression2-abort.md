---
title: IDebugExpression2::Abbruch | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugExpression2::Abort
helpviewer_keywords:
- IDebugExpression2::Abort
ms.assetid: 4fcb712e-1bdb-4b75-a440-35cc79ee147e
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 5de2e34a8ae1e038c2109627099dacc5bd03a1ac
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/06/2020
ms.locfileid: "80729773"
---
# <a name="idebugexpression2abort"></a>IDebugExpression2::Abort
Diese Methode bricht die asynchrone Ausdrucksauswertung ab, die durch einen Aufruf der [EvaluateAsync-Methode](../../../extensibility/debugger/reference/idebugexpression2-evaluateasync.md) gestartet wird.

## <a name="syntax"></a>Syntax

```cpp
HRESULT Abort(
   void
);
```

```csharp
int Abort();
```

## <a name="return-value"></a>Rückgabewert
 Wenn die Ausführung erfolgreich ist, wird `S_OK`, andernfalls ein Fehlercode zurückgegeben.

## <a name="remarks"></a>Bemerkungen
 Wenn die Asynchronexpressionauswertung abgebrochen wird, senden Sie kein [IDebugExpressionEvaluationCompleteEvent2-Ereignis](../../../extensibility/debugger/reference/idebugexpressionevaluationcompleteevent2.md) an den Ereignisrückruf, der an die [Attach-](../../../extensibility/debugger/reference/idebugprogram2-attach.md) oder [Attach-Methoden](../../../extensibility/debugger/reference/idebugengine2-attach.md) übergeben wird.

## <a name="see-also"></a>Weitere Informationen
- [IDebugExpression2](../../../extensibility/debugger/reference/idebugexpression2.md)
- [IDebugExpressionEvaluationCompleteEvent2](../../../extensibility/debugger/reference/idebugexpressionevaluationcompleteevent2.md)
- [EvaluateAsync](../../../extensibility/debugger/reference/idebugexpression2-evaluateasync.md)
