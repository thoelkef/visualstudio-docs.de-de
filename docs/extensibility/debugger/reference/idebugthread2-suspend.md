---
title: IDebugThread2::Suspend | Microsoft-Dokumentation
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IDebugThread2::Suspend
helpviewer_keywords:
- IDebugThread2::Suspend
ms.assetid: 1e20be85-aa12-48de-bb83-0bf0976e99ae
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 9da385dc9f50ec66b45df1c9955f338a6c550467
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/23/2018
ms.locfileid: "49905401"
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