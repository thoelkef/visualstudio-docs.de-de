---
title: "IDebugPortSupplier3::EnumPersistedPorts | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugPortSupplier3::EnumPersistedPorts"
helpviewer_keywords: 
  - "IDebugPortSupplier3::EnumPersistedPorts"
ms.assetid: 1c3dead3-5d6c-4067-8418-4015f0b0dd07
caps.latest.revision: 12
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 12
---
# IDebugPortSupplier3::EnumPersistedPorts
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Diese Methode ruft ein Objekt ab, das eine Enumeration der Liste der beibehaltenen Ports ermöglicht.  
  
## Syntax  
  
```cpp  
HRESULT EnumPersistedPorts(  
   BSTR_ARRAY         PortNames,  
   IEnumDebugPorts2** ppEnum  
);  
```  
  
```c#  
int EnumPersistedPorts(  
   BSTR_ARRAY           PortNames,  
   out IEnumDebugPorts2 ppEnum  
);  
```  
  
#### Parameter  
 `PortNames`  
 \[in\]  Eine [BSTR\_ARRAY](../../../extensibility/debugger/reference/bstr-array.md) Struktur, die eine Liste mit Namen des Anschlusses enthält, die mit den beibehaltenen Ports zu suchen und zu wechseln.  Nur die beibehaltenen Ports mit diesem Namen werden zurückgegeben.  
  
 `ppEnum`  
 \[out\]  Ein Objekt, das die [IEnumDebugPorts2](../../../extensibility/debugger/reference/ienumdebugports2.md)\-Schnittstelle implementiert.  
  
## Rückgabewert  
 Bei Erfolg gibt `S_OK`zurück. andernfalls gibt einen Fehlercode zurück.  
  
## Hinweise  
 Beibehaltene Ports geladen werden, wenn ein Anschluss lieferant instanziiert wird, und gespeichert, wenn sich der Port lieferant zerstört wird.  
  
## Siehe auch  
 [IDebugPortSupplier3](../../../extensibility/debugger/reference/idebugportsupplier3.md)   
 [IEnumDebugPorts2](../../../extensibility/debugger/reference/ienumdebugports2.md)   
 [BSTR\_ARRAY](../../../extensibility/debugger/reference/bstr-array.md)