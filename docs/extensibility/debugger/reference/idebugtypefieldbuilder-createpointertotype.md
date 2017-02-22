---
title: "IDebugTypeFieldBuilder::CreatePointerToType | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "CreatePointerToType"
  - "IDebugTypeFieldBuilder::CreatePointerToType"
ms.assetid: 73966e8a-b643-43e0-9b4e-0aa4b402ebbe
caps.latest.revision: 8
caps.handback.revision: 8
ms.author: "gregvanl"
manager: "ghogen"
---
# IDebugTypeFieldBuilder::CreatePointerToType
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Stellt einen Zeiger auf den angegebenen Typ.  
  
## Syntax  
  
```cpp#  
HRESULT CreatePointerToType(  
   IDebugField*  pTypeField,  
   IDebugField** pPtrToTypeField  
);  
```  
  
```c#  
int CreatePointerToType(  
   IDebugField     pTypeField,  
   out IDebugField pPtrToTypeField  
);  
```  
  
#### Parameter  
 `pTypeField`  
 \[in\]  Typ, um zu zeigen.  Sie wird von der [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)\-Schnittstelle dargestellt.  
  
 `pPtrToTypeField`  
 \[out\]  Gibt den Zeiger zurück, der durch ein neues **IDebugField\-**\-Objekt dargestellt wird.  
  
## Rückgabewert  
 Bei Erfolg gibt `S_OK`zurück. andernfalls gibt einen Fehlercode zurück.  
  
## Siehe auch  
 [IDebugTypeFieldBuilder](../../../extensibility/debugger/reference/idebugtypefieldbuilder.md)