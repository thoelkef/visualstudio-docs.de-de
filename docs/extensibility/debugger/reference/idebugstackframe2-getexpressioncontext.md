---
title: IDebugStackFrame2::GetExpressionContext | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugStackFrame2::GetExpressionContext
helpviewer_keywords:
- IDebugStackFrame2::GetExpressionContext
ms.assetid: a2604e6a-502d-473b-868f-b11ac64c7a35
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: e9a301bcba6e1fd98e1efbe2c051f2ea27801483
ms.sourcegitcommit: 19ec963ed6d585719cb83ba677434ea6580e0d1f
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/24/2019
ms.locfileid: "66210902"
---
# <a name="idebugstackframe2getexpressioncontext"></a>IDebugStackFrame2::GetExpressionContext
Ruft ein Evaluierungskontext für ausdrucksauswertung im aktuellen Kontext des einen Stapelrahmen und der Thread ab.

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
[out] Gibt eine [IDebugExpressionContext2](../../../extensibility/debugger/reference/idebugexpressioncontext2.md) Objekt, das einen Kontext für die Auswertung des Ausdrucks darstellt.

## <a name="return-value"></a>Rückgabewert
 Wenn erfolgreich, wird `S_OK`ist, andernfalls ein Fehlercode zurückgegeben.

## <a name="remarks"></a>Hinweise
 Im Allgemeinen kann ein ausdrucksauswertungskontext als Bereich für die Durchführung der Auswertung des Ausdrucks betrachtet werden. Rufen Sie die [ParseText](../../../extensibility/debugger/reference/idebugexpressioncontext2-parsetext.md) Methode, um einen Ausdruck zu analysieren, und rufen Sie dann das resultierende [EvaluateSync](../../../extensibility/debugger/reference/idebugexpression2-evaluatesync.md) oder [EvaluateAsync](../../../extensibility/debugger/reference/idebugexpression2-evaluateasync.md) Methoden zum Auswerten des analysierten Ausdrucks.

## <a name="see-also"></a>Siehe auch
- [IDebugStackFrame2](../../../extensibility/debugger/reference/idebugstackframe2.md)
- [IDebugExpressionContext2](../../../extensibility/debugger/reference/idebugexpressioncontext2.md)
- [ParseText](../../../extensibility/debugger/reference/idebugexpressioncontext2-parsetext.md)
- [EvaluateSync](../../../extensibility/debugger/reference/idebugexpression2-evaluatesync.md)
- [EvaluateAsync](../../../extensibility/debugger/reference/idebugexpression2-evaluateasync.md)