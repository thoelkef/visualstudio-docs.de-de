---
title: "IDebugField::GetAddress | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugField::GetAddress"
helpviewer_keywords: 
  - "IDebugField::GetAddress-Methode"
ms.assetid: 6981bf03-66ef-4bf9-87ea-f6c9624486cb
caps.latest.revision: 11
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 11
---
# IDebugField::GetAddress
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Diese Methode ruft die die Adresse eines Felds ab.  
  
## Syntax  
  
```cpp#  
HRESULT GetAddress(   
   IDebugAddress** ppAddress  
);  
```  
  
```c#  
int GetAddress(  
   out IDebugAddress ppAddress  
);  
```  
  
#### Parameter  
 `ppAddress`  
 \[out\]  Gibt die Adresse als [IDebugAddress](../../../extensibility/debugger/reference/idebugaddress.md)\-Objekt zurück.  
  
## Rückgabewert  
 Bei Erfolg gibt `S_OK`zurück. andernfalls geben Sie einen Fehlercode zurück.  
  
## Siehe auch  
 [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)   
 [IDebugAddress](../../../extensibility/debugger/reference/idebugaddress.md)