---
title: IDebugExpression2::Abort | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- IDebugExpression2::Abort
helpviewer_keywords:
- IDebugExpression2::Abort
ms.assetid: 4fcb712e-1bdb-4b75-a440-35cc79ee147e
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 668b4fe87bb0c37796d63cb313c15d146c70a58e
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/02/2019
ms.locfileid: "53910593"
---
# <a name="idebugexpression2abort"></a>IDebugExpression2::Abort
Diese Methode bricht den asynchronen ausdrucksauswertung ab, als durch einen Aufruf der [EvaluateAsync](../../../extensibility/debugger/reference/idebugexpression2-evaluateasync.md) Methode.  
  
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
 Wenn erfolgreich, wird `S_OK`ist, andernfalls ein Fehlercode zurückgegeben.  
  
## <a name="remarks"></a>Hinweise  
 Asynchrone ausdrucksauswertung abgebrochen wird, werden nicht gesendet, wenn ein [IDebugExpressionEvaluationCompleteEvent2](../../../extensibility/debugger/reference/idebugexpressionevaluationcompleteevent2.md) Ereignis an den Ereignisrückruf übergeben wird, um die [Anfügen](../../../extensibility/debugger/reference/idebugprogram2-attach.md) oder [Anfügen](../../../extensibility/debugger/reference/idebugengine2-attach.md) Methoden.  
  
## <a name="see-also"></a>Siehe auch  
 [IDebugExpression2](../../../extensibility/debugger/reference/idebugexpression2.md)   
 [IDebugExpressionEvaluationCompleteEvent2](../../../extensibility/debugger/reference/idebugexpressionevaluationcompleteevent2.md)   
 [EvaluateAsync](../../../extensibility/debugger/reference/idebugexpression2-evaluateasync.md)