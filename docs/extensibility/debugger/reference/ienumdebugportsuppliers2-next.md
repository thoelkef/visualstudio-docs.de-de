---
title: "IEnumDebugPortSuppliers2::Next | Microsoft Docs"
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
  - "IEnumDebugPortSuppliers2::Next"
helpviewer_keywords: 
  - "IEnumDebugPortSuppliers2::Next"
ms.assetid: e2a2d226-e70b-42c2-bf00-a936517940c8
caps.latest.revision: 12
caps.handback.revision: 12
ms.author: "gregvanl"
manager: "ghogen"
---
# IEnumDebugPortSuppliers2::Next
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Gibt die nächste Gruppe von Elementen aus der Enumeration zurück.  
  
## Syntax  
  
```cpp#  
HRESULT Next(  
   ULONG                 celt,  
   IDebugPortSupplier2** rgelt,  
   ULONG*                pceltFetched  
);  
```  
  
```c#  
int Next(  
   uint                  celt,  
   IDebugPortSupplier2[] rgelt,  
   ref uint              pceltFetched  
);  
```  
  
#### Parameter  
 `celt`  
 \[in\]  Die Anzahl der abzurufenden Elemente.  Gibt die maximale Größe des `rgelt` Arrays an.  
  
 `rgelt`  
 \[in, out\]  Array von Elementen, [IDebugPortSupplier2](../../../extensibility/debugger/reference/idebugportsupplier2.md) ausgefüllt werden soll.  
  
 `pceltFetched`  
 \[out\]  Gibt die Anzahl der Elemente zurück, die sich tatsächlich in `rgelt`zurückgegeben werden.  
  
## Rückgabewert  
 Bei Erfolg gibt `S_OK`zurück.  Gibt `S_FALSE` zurück, wenn kleiner als die angeforderte Anzahl von Elementen zurückgegeben werden konnte. andernfalls gibt einen Fehlercode zurück.  
  
## Siehe auch  
 [IEnumDebugPortSuppliers2](../../../extensibility/debugger/reference/ienumdebugportsuppliers2.md)   
 [IDebugPortSupplier2](../../../extensibility/debugger/reference/idebugportsupplier2.md)