---
title: "IDebugProperty2::GetParent | Microsoft Docs"
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
  - "IDebugProperty2::GetParent"
helpviewer_keywords: 
  - "IDebugProperty2::GetParent"
ms.assetid: 58780469-fe25-4d84-9187-67940ca0767f
caps.latest.revision: 10
caps.handback.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
---
# IDebugProperty2::GetParent
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Ruft die übergeordnete Eigenschaft einer Eigenschaft ab.  
  
## Syntax  
  
```cpp#  
HRESULT GetParent (   
   IDebugProperty2** ppParent  
);  
```  
  
```c#  
int GetParent (   
   out IDebugProperty2 ppParent  
);  
```  
  
#### Parameter  
 `ppParent`  
 \[out\]  Gibt ein [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)\-Objekt zurück, das das übergeordnete Element der Eigenschaft darstellt.  
  
## Rückgabewert  
 Bei Erfolg gibt `S_OK`zurück. gibt andernfalls Fehlercode zurück.  Gibt `S_GETPARENT_NO_PARENT` zurück, wenn kein übergeordnetes Element vorhanden ist.  
  
## Siehe auch  
 [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)