---
title: "IDebugBoundBreakpoint2::SetPassCount | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugBoundBreakpoint2::SetPassCount"
helpviewer_keywords: 
  - "SetPassCount-Methode"
  - "IDebugBoundBreakpoint2::SetPassCount-Methode"
ms.assetid: b32c12f9-b34d-43bd-a1b9-61af6cf8e51b
caps.latest.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 10
---
# IDebugBoundBreakpoint2::SetPassCount
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Anzahl der Änderungen übergeben oder legt diese fest, die mit diesem gebundenen Haltepunkt.  
  
## Syntax  
  
```cpp#  
HRESULT SetPassCount(   
   BP_PASSCOUNT bpPassCount  
);  
```  
  
```c#  
int SetPassCount(   
   BP_PASSCOUNT bpPassCount  
);  
```  
  
#### Parameter  
 `bpPassCount`  
 \[in\]  Die [BP\_PASSCOUNT](../../../extensibility/debugger/reference/bp-passcount.md) gültige Struktur, die die Anzahl angibt.  
  
## Rückgabewert  
 Bei Erfolg gibt `S_OK`zurück. andernfalls gibt einen Fehlercode zurück.  Gibt `E_BP_DELETED` zurück, wenn sich der Zustand des Objekts `BPS_DELETED` gebundenen Haltepunkt festgelegt ist \(Teil der [BP\_STATE](../../../extensibility/debugger/reference/bp-state.md)\-Enumeration\).  
  
## Hinweise  
 Die Anzahl der gültige bestimmt, wann der Haltepunkt ausgelöst wird.  Die aktuelle Phase oder die Trefferanzahl können abgerufen werden, indem die [GetHitCount](../../../extensibility/debugger/reference/idebugboundbreakpoint2-gethitcount.md)\-Methode aufruft.  
  
 Jede gültige Anzahl der zuvor mit diesem Haltepunkt zugeordnet wurde, geht verloren.  
  
## Siehe auch  
 [IDebugBoundBreakpoint2](../../../extensibility/debugger/reference/idebugboundbreakpoint2.md)   
 [GetHitCount](../../../extensibility/debugger/reference/idebugboundbreakpoint2-gethitcount.md)   
 [BP\_PASSCOUNT](../../../extensibility/debugger/reference/bp-passcount.md)   
 [BP\_STATE](../../../extensibility/debugger/reference/bp-state.md)