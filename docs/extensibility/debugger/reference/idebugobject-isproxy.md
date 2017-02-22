---
title: "IDebugObject::IsProxy | Microsoft Docs"
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
  - "IDebugObject::IsProxy"
  - "IsProxy"
ms.assetid: 06c66b87-db95-4400-ab26-5d33e743a439
caps.latest.revision: 8
caps.handback.revision: 8
ms.author: "gregvanl"
manager: "ghogen"
---
# IDebugObject::IsProxy
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Bestimmt, ob es sich bei dem Objekt um einen transparenten Proxy befindet.  
  
## Syntax  
  
```cpp#  
HRESULT IsProxy (  
   BOOL* pfIsProxy  
);  
```  
  
```c#  
int IsProxy (  
   out bool pfIsProxy  
);  
```  
  
#### Parameter  
 `pfIsProxy`  
 \[out\]  `TRUE` , wenn das Objekt einen transparenten Proxy befindet. andernfalls `FALSE`.  
  
## Rückgabewert  
 Bei Erfolg gibt `S_OK`zurück. andernfalls gibt einen Fehlercode zurück.  
  
## Hinweise  
 Diese Methode wird vom standardmäßigen Debugmodul C\+\+ implementiert.  
  
## Siehe auch  
 [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md)