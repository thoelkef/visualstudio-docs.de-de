---
title: "IDebugArrayField::GetNumberOfElements | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugArrayField::GetNumberOfElements"
helpviewer_keywords: 
  - "IDebugArrayField::GetNumberOfElements-Methode"
ms.assetid: a1961ef3-d69d-4022-b8c9-b9cfb9811345
caps.latest.revision: 9
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 9
---
# IDebugArrayField::GetNumberOfElements
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Ruft die Anzahl der Elemente im Array ab.  
  
## Syntax  
  
```cpp#  
HRESULT GetNumberOfElements(   
   DWORD* pdwNumElements  
);  
```  
  
```c#  
int GetNumberOfElements(  
   out uint pdwNumElements  
);  
```  
  
#### Parameter  
 `pdwNumElements`  
 \[out\]  Gibt die Anzahl der Elemente im Array zurück.  
  
## Rückgabewert  
 Bei Erfolg gibt S\_OK zurück. andernfalls gibt einen Fehlercode zurück.  
  
## Hinweise  
 Der zurückgegebene Wert ist die Gesamtzahl der Elemente im Array, unabhängig von der Anzahl der Dimensionen.  
  
## Siehe auch  
 [IDebugArrayField](../../../extensibility/debugger/reference/idebugarrayfield.md)