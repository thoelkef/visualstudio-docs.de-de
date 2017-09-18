---
title: "IDebugField::GetTypeInfo | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugField::GetTypeInfo"
helpviewer_keywords: 
  - "IDebugField::GetTypeInfo-Methode"
ms.assetid: bb5acfa3-04c3-4088-be84-9ff8926cd16f
caps.latest.revision: 11
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 11
---
# IDebugField::GetTypeInfo
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Diese Methode ruft TYPE\-unabhängige Informationen über das Symbol oder den Typ ab.  
  
## Syntax  
  
```cpp#  
HRESULT GetTypeInfo(   
   TYPE_INFO* pTypeInfo  
);  
```  
  
```c#  
int GetTypeInfo(  
   TYPE_INFO[] pTypeInfo  
);  
```  
  
#### Parameter  
 `pTypeInfo`  
 \[out\]  Gibt Typinformationen in der angegebenen [TYPE\_INFO](../../../extensibility/debugger/reference/type-info.md) Struktur zurück.  
  
## Rückgabewert  
 Bei Erfolg gibt `S_OK`zurück. andernfalls gibt einen Fehlercode zurück.  
  
## Hinweise  
 TYPE\-unabhängige Informationen würden, z. B. AppDomain, das Modul und die Klasse umfassen, die das Symbol enthält.  
  
## Siehe auch  
 [GetType](../../../extensibility/debugger/reference/idebugfield-gettype.md)   
 [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)   
 [TYPE\_INFO](../../../extensibility/debugger/reference/type-info.md)