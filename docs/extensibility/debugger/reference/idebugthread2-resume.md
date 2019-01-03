---
title: IDebugThread2::Resume | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- IDebugThread2::Resume
helpviewer_keywords:
- IDebugThread2::Resume
ms.assetid: 36aad682-b0b9-40a2-b3fc-f0e61d41cdbc
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: bad2daaa21607194504923db8e896237298c75d5
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/02/2019
ms.locfileid: "53824586"
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
 [out] Gibt den Unterbrechungszähler nach der Wiederaufnahme des Vorgangs zurück.  
  
## <a name="return-value"></a>Rückgabewert  
 Wenn erfolgreich, wird `S_OK`ist, andernfalls ein Fehlercode zurückgegeben.  
  
## <a name="remarks"></a>Hinweise  
 Jeder Aufruf von verringert diese Methode den Unterbrechungszähler bis zu diesem Zeitpunkt 0 erreicht, wird tatsächlich Ausführung fortgesetzt. Diese Unterbrechungszähler wird angezeigt, der **Threads** Debug-Fenster.  
  
 Bei jedem Aufruf dieser Methode, muss ein vorherigen Aufruf der [Suspend](../../../extensibility/debugger/reference/idebugthread2-suspend.md) Methode. Der Unterbrechungszähler bestimmt, wie oft die `IDebugThread2::Suspend` bisher Methode aufgerufen wurde.  
  
## <a name="see-also"></a>Siehe auch  
 [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md)   
 [Suspend](../../../extensibility/debugger/reference/idebugthread2-suspend.md)