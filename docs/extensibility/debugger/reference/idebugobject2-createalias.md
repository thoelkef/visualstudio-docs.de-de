---
title: "IDebugObject2::CreateAlias | Microsoft Docs"
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
  - "IDebugObject2::CreateAlias"
helpviewer_keywords: 
  - "IDebugObject2::CreateAlias-Methode"
ms.assetid: 54a05920-5d13-4f67-962b-d1a7f013dff9
caps.latest.revision: 7
caps.handback.revision: 7
ms.author: "gregvanl"
manager: "ghogen"
---
# IDebugObject2::CreateAlias
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Erstellt eine eindeutige ID oder einen Alias für dieses Objekt einen vorhandenen Alias oder gibt diese zurück.  
  
## Syntax  
  
```cpp  
HRESULT CreateAlias(  
   IDebugAlias** ppAlias  
);  
```  
  
```c#  
int CreateAlias(  
   out IDebugAlias ppAlias  
);  
```  
  
#### Parameter  
 `ppAlias`  
 \[out\]  Der neue existierend \(oder Alias\).  
  
## Rückgabewert  
 Bei Erfolg gibt S\_OK zurück. andernfalls gibt einen Fehlercode zurück.  
  
## Hinweise  
 Ein Alias ist eine Bezeichnung, die ein bestimmtes Objekt darstellt, während das Objekt im Arbeitsspeicher ist.  
  
## Siehe auch  
 [IDebugObject2](../../../extensibility/debugger/reference/idebugobject2.md)   
 [IDebugAlias](../../../extensibility/debugger/reference/idebugalias.md)