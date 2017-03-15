---
title: "IDebugBoundBreakpoint2::SetHitCount | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugBoundBreakpoint2::SetHitCount"
helpviewer_keywords: 
  - "SetHitCount-Methode"
  - "IDebugBoundBreakpoint2::SetHitCount-Methode"
ms.assetid: 8145d875-26b1-4049-a2a2-e7d3d7f4735f
caps.latest.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 10
---
# IDebugBoundBreakpoint2::SetHitCount
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Legt die Trefferanzahl für den gebundenen Haltepunkt fest.  
  
## Syntax  
  
```cpp#  
HRESULT SetHitCount(   
   DWORD dwHitCount  
);  
```  
  
```c#  
int SetHitCount(   
   uint dwHitCount  
);  
```  
  
#### Parameter  
 `dwHitCount`  
 \[in\]  Die Trefferanzahl, der festgelegt werden soll.  
  
## Rückgabewert  
 Bei Erfolg gibt `S_OK`zurück. andernfalls gibt einen Fehlercode zurück.  Gibt `E_BP_DELETED` zurück, wenn sich der Zustand des Objekts `BPS_DELETED` gebundenen Haltepunkt festgelegt ist \(Teil der [BP\_STATE](../../../extensibility/debugger/reference/bp-state.md)\-Enumeration\).  
  
## Hinweise  
 Die Trefferanzahl ist, wieoft dieser Haltepunkt während der aktuelle Reihe der Sitzung ausgelöst hat.  
  
 Diese Methode wird in der Regel durch das Debugmodul aufgerufen, um die aktuelle Trefferanzahl auf diesem Haltepunkt zu aktualisieren.  
  
## Siehe auch  
 [IDebugBoundBreakpoint2](../../../extensibility/debugger/reference/idebugboundbreakpoint2.md)   
 [BP\_STATE](../../../extensibility/debugger/reference/bp-state.md)