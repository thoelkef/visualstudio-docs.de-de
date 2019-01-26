---
title: IDebugThread2::Suspend | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- IDebugThread2::Suspend
helpviewer_keywords:
- IDebugThread2::Suspend
ms.assetid: 1e20be85-aa12-48de-bb83-0bf0976e99ae
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 74d7214b8cc70f8fc844410cb22842ab4eea15e1
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/26/2019
ms.locfileid: "55069737"
---
# <a name="idebugthread2suspend"></a>IDebugThread2::Suspend
Hält einen Thread.  
  
## <a name="syntax"></a>Syntax  
  
```cpp  
HRESULT Suspend (   
   DWORD *pdwSuspendCount  
);  
```  
  
```csharp  
HRESULT Suspend (   
   out uint pdwSuspendCount  
);  
```  
  
#### <a name="parameters"></a>Parameter  
 `pdwSuspendCount`  
 [out] Gibt den Unterbrechungszähler nach dem Vorgang "Anhalten" zurück.  
  
## <a name="return-value"></a>Rückgabewert  
 Wenn erfolgreich, wird `S_OK`ist, andernfalls ein Fehlercode zurückgegeben.  
  
## <a name="remarks"></a>Hinweise  
 Jeder Aufruf dieser Methode inkrementiert den Unterbrechungszähler über 0. Diese Unterbrechungszähler wird angezeigt, der **Threads** Debug-Fenster.  
  
 Bei jedem Aufruf dieser Methode, muss ein späterer Aufruf von der [fortsetzen](../../../extensibility/debugger/reference/idebugthread2-resume.md) Methode.  
  
## <a name="see-also"></a>Siehe auch  
 [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md)   
 [Resume](../../../extensibility/debugger/reference/idebugthread2-resume.md)