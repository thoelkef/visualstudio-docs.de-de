---
title: "IDebugPortSupplierEx2::SetServer | Microsoft Docs"
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
  - "IDebugPortSupplierEx2::SetServer"
ms.assetid: 0e8ef194-3a4f-4abf-8382-4607ab3005d1
caps.latest.revision: 5
caps.handback.revision: 5
ms.author: "gregvanl"
manager: "ghogen"
---
# IDebugPortSupplierEx2::SetServer
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Legt den zentralen Server für den Anschlusslieferanten ab.  
  
## Syntax  
  
```cpp#  
HRESULT SetServer(  
   IDebugCoreServer2* pServer  
);  
```  
  
```c#  
int SetServer(  
   IDebugCoreServer2 pServer  
);  
```  
  
#### Parameter  
 `pServer`  
 Für den Anschlusslieferanten zentralen Server festzulegen.  
  
## Rückgabewert  
 Bei Erfolg gibt `S_OK`zurück. andernfalls gibt einen Fehlercode zurück.  
  
## Siehe auch  
 [IDebugPortSupplierEx2](../../../extensibility/debugger/reference/idebugportsupplierex2.md)