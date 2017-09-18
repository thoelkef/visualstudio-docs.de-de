---
title: "IDebugArrayObject::GetDimensions | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugArrayObject::GetDimensions"
helpviewer_keywords: 
  - "IDebugArrayObject::GetDimensions-Methode"
ms.assetid: 113e0aff-9028-49d6-b104-9fe7be4772d7
caps.latest.revision: 9
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 9
---
# IDebugArrayObject::GetDimensions
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Ruft die Dimensionen des Arrays ab.  
  
## Syntax  
  
```cpp#  
HRESULT GetDimensions(   
   DWORD dwCount,  
   DWORD dwDimensions[]  
);  
```  
  
```c#  
int GetDimensions(  
   [In] uint    dwCount,   
   [Out] uint[] dwDimensions  
);  
```  
  
#### Parameter  
 `dwCount`  
 \[in\]  Die Anzahl der abzurufenden Dimensionen.  
  
 `dwDimensions`  
 \[in, out\]  Ein Array, das die Größe jeder Dimension gefüllt wird.  `dwCount` gibt die maximale Größe des `dwDimensions` Arrays an.  
  
## Rückgabewert  
 Bei Erfolg gibt S\_OK zurück. andernfalls gibt einen Fehlercode zurück.  
  
## Hinweise  
 Ein mehrdimensionales Array kann unterschiedliche Größen für jede Dimension aufweisen.  Beispielsweise würde das dreidimensionale Array `myarray[3][2][6]`diese Methode 3, 2 und 6 im `dwDimensions`\-Parameter in dieser Reihenfolge zurückgeben.  
  
## Siehe auch  
 [IDebugArrayObject](../../../extensibility/debugger/reference/idebugarrayobject.md)