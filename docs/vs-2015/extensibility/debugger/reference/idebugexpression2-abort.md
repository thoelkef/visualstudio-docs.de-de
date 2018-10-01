---
title: IDebugExpression2::Abort | Microsoft-Dokumentation
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
- IDebugExpression2::Abort
helpviewer_keywords:
- IDebugExpression2::Abort
ms.assetid: 4fcb712e-1bdb-4b75-a440-35cc79ee147e
caps.latest.revision: 12
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: b71c5b2eb997352fc853484304c57562d72ecdae
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/22/2018
ms.locfileid: "47523139"
---
# <a name="idebugexpression2abort"></a>IDebugExpression2::Abort
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Die neueste Version dieses Themas finden Sie unter [IDebugExpression2::Abort](https://docs.microsoft.com/visualstudio/extensibility/debugger/reference/idebugexpression2-abort).  
  
Diese Methode bricht den asynchronen ausdrucksauswertung ab, als durch einen Aufruf der [EvaluateAsync](../../../extensibility/debugger/reference/idebugexpression2-evaluateasync.md) Methode.  
  
## <a name="syntax"></a>Syntax  
  
```cpp#  
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

