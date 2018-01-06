---
title: IDebugBoundBreakpoint2::SetCondition | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: IDebugBoundBreakpoint2::SetCondition
helpviewer_keywords:
- SetCondition method
- IDebugBoundBreakpoint2::SetCondition method
ms.assetid: 5d366876-efed-43d0-8ea1-dfdb009cbfac
caps.latest.revision: "11"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 88cfedfd31532750d9db4fd00f43e507e6812e2b
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/22/2017
---
# <a name="idebugboundbreakpoint2setcondition"></a>IDebugBoundBreakpoint2::SetCondition
Legt fest oder ändert die Bedingung dieser gebundenen Haltepunkt zugeordnet.  
  
## <a name="syntax"></a>Syntax  
  
```cpp  
HRESULT SetCondition(   
   BP_CONDITION bpCondition  
);  
```  
  
```csharp  
int SetCondition(   
   enum_BP_CONDITION bpCondition  
);  
```  
  
#### <a name="parameters"></a>Parameter  
 `bpCondition`  
 [in] Ein Wert aus der [BP_CONDITION](../../../extensibility/debugger/reference/bp-condition.md) -Enumeration, die die Bedingung beschreibt.  
  
## <a name="return-value"></a>Rückgabewert  
 Im Erfolgsfall gibt `S_OK`ist, andernfalls wird ein Fehlercode zurückgegeben. Gibt `E_BP_DELETED` , wenn der Zustand des Objekts gebundenen Haltepunkt, um festgelegt ist `BPS_DELETED` (Teil der [BP_STATE](../../../extensibility/debugger/reference/bp-state.md) Enumeration).  
  
## <a name="remarks"></a>Hinweise  
 Jede Bedingung, die zuvor diesem Breakpoint zugeordnet war, geht verloren.  
  
## <a name="see-also"></a>Siehe auch  
 [IDebugBoundBreakpoint2](../../../extensibility/debugger/reference/idebugboundbreakpoint2.md)   
 [BP_CONDITION](../../../extensibility/debugger/reference/bp-condition.md)   
 [BP_STATE](../../../extensibility/debugger/reference/bp-state.md)