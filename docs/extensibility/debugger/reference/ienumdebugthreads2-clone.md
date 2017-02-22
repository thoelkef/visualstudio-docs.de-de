---
title: "IEnumDebugThreads2::Clone | Microsoft Docs"
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
  - "IEnumDebugThreads2::Clone"
helpviewer_keywords: 
  - "IEnumDebugThreads2::Clone"
ms.assetid: d774322c-e72d-4df3-b317-928da39dadc5
caps.latest.revision: 9
caps.handback.revision: 9
ms.author: "gregvanl"
manager: "ghogen"
---
# IEnumDebugThreads2::Clone
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Gibt eine Kopie der aktuellen Enumeration z. B. ein separates Objekt zurück.  
  
## Syntax  
  
```cpp#  
HRESULT Clone(  
   IEnumDebugThreads2** ppEnum  
);  
```  
  
```c#  
int Clone(  
   out IEnumDebugThreads2 ppEnum  
);  
```  
  
#### Parameter  
 `ppEnum`  
 \[out\]  Gibt eine Kopie dieser Enumeration z. B. ein separates Objekt zurück.  
  
## Rückgabewert  
 Bei Erfolg gibt `S_OK`zurück. andernfalls gibt einen Fehlercode zurück.  
  
## Hinweise  
 Die Kopie der Enumeration verfügt über denselben Status wie das Original, wenn diese Methode aufgerufen wird.  Allerdings sind die Kopie und die Bedingungen der Vorlage und können separat individuell geändert werden.  
  
## Siehe auch  
 [IEnumDebugThreads2](../../../extensibility/debugger/reference/ienumdebugthreads2.md)