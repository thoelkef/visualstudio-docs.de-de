---
title: "IDebugArrayObject::GetElements | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugArrayObject::GetElements"
helpviewer_keywords: 
  - "IDebugArrayObject::GetElements-Methode"
ms.assetid: f6a6262f-5183-46ce-8a45-33ef46088b98
caps.latest.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 10
---
# IDebugArrayObject::GetElements
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Ruft einen Enumerator zum Auflisten aller Elemente des Arrays ab.  
  
## Syntax  
  
```cpp#  
HRESULT GetElements(   
   IEnumDebugObjects** ppEnum  
);  
```  
  
```c#  
int GetElements(  
   out IEnumDebugObjects ppEnum  
);  
```  
  
#### Parameter  
 `ppEnum`  
 \[out\]  Gibt ein [IEnumDebugObjects](../../../extensibility/debugger/reference/ienumdebugobjects.md)\-Objekt zurück, das das Aufzählen über alle Elemente zulässig.  
  
## Rückgabewert  
 Bei Erfolg gibt S\_OK zurück. andernfalls gibt einen Fehlercode zurück.  
  
## Hinweise  
 Alternativ können Sie die [GetCount](../../../extensibility/debugger/reference/idebugarrayobject-getcount.md) und [GetElement](../../../extensibility/debugger/reference/idebugarrayobject-getelement.md)\-Methoden zum Durchlaufen der Elemente.  
  
## Siehe auch  
 [IDebugArrayObject](../../../extensibility/debugger/reference/idebugarrayobject.md)