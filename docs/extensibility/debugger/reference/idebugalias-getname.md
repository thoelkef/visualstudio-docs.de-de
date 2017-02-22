---
title: "IDebugAlias::GetName | Microsoft Docs"
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
  - "IDebugAlias::GetName"
helpviewer_keywords: 
  - "IDebugAlias::GetName-Methode"
ms.assetid: ac2d8891-56b5-40ef-9866-ed74f18bb043
caps.latest.revision: 8
caps.handback.revision: 8
ms.author: "gregvanl"
manager: "ghogen"
---
# IDebugAlias::GetName
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Ruft den Namen dieses Alias ab.  
  
## Syntax  
  
```cpp  
HRESULT GetName(  
   BSTR* pbstrName  
);  
```  
  
```c#  
int GetName(  
   out string pbstrName  
);  
```  
  
#### Parameter  
 `pbstrName`  
 \[out\]  Name des Alias.  
  
## Rückgabewert  
 Bei Erfolg gibt S\_OK zurück. andernfalls gibt einen Fehlercode zurück.  
  
## Siehe auch  
 [IDebugAlias](../../../extensibility/debugger/reference/idebugalias.md)