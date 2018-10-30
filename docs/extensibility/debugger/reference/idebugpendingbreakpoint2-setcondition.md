---
title: IDebugPendingBreakpoint2::SetCondition | Microsoft-Dokumentation
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IDebugPendingBreakpoint2::SetCondition
helpviewer_keywords:
- SetCondition method
- IDebugPendingBreakpoint2::SetCondition method
ms.assetid: 0534224f-654f-4862-bc4d-a9a81a5f8899
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: ebf6e77292543fe9eebd8f08cf2fd25ef48c7e77
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/23/2018
ms.locfileid: "49886616"
---
# <a name="idebugpendingbreakpoint2setcondition"></a>IDebugPendingBreakpoint2::SetCondition
Legt fest oder ändert die Bedingung, die dem ausstehenden Haltepunkt zugeordnet.  
  
## <a name="syntax"></a>Syntax  
  
```cpp  
HRESULT SetCondition(   
   BP_CONDITION bpCondition  
);  
```  
  
```csharp  
int SetCondition(   
   BP_CONDITION bpCondition  
);  
```  
  
#### <a name="parameters"></a>Parameter  
 `bpCondition`  
 [in] Ein [BP_CONDITION](../../../extensibility/debugger/reference/bp-condition.md) Struktur, die die Bedingung festlegen angibt.  
  
## <a name="return-value"></a>Rückgabewert  
 Wenn erfolgreich, wird `S_OK`ist, andernfalls ein Fehlercode zurückgegeben.  
  
## <a name="remarks"></a>Hinweise  
 Jede Bedingung, die zuvor mit dem ausstehenden Haltepunkt verknüpft war, geht verloren. Alle Breakpoints, die von dieser ausstehenden Haltepunkt gebunden werden aufgerufen, um ihre Bedingung auf die im angegebenen Wert festlegen die `bpCondition` Parameter.  
  
## <a name="see-also"></a>Siehe auch  
 [IDebugPendingBreakpoint2](../../../extensibility/debugger/reference/idebugpendingbreakpoint2.md)   
 [BP_CONDITION](../../../extensibility/debugger/reference/bp-condition.md)