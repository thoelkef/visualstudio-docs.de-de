---
title: "IDebugArrayObject::GetCount | Microsoft Docs"
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
  - "IDebugArrayObject::GetCount"
helpviewer_keywords: 
  - "IDebugArrayObject::GetCount-Methode"
ms.assetid: 7931f3f7-033c-4bf8-8abd-95183952ebb0
caps.latest.revision: 10
caps.handback.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
---
# IDebugArrayObject::GetCount
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Ruft die Anzahl der Elemente im Array ab.  
  
## Syntax  
  
```  
[C++]  
HRESULT GetCount(   
   DWORD* pdwElements  
);  
```  
  
```  
[C#]  
int GetCount(  
   out uint pdwElements  
);  
```  
  
#### Parameter  
 `pdwElements`  
 \[out\]  Gibt die Anzahl zurück.  
  
## Rückgabewert  
 Bei Erfolg gibt S\_OK zurück. andernfalls gibt einen Fehlercode zurück.  
  
## Hinweise  
 Diese Methode erkennt alle Elemente eines Arrayobjekts als eindimensionales Array, selbst wenn das Arrayobjekt mehrdimensional ist.  Beispielsweise würde das Array `myarray[3][2][6]`diese Methode 36 im `pdwElements`\-Parameter zurückgeben.  Verwenden Sie die [GetElement](../../../extensibility/debugger/reference/idebugarrayobject-getelement.md)\-Methode, um die einzelnen Elemente einzeln abzurufen.  
  
## Siehe auch  
 [IDebugArrayObject](../../../extensibility/debugger/reference/idebugarrayobject.md)