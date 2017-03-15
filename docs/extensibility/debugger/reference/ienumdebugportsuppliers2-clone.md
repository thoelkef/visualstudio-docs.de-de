---
title: "IEnumDebugPortSuppliers2::Clone | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IEnumDebugPortSuppliers2::Clone"
helpviewer_keywords: 
  - "IEnumDebugPortSuppliers2::Clone"
ms.assetid: 98b9914d-4f32-44da-b422-68830bce44b4
caps.latest.revision: 9
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 9
---
# IEnumDebugPortSuppliers2::Clone
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Gibt eine Kopie der aktuellen Enumeration z. B. ein separates Objekt zurück.  
  
## Syntax  
  
```cpp#  
HRESULT Clone(  
   IEnumDebugPortSuppliers2** ppEnum  
);  
```  
  
```c#  
int Clone(  
   out IEnumDebugPortSuppliers2 ppEnum  
);  
```  
  
#### Parameter  
 `ppEnum`  
 \[out\]  Gibt eine Kopie dieser Enumeration z. B. ein separates Objekt zurück.  
  
## Rückgabewert  
 Bei Erfolg gibt `S_OK`zurück. andernfalls gibt einen Fehlercode zurück.  
  
## Hinweise  
 Die Kopie der Enumeration verfügt über denselben Status wie das Original, wenn diese Methode aufgerufen wird.  Allerdings sind die Kopie und die Bedingungen der Vorlage und können separat individuell geändert werden.  
  
## Siehe auch  
 [IEnumDebugPortSuppliers2](../../../extensibility/debugger/reference/ienumdebugportsuppliers2.md)