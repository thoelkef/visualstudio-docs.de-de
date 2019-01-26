---
title: IDebugThread2::GetLogicalThread | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- IDebugThread2::GetLogicalThread
helpviewer_keywords:
- IDebugThread2::GetLogicalThread
ms.assetid: bce6230e-41d4-49b7-a050-2dde5efb6805
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 0034daecab2543d9a48a627a26a88ee84a872f73
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/25/2019
ms.locfileid: "54945930"
---
# <a name="idebugthread2getlogicalthread"></a>IDebugThread2::GetLogicalThread
Debug-Engines implementieren Sie diese Methode nicht.  
  
## <a name="syntax"></a>Syntax  
  
```cpp  
HRESULT GetLogicalThread(   
   IDebugStackFrame2*     pStackFrame,  
   IDebugLogicalThread2** ppLogicalThread  
);  
```  
  
```csharp  
int GetLogicalThread(   
   IDebugStackFrame2        pStackFrame,  
   out IDebugLogicalThread2 ppLogicalThread  
);  
```  
  
#### <a name="parameters"></a>Parameter  
 `pStackFrame`  
 [in] Ein [IDebugStackFrame2](../../../extensibility/debugger/reference/idebugstackframe2.md) Objekt, das den Stapelrahmen darstellt.  
  
 `ppLogicalThread`  
 [out] Gibt eine `IDebugLogicalThread2` Schnittstelle, die den zugeordneten logischen Thread darstellt. Eine Implementierung der Debug-Engine sollte dies auf einen null-Wert festgelegt.  
  
## <a name="return-value"></a>Rückgabewert  
 Debug-Engine-Implementierungen immer return `E_NOTIMPL`.  
  
## <a name="see-also"></a>Siehe auch  
 [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md)