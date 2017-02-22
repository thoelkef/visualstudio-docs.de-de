---
title: "IDebugObject::GetMemoryContext | Microsoft Docs"
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
  - "IDebugObject::GetMemoryContext"
helpviewer_keywords: 
  - "IDebugObject::GetMemoryContext-Methode"
ms.assetid: 6760a0d3-a898-4e81-b68f-c45c584b225b
caps.latest.revision: 9
caps.handback.revision: 9
ms.author: "gregvanl"
manager: "ghogen"
---
# IDebugObject::GetMemoryContext
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Ruft den Arbeitsspeicher Elementkontext ab, der die Adresse des Werts des Objekts darstellt.  
  
## Syntax  
  
```cpp#  
HRESULT GetMemoryContext(   
   IDebugMemoryContext2** pContext  
);  
```  
  
```c#  
int GetMemoryContext(  
   ref IDebugMemoryContext2 pContext  
);  
```  
  
#### Parameter  
 `pContext`  
 \[out\]  Gibt ein [IDebugMemoryContext2](../../../extensibility/debugger/reference/idebugmemorycontext2.md)\-Objekt zurück, das die Adresse des Werts des Objekts darstellt.  
  
## Rückgabewert  
 Bei Erfolg gibt S\_OK zurück. andernfalls gibt einen Fehlercode zurück.  
  
## Hinweise  
 Der zurückgegebene Arbeitsspeicher Elementkontext gibt die Adresse des Werts veranschaulicht, wie durch diese [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md)\-Objekt dargestellt.  
  
## Siehe auch  
 [IDebugMemoryContext2](../../../extensibility/debugger/reference/idebugmemorycontext2.md)