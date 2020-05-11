---
title: IDebugStackFrame2::GetExpressionContext | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugStackFrame2::GetExpressionContext
helpviewer_keywords:
- IDebugStackFrame2::GetExpressionContext
ms.assetid: a2604e6a-502d-473b-868f-b11ac64c7a35
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: fb1a075d04ed53fdbe2181975a56eddfcbc3b683
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/06/2020
ms.locfileid: "80719742"
---
# <a name="idebugstackframe2getexpressioncontext"></a>IDebugStackFrame2::GetExpressionContext
Ruft einen Auswertungskontext für die Ausdrucksauswertung im aktuellen Kontext eines Stapelrahmens und Threads ab.

## <a name="syntax"></a>Syntax

```cpp
HRESULT GetExpressionContext ( 
   IDebugExpressionContext2** ppExprCxt
);
```

```csharp
int GetExpressionContext ( 
   out IDebugExpressionContext2 ppExprCxt
);
```

## <a name="parameters"></a>Parameter
`ppExprCxt`\
[out] Gibt ein [IDebugExpressionContext2-Objekt](../../../extensibility/debugger/reference/idebugexpressioncontext2.md) zurück, das einen Kontext für die Ausdrucksauswertung darstellt.

## <a name="return-value"></a>Rückgabewert
 Wenn die Ausführung erfolgreich ist, wird `S_OK`, andernfalls ein Fehlercode zurückgegeben.

## <a name="remarks"></a>Bemerkungen
 Im Allgemeinen kann ein Ausdrucksauswertungskontext als Einsenderaum für die Ausdrucksauswertung betrachtet werden. Rufen Sie die [ParseText-Methode](../../../extensibility/debugger/reference/idebugexpressioncontext2-parsetext.md) auf, um einen Ausdruck zu analysieren, und rufen Sie dann die resultierenden [EvaluateSync-](../../../extensibility/debugger/reference/idebugexpression2-evaluatesync.md) oder [EvaluateAsync-Methoden](../../../extensibility/debugger/reference/idebugexpression2-evaluateasync.md) auf, um den analysierten Ausdruck auszuwerten.

## <a name="see-also"></a>Weitere Informationen
- [IDebugStackFrame2](../../../extensibility/debugger/reference/idebugstackframe2.md)
- [IDebugExpressionContext2](../../../extensibility/debugger/reference/idebugexpressioncontext2.md)
- [ParseText](../../../extensibility/debugger/reference/idebugexpressioncontext2-parsetext.md)
- [EvaluateSync](../../../extensibility/debugger/reference/idebugexpression2-evaluatesync.md)
- [EvaluateAsync](../../../extensibility/debugger/reference/idebugexpression2-evaluateasync.md)
