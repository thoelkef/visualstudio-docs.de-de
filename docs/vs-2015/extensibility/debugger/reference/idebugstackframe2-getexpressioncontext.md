---
title: IDebugStackFrame2::GetExpressionContext | Microsoft-Dokumentation
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- IDebugStackFrame2::GetExpressionContext
helpviewer_keywords:
- IDebugStackFrame2::GetExpressionContext
ms.assetid: a2604e6a-502d-473b-868f-b11ac64c7a35
caps.latest.revision: 11
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 1343118b86325225a499b7caf6d19c31cc84532d
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/22/2018
ms.locfileid: "47514235"
---
# <a name="idebugstackframe2getexpressioncontext"></a>IDebugStackFrame2::GetExpressionContext
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Die neueste Version dieses Themas finden Sie unter [IDebugStackFrame2::GetExpressionContext](https://docs.microsoft.com/visualstudio/extensibility/debugger/reference/idebugstackframe2-getexpressioncontext).  
  
Ruft ein Evaluierungskontext für ausdrucksauswertung im aktuellen Kontext des einen Stapelrahmen und der Thread ab.  
  
## <a name="syntax"></a>Syntax  
  
```cpp#  
HRESULT GetExpressionContext (   
   IDebugExpressionContext2** ppExprCxt  
);  
```  
  
```csharp  
int GetExpressionContext (   
   out IDebugExpressionContext2 ppExprCxt  
);  
```  
  
#### <a name="parameters"></a>Parameter  
 `ppExprCxt`  
 [out] Gibt eine [IDebugExpressionContext2](../../../extensibility/debugger/reference/idebugexpressioncontext2.md) Objekt, das einen Kontext für die Auswertung des Ausdrucks darstellt.  
  
## <a name="return-value"></a>Rückgabewert  
 Wenn erfolgreich, wird `S_OK`ist, andernfalls ein Fehlercode zurückgegeben.  
  
## <a name="remarks"></a>Hinweise  
 Im Allgemeinen kann ein ausdrucksauswertungskontext als Bereich für die Durchführung der Auswertung des Ausdrucks betrachtet werden. Rufen Sie die [ParseText](../../../extensibility/debugger/reference/idebugexpressioncontext2-parsetext.md) Methode, um einen Ausdruck zu analysieren, und rufen Sie dann das resultierende [EvaluateSync](../../../extensibility/debugger/reference/idebugexpression2-evaluatesync.md) oder [EvaluateAsync](../../../extensibility/debugger/reference/idebugexpression2-evaluateasync.md) Methoden zum Auswerten des analysierten Ausdrucks.  
  
## <a name="see-also"></a>Siehe auch  
 [IDebugStackFrame2](../../../extensibility/debugger/reference/idebugstackframe2.md)   
 [IDebugExpressionContext2](../../../extensibility/debugger/reference/idebugexpressioncontext2.md)   
 [ParseText](../../../extensibility/debugger/reference/idebugexpressioncontext2-parsetext.md)   
 [EvaluateSync](../../../extensibility/debugger/reference/idebugexpression2-evaluatesync.md)   
 [EvaluateAsync](../../../extensibility/debugger/reference/idebugexpression2-evaluateasync.md)

