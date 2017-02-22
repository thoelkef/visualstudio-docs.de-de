---
title: "IDebugAlias::GetObject | Microsoft Docs"
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
  - "IDebugAlias::GetObject"
helpviewer_keywords: 
  - "IDebugAlias::GetObject-Methode"
ms.assetid: 97bc3af6-6e55-4940-8a6d-692c61257806
caps.latest.revision: 7
caps.handback.revision: 7
ms.author: "gregvanl"
manager: "ghogen"
---
# IDebugAlias::GetObject
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Ruft das Objekt ab, zu dem dieser Alias ist.  
  
## Syntax  
  
```cpp  
HRESULT GetObject(  
   IDebugObject2** ppObject  
);  
```  
  
```c#  
int GetObject(  
   Out IDebugObject2 ppObject  
)  
```  
  
#### Parameter  
 `ppObject`  
 \[out\]  [IDebugObject2](../../../extensibility/debugger/reference/idebugobject2.md) , das dieser Alias darstellt.  
  
## Rückgabewert  
 Bei Erfolg gibt S\_OK zurück. andernfalls gibt einen Fehlercode zurück.  
  
## Siehe auch  
 [IDebugAlias](../../../extensibility/debugger/reference/idebugalias.md)   
 [IDebugObject2](../../../extensibility/debugger/reference/idebugobject2.md)