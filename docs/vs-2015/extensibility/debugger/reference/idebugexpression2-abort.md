---
title: 'IDebugExpression2:: Abort | Microsoft-Dokumentation'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugExpression2::Abort
helpviewer_keywords:
- IDebugExpression2::Abort
ms.assetid: 4fcb712e-1bdb-4b75-a440-35cc79ee147e
caps.latest.revision: 12
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 8019d811f07373ba86059236013da645ff82c42a
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "68163770"
---
# <a name="idebugexpression2abort"></a>IDebugExpression2::Abort
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Diese Methode bricht die asynchrone Ausdrucks Auswertung ab, wie durch einen-Aufrufvorgang der [evaluateasync](../../../extensibility/debugger/reference/idebugexpression2-evaluateasync.md) -Methode gestartet.  
  
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
 Wenn die Ausführung erfolgreich ist, wird `S_OK`, andernfalls ein Fehlercode zurückgegeben.  
  
## <a name="remarks"></a>Bemerkungen  
 Wenn die asynchrone Ausdrucks Auswertung abgebrochen wird, senden Sie kein [IDebugExpressionEvaluationCompleteEvent2](../../../extensibility/debugger/reference/idebugexpressionevaluationcompleteevent2.md) -Ereignis an den Ereignis Rückruf, der an die [Attach](../../../extensibility/debugger/reference/idebugprogram2-attach.md) -oder [Attach](../../../extensibility/debugger/reference/idebugengine2-attach.md) -Methoden übermittelt wurde.  
  
## <a name="see-also"></a>Weitere Informationen  
 [IDebugExpression2](../../../extensibility/debugger/reference/idebugexpression2.md)   
 [IDebugExpressionEvaluationCompleteEvent2](../../../extensibility/debugger/reference/idebugexpressionevaluationcompleteevent2.md)   
 [EvaluateAsync](../../../extensibility/debugger/reference/idebugexpression2-evaluateasync.md)
