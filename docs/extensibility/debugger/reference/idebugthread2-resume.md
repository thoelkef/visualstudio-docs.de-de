---
title: IDebugThread2::Resume | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- IDebugThread2::Resume
helpviewer_keywords:
- IDebugThread2::Resume
ms.assetid: 36aad682-b0b9-40a2-b3fc-f0e61d41cdbc
caps.latest.revision: 10
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload:
- vssdk
ms.openlocfilehash: 5de844c3b07a509f266e2f9d278d1f78bea2b089
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/22/2017
---
# <a name="idebugthread2resume"></a>IDebugThread2::Resume
Setzt die Ausführung eines Threads.  
  
## <a name="syntax"></a>Syntax  
  
```cpp  
HRESULT Resume (   
   DWORD *pdwSuspendCount  
);  
```  
  
```csharp  
int Resume (   
   out uint pdwSuspendCount  
);  
```  
  
#### <a name="parameters"></a>Parameter  
 `pdwSuspendCount`  
 [out] Gibt zurück, den Unterbrechungszähler nach Abschluss des Vorgangs fortsetzen.  
  
## <a name="return-value"></a>Rückgabewert  
 Im Erfolgsfall gibt `S_OK`ist, andernfalls wird ein Fehlercode zurückgegeben.  
  
## <a name="remarks"></a>Hinweise  
 Jeder Aufruf von dieser Methode dekrementiert den Unterbrechungszähler bis zu diesem Zeitpunkt 0 erreicht, wird tatsächlich die Ausführung fortgesetzt. Diese Unterbrechungszähler wird angezeigt, der **Threads** Debug-Fenster.  
  
 Für jeden Aufruf dieser Methode muss ein vorherigen Aufruf der [Suspend](../../../extensibility/debugger/reference/idebugthread2-suspend.md) Methode. Der Unterbrechungszähler bestimmt, wie oft die `IDebugThread2::Suspend` bisher-Methode aufgerufen wurde.  
  
## <a name="see-also"></a>Siehe auch  
 [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md)   
 [Suspend](../../../extensibility/debugger/reference/idebugthread2-suspend.md)