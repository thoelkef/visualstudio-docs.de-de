---
title: "IDebugMemoryContext2::GetInfo | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugMemoryContext2::GetInfo"
helpviewer_keywords: 
  - "GetInfo-Methode"
  - "IDebugMemoryContext2::GetInfo-Methode"
ms.assetid: 08c7f091-1816-4d64-8834-f9ecaac5c58d
caps.latest.revision: 13
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 13
---
# IDebugMemoryContext2::GetInfo
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Ruft eine [CONTEXT\_INFO](../../../extensibility/debugger/reference/context-info.md) Struktur ab, die den Kontext beschreibt.  
  
## Syntax  
  
```cpp#  
HRESULT GetInfo(   
   CONTEXT_INFO_FIELDS dwFields,  
   CONTEXT_INFO*       pInfo  
);  
```  
  
```c#  
int GetInfo(  
   enum_CONTEXT_INFO_FIELDS dwFields,   
   CONTEXT_INFO[]           pinfo  
);  
```  
  
#### Parameter  
 `dwFields`  
 \[in\]  Eine Kombination von Flags aus der [CONTEXT\_INFO\_FIELDS](../../../extensibility/debugger/reference/context-info-fields.md)\-Enumeration, die angeben, welche Felder der [CONTEXT\_INFO](../../../extensibility/debugger/reference/context-info.md) Struktur sein sollen, geben aus.  
  
 `pInfo`  
 \[in, out\]  Die `CONTEXT_INFO` Struktur, die gefüllt wird.  
  
## Rückgabewert  
 Bei Erfolg gibt `S_OK`zurück. andernfalls gibt einen Fehlercode zurück.  
  
## Siehe auch  
 [IDebugMemoryContext2](../../../extensibility/debugger/reference/idebugmemorycontext2.md)   
 [CONTEXT\_INFO\_FIELDS](../../../extensibility/debugger/reference/context-info-fields.md)   
 [CONTEXT\_INFO](../../../extensibility/debugger/reference/context-info.md)