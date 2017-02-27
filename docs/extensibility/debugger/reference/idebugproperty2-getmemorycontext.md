---
title: "IDebugProperty2::GetMemoryContext | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugProperty2::GetMemoryContext"
helpviewer_keywords: 
  - "IDebugProperty2::GetMemoryContext"
ms.assetid: 91793d25-790f-4881-a5c0-d0458e534514
caps.latest.revision: 13
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 13
---
# IDebugProperty2::GetMemoryContext
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Ruft den Arbeitsspeicher Elementkontext des Eigenschaftswerts ab.  
  
## Syntax  
  
```cpp#  
HRESULT GetMemoryContext (   
   IDebugMemoryContext2** ppMemory  
);  
```  
  
```c#  
int GetMemoryContext(  
   out IDebugMemoryContext2 ppMemory  
);  
```  
  
#### Parameter  
 `ppMemory`  
 \[out\]  Gibt das [IDebugMemoryContext2](../../../extensibility/debugger/reference/idebugmemorycontext2.md)\-Objekt zurück, das den Speicher darstellt, der dieser Eigenschaft zugeordnet ist.  
  
## Rückgabewert  
 Bei Erfolg gibt `S_OK`zurück. gibt andernfalls Fehlercode zurück.  Gibt `S_GETMEMORYCONTEXT_NO_MEMORY_CONTEXT` zurück, wenn kein Kontext gibt Arbeitsspeicher abrufen.  
  
## Siehe auch  
 [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)   
 [IDebugMemoryContext2](../../../extensibility/debugger/reference/idebugmemorycontext2.md)