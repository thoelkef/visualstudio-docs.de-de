---
title: "IDebugThread2::SetThreadName | Microsoft Docs"
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
  - "IDebugThread2::SetThreadName"
helpviewer_keywords: 
  - "IDebugThread2::SetThreadName"
ms.assetid: fa934121-3f58-44dc-9c30-d3f752e44c8b
caps.latest.revision: 10
caps.handback.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
---
# IDebugThread2::SetThreadName
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Legt den Namen des Threads fest.  
  
## Syntax  
  
```cpp#  
HRESULT SetThreadName (   
   LPCOLESTR pszName  
);  
```  
  
```c#  
int SetThreadName (   
   string pszName  
);  
```  
  
#### Parameter  
 `pszName`  
 \[in\]  Der Name des Threads.  
  
## Rückgabewert  
 Bei Erfolg gibt `S_OK`zurück. andernfalls gibt einen Fehlercode zurück.  
  
## Hinweise  
 Um den Namen des Threads abzurufen, rufen Sie die [GetName](../../../extensibility/debugger/reference/idebugthread2-getname.md)\-Methode auf.  
  
## Siehe auch  
 [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md)   
 [GetName](../../../extensibility/debugger/reference/idebugthread2-getname.md)