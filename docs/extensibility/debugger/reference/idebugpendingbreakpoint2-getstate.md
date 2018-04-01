---
title: IDebugPendingBreakpoint2::GetState | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- IDebugPendingBreakpoint2::GetState
helpviewer_keywords:
- GetState method
- IDebugPendingBreakpoint2::GetState method
ms.assetid: e88d543f-2e83-4ba7-86ca-f874e39955ff
caps.latest.revision: 10
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload:
- vssdk
ms.openlocfilehash: 7a9f420bfd36fed7fcc3f239e5610a34e63b52a6
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/22/2017
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
 [in, out] Ein [PENDING_BP_STATE_INFO](../../../extensibility/debugger/reference/pending-bp-state-info.md) -Struktur, die mit einer Beschreibung dieser ausstehender Haltepunkt ausgefüllt ist.  
  
## <a name="return-value"></a>Rückgabewert  
 Im Erfolgsfall gibt `S_OK`ist, andernfalls wird ein Fehlercode zurückgegeben.  
  
## <a name="see-also"></a>Siehe auch  
 [IDebugPendingBreakpoint2](../../../extensibility/debugger/reference/idebugpendingbreakpoint2.md)   
 [PENDING_BP_STATE_INFO](../../../extensibility/debugger/reference/pending-bp-state-info.md)