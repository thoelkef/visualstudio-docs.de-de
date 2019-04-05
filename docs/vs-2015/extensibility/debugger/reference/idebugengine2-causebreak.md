---
title: IDebugEngine2::CauseBreak | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugEngine2::CauseBreak
helpviewer_keywords:
- IDebugEngine2::CauseBreak
ms.assetid: 17fe4698-b04e-4798-8412-80e0da60c387
caps.latest.revision: 9
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 2b6e52e4885a61c3fe04fff5bdcca08fd00cf460
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/23/2019
ms.locfileid: "58960014"
---
# <a name="idebugengine2causebreak"></a>IDebugEngine2::CauseBreak
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Fordert an, dass alle Programme, die von der Debug-Engine (DE), um die Ausführung der nächsten beenden gedebuggt wird versucht, dass einer ihrer Threads ausführen.  
  
## <a name="syntax"></a>Syntax  
  
```cpp#  
HRESULT CauseBreak(   
   void   
);  
```  
  
```csharp  
int CauseBreak();  
```  
  
## <a name="return-value"></a>Rückgabewert  
 Wenn erfolgreich, wird `S_OK`ist, andernfalls ein Fehlercode zurückgegeben.  
  
## <a name="remarks"></a>Hinweise  
 Diese Methode ist asynchron: ein [IDebugBreakEvent2](../../../extensibility/debugger/reference/idebugbreakevent2.md) Ereignis wird immer dann gesendet, wenn Sie als Nächstes versucht das Programm ausgeführt wird, nachdem diese Methode aufgerufen wird.  
  
## <a name="see-also"></a>Siehe auch  
 [CauseBreak](../../../extensibility/debugger/reference/idebugprogram2-causebreak.md)   
 [IDebugEngine2](../../../extensibility/debugger/reference/idebugengine2.md)
