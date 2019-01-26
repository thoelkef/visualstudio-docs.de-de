---
title: IDebugPendingBreakpoint2::SetPassCount | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- IDebugPendingBreakpoint2::SetPassCount
helpviewer_keywords:
- SetPassCount method
- IDebugPendingBreakpoint2::SetPassCount method
ms.assetid: 08ddd328-57eb-42e0-baa9-8424dcd1bf04
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 31041067466d181d631cdce776db06810b3690a8
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/25/2019
ms.locfileid: "54989691"
---
# <a name="idebugpendingbreakpoint2setpasscount"></a>IDebugPendingBreakpoint2::SetPassCount
Legt fest oder ändert die Anzahl der Durchläufe dem ausstehenden Haltepunkt zugeordnet.  
  
## <a name="syntax"></a>Syntax  
  
```cpp  
HRESULT SetPassCount(   
   BP_PASSCOUNT bpPassCount  
);  
```  
  
```csharp  
int SetPassCount(   
   BP_PASSCOUNT bpPassCount  
);  
```  
  
#### <a name="parameters"></a>Parameter  
 `bpPassCount`  
 [in] Ein [BP_PASSCOUNT](../../../extensibility/debugger/reference/bp-passcount.md) Struktur, die Anzahl der Durchläufe enthält.  
  
## <a name="return-value"></a>Rückgabewert  
 Wenn erfolgreich, wird `S_OK`ist, andernfalls ein Fehlercode zurückgegeben. Gibt `E_BP_DELETED` , wenn der Haltepunkt gelöscht wurde.  
  
## <a name="remarks"></a>Hinweise  
 Alle Pass-Anzahl, die zuvor mit dem ausstehenden Haltepunkt verknüpft war, geht verloren. Alle Breakpoints, die von dieser ausstehenden Haltepunkt gebunden werden aufgerufen, um die Anzahl der Durchläufe für die Verwendung der `bpPassCount` Parameter.  
  
## <a name="see-also"></a>Siehe auch  
 [IDebugPendingBreakpoint2](../../../extensibility/debugger/reference/idebugpendingbreakpoint2.md)   
 [BP_PASSCOUNT](../../../extensibility/debugger/reference/bp-passcount.md)