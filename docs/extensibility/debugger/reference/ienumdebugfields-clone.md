---
title: "IEnumDebugFields::Clone | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IEnumDebugFields::Clone"
helpviewer_keywords: 
  - "IEnumDebugFields::Clone-Methode"
ms.assetid: 7ec265a8-696f-45ce-a2a2-0a83e96fee1b
caps.latest.revision: 5
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 5
---
# IEnumDebugFields::Clone
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Diese Methode gibt eine Kopie der aktuellen Enumeration z. B. ein separates Objekt zurück.  
  
## Syntax  
  
```cpp#  
HRESULT Clone(  
   IEnumDebugFields** ppEnum  
);  
```  
  
```c#  
int Clone(  
   out IEnumDebugFields ppEnum  
);  
```  
  
#### Parameter  
 `ppEnum`  
 \[out\]  Gibt eine Kopie dieser Enumeration z. B. ein separates Objekt zurück.  
  
## Eigenschaftswert\/Rückgabewert  
 Bei Erfolg gibt `S_OK`zurück. andernfalls gibt einen Fehlercode zurück.  
  
## Hinweise  
 Die Kopie der Enumeration verfügt über denselben Status wie das Original, wenn diese Methode aufgerufen wird.  Allerdings sind die Kopie und die Bedingungen der Vorlage und können separat individuell geändert werden.  
  
## Siehe auch  
 [IEnumDebugFields](../../../extensibility/debugger/reference/ienumdebugfields.md)