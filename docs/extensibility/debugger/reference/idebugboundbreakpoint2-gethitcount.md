---
title: "IDebugBoundBreakpoint2::GetHitCount | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugBoundBreakpoint2::GetHitCount"
helpviewer_keywords: 
  - "GetHitCount-Methode"
  - "IDebugBoundBreakpoint2::GetHitCount-Methode"
ms.assetid: 23481f37-047c-41d2-8286-4da1f4084961
caps.latest.revision: 10
caps.handback.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
---
# IDebugBoundBreakpoint2::GetHitCount
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Ruft die aktuelle Trefferanzahl für diese Bindung Haltepunkt ab.  
  
## Syntax  
  
```cpp#  
HRESULT GetHitCount(   
   DWORD* pdwHitCount  
);  
```  
  
```c#  
int GetHitCount(   
   out uint pdwHitCount  
);  
```  
  
#### Parameter  
 `pdwHitCount`  
 \[out\]  Gibt die Trefferanzahl zurück.  
  
## Rückgabewert  
 Bei Erfolg gibt `S_OK`zurück. andernfalls gibt einen Fehlercode zurück.  Gibt `E_BP_DELETED` zurück, wenn sich der Zustand des Objekts `BPS_DELETED` gebundenen Haltepunkt festgelegt ist \(Teil der [BP\_STATE](../../../extensibility/debugger/reference/bp-state.md)\-Enumeration\).  
  
## Hinweise  
 Die Trefferanzahl ist, wieoft dieser Haltepunkt während der aktuelle Reihe der Sitzung ausgelöst hat.  
  
## Siehe auch  
 [IDebugBoundBreakpoint2](../../../extensibility/debugger/reference/idebugboundbreakpoint2.md)   
 [BP\_STATE](../../../extensibility/debugger/reference/bp-state.md)