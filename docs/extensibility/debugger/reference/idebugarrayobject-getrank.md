---
title: "IDebugArrayObject::GetRank | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugArrayObject::GetRank"
helpviewer_keywords: 
  - "IDebugArrayObject::GetRank-Methode"
ms.assetid: 9948551a-e334-4ff6-979c-08dab633b9b6
caps.latest.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 10
---
# IDebugArrayObject::GetRank
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Ruft den Rang des Arrays, d. h. die Anzahl der Dimensionen ab.  
  
## Syntax  
  
```cpp#  
HRESULT GetRank(   
   DWORD* pdwRank  
);  
```  
  
```c#  
int GetRank(  
   out uint pdwRank  
);  
```  
  
#### Parameter  
 `pdwRank`  
 \[out\]  Gibt den Rang zurück.  
  
## Rückgabewert  
 Bei Erfolg gibt S\_OK zurück. andernfalls gibt einen Fehlercode zurück.  
  
## Hinweise  
 Verwenden Sie die [GetDimensions](../../../extensibility/debugger/reference/idebugarrayobject-getdimensions.md)\-Methode, um die Größe jeder Dimension des Arrayobjekts abzurufen.  
  
## Siehe auch  
 [IDebugArrayObject](../../../extensibility/debugger/reference/idebugarrayobject.md)