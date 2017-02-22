---
title: "IDebugBinder::GetMemoryContext | Microsoft Docs"
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
  - "IDebugBinder::GetMemoryContext"
helpviewer_keywords: 
  - "IDebugBinder::GetMemoryContext-Methode"
ms.assetid: 801c5b60-acff-4822-b23d-e9c7bbca8a0f
caps.latest.revision: 12
caps.handback.revision: 12
ms.author: "gregvanl"
manager: "ghogen"
---
# IDebugBinder::GetMemoryContext
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Diese Methode konvertiert ein Objekt oder eine Speicheradresse Speicherort zu einem Speicher Elementkontext.  
  
## Syntax  
  
```cpp#  
HRESULT GetMemoryContext(   
   IDebugField*           pField,  
   DWORD                  dwConstant,  
   IDebugMemoryContext2** ppMemCxt  
);  
```  
  
```c#  
int GetMemoryContext(  
   IDebugField              pField,   
   uint                     dwConstant,   
   out IDebugMemoryContext2 ppMemCxt  
);  
```  
  
#### Parameter  
 `pField`  
 \[in\]  [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) , das das Objekt beschreibt.  Wenn `NULL`, `dwConstant`\-Version verwenden.  
  
 `dwConstant`  
 \[in\]  Eine konstante Speicheradresse, wie 0x5000.  
  
 `ppMemCxt`  
 \[out\]  Gibt die [IDebugMemoryContext2](../../../extensibility/debugger/reference/idebugmemorycontext2.md)\-Schnittstelle, die die Adresse des Objekts darstellt, oder die Adresse im Arbeitsspeicher zurück.  
  
## Rückgabewert  
 Bei Erfolg gibt `S_OK`zurück. andernfalls gibt einen Fehlercode zurück.  
  
## Siehe auch  
 [IDebugBinder](../../../extensibility/debugger/reference/idebugbinder.md)   
 [IDebugMemoryContext2](../../../extensibility/debugger/reference/idebugmemorycontext2.md)   
 [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)