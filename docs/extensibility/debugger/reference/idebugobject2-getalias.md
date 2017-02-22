---
title: "IDebugObject2::GetAlias | Microsoft Docs"
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
  - "IDebugObject2::GetAlias"
helpviewer_keywords: 
  - "IDebugObject2::GetAlias-Methode"
ms.assetid: aa6824d5-c932-42ba-8713-950e7d1fb42f
caps.latest.revision: 7
caps.handback.revision: 7
ms.author: "gregvanl"
manager: "ghogen"
---
# IDebugObject2::GetAlias
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Ruft den Aliasnamen ab, der diesem Objekt zugeordnet ist, sofern vorhanden.  
  
## Syntax  
  
```cpp  
HRESULT GetAlias(  
   IDebugAlias** ppAlias  
);  
```  
  
```c#  
int GetAlias(  
   out IDebugAlias ppAlias  
);  
```  
  
#### Parameter  
 `ppAlias`  
 \[out\]  Gibt ein [IDebugAlias](../../../extensibility/debugger/reference/idebugalias.md)\-Objekt zurück, das den Alias für dieses Objekt darstellt. andernfalls gibt einen NULL\-Wert zurück.  
  
## Rückgabewert  
 Bei Erfolg gibt S\_OK zurück. andernfalls gibt einen Fehlercode zurück.  
  
## Hinweise  
 Ein Alias für ein Objekt wird mit einem Aufruf der [CreateAlias](../../../extensibility/debugger/reference/idebugobject2-createalias.md)\-Methode erstellt wird.  
  
## Siehe auch  
 [IDebugObject2](../../../extensibility/debugger/reference/idebugobject2.md)   
 [IDebugAlias](../../../extensibility/debugger/reference/idebugalias.md)