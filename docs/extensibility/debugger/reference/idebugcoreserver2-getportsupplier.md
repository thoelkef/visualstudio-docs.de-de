---
title: "IDebugCoreServer2::GetPortSupplier | Microsoft Docs"
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
  - "IDebugCoreServer2::GetPortSupplier"
helpviewer_keywords: 
  - "IDebugCoreServer2::GetPortSupplier"
ms.assetid: acf181d4-ef42-4aa5-86f9-95fd5467ea31
caps.latest.revision: 10
caps.handback.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
---
# IDebugCoreServer2::GetPortSupplier
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Ruft einen bestimmten Anschlusslieferanten ab.  
  
## Syntax  
  
```cpp#  
HRESULT GetPortSupplier(   
   REFGUID               guidPortSupplier,  
   IDebugPortSupplier2** ppPortSupplier  
);  
```  
  
```c#  
int GetPortSupplier(   
   ref Guid                guidPortSupplier,  
   out IDebugPortSupplier2 ppPortSupplier  
);  
```  
  
#### Parameter  
 `guidPortSupplier`  
 \[in\]  GUID des abzurufenden Anschlusslieferanten.  
  
 `ppPortSupplier`  
 \[out\]  Gibt ein [IDebugPortSupplier2](../../../extensibility/debugger/reference/idebugportsupplier2.md)\-Objekt zurück, das den gewünschten Anschlusslieferanten darstellt.  
  
## Rückgabewert  
 Bei Erfolg gibt `S_OK`zurück. andernfalls gibt einen Fehlercode zurück.  
  
## Siehe auch  
 [IDebugCoreServer2](../../../extensibility/debugger/reference/idebugcoreserver2.md)   
 [IDebugPortSupplier2](../../../extensibility/debugger/reference/idebugportsupplier2.md)