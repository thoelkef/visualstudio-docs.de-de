---
title: IDebugPendingBreakpoint2::GetState | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- IDebugPendingBreakpoint2::GetState
helpviewer_keywords:
- GetState method
- IDebugPendingBreakpoint2::GetState method
ms.assetid: e88d543f-2e83-4ba7-86ca-f874e39955ff
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 1998c6dd747e7c3968c238e617cec7e152c9f974
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/02/2019
ms.locfileid: "53903564"
---
# <a name="idebugpendingbreakpoint2getstate"></a>IDebugPendingBreakpoint2::GetState
Ruft den Status des ausstehenden Haltepunkts ab.  
  
## <a name="syntax"></a>Syntax  
  
```cpp  
HRESULT GetState(   
   PENDING_BP_STATE_INFO* pState  
);  
```  
  
```csharp  
int GetState(   
   PENDING_BP_STATE_INFO[] pState  
);  
```  
  
#### <a name="parameters"></a>Parameter  
 `pState`  
 [in, out] Ein [PENDING_BP_STATE_INFO](../../../extensibility/debugger/reference/pending-bp-state-info.md) -Struktur, die mit der eine Beschreibung dieser ausstehenden Haltepunkt gefüllt wird.  
  
## <a name="return-value"></a>Rückgabewert  
 Wenn erfolgreich, wird `S_OK`ist, andernfalls ein Fehlercode zurückgegeben.  
  
## <a name="see-also"></a>Siehe auch  
 [IDebugPendingBreakpoint2](../../../extensibility/debugger/reference/idebugpendingbreakpoint2.md)   
 [PENDING_BP_STATE_INFO](../../../extensibility/debugger/reference/pending-bp-state-info.md)