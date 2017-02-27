---
title: "IDebugBreakpointEvent2::EnumBreakpoints | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugBreakpointEvent2:::EnumBreakpoints"
helpviewer_keywords: 
  - "IDebugBreakpointEvent2:::EnumBreakpoints"
ms.assetid: 606a9625-ee43-4e84-9a47-af9a50d2d005
caps.latest.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 10
---
# IDebugBreakpointEvent2::EnumBreakpoints
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Erstellt einen Enumerator für alle Haltepunkte, die am aktuellen Speicherort des Codes ausgelöst hat.  
  
## Syntax  
  
```cpp#  
HRESULT EnumBreakpoints(  
  IEnumDebugBoundBreakpoints2** ppEnum  
);  
```  
  
```c#  
int EnumBreakpoints(  
  out IEnumDebugBoundBreakpoints2 ppEnum  
);  
```  
  
#### Parameter  
 `ppEnum`  
 \[out\]  Gibt ein [IEnumDebugBoundBreakpoints2](../../../extensibility/debugger/reference/ienumdebugboundbreakpoints2.md)\-Objekt zurück, das alle Haltepunkte aufgelistet, die mit dem aktuellen Speicherort des Codes zugeordnet sind.  
  
## Rückgabewert  
 Bei Erfolg gibt `S_OK`zurück. andernfalls gibt einen Fehlercode zurück.  
  
## Hinweise  
 Nicht alle Haltepunkte möglicherweise an einem bestimmten Speicherort lösen in einer bestimmten Zeit ausgeführt \(zum Beispiel wird ein Haltepunkt mit einer Bedingung nicht fehl, bis diese Bedingung erfüllt ist.\)  
  
## Siehe auch  
 [IDebugBreakpointEvent2](../../../extensibility/debugger/reference/idebugbreakpointevent2.md)   
 [IEnumDebugBoundBreakpoints2](../../../extensibility/debugger/reference/ienumdebugboundbreakpoints2.md)