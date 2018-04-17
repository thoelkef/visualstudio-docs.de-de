---
title: IDebugThread2::GetLogicalThread | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IDebugThread2::GetLogicalThread
helpviewer_keywords:
- IDebugThread2::GetLogicalThread
ms.assetid: bce6230e-41d4-49b7-a050-2dde5efb6805
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: ab093cb4ca4760737f8216452cfde7340b0329fd
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/16/2018
---
# <a name="idebugthread2getlogicalthread"></a>IDebugThread2::GetLogicalThread
Debugmodule implementieren Sie diese Methode nicht.  
  
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
 [out] Gibt eine `IDebugLogicalThread2` Schnittstelle, die den zugeordneten logischen Thread darstellt. Eine Implementierung der Debug-Modul sollte dies auf einen null-Wert festgelegt.  
  
## <a name="return-value"></a>Rückgabewert  
 Debuggen Modul Implementierungen immer return `E_NOTIMPL`.  
  
## <a name="see-also"></a>Siehe auch  
 [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md)