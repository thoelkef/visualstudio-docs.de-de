---
title: "IEnumDebugProcesses2::Clone | Microsoft Docs"
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
  - "IEnumDebugProcesses2::Clone"
helpviewer_keywords: 
  - "IEnumDebugProcesses2::Clone"
ms.assetid: 3d4196d3-5a80-4f76-b8b2-f72e80c8d406
caps.latest.revision: 9
caps.handback.revision: 9
ms.author: "gregvanl"
manager: "ghogen"
---
# IEnumDebugProcesses2::Clone
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Gibt eine Kopie der aktuellen Enumeration z. B. ein separates Objekt zurück.  
  
## Syntax  
  
```cpp#  
HRESULT Clone(  
   IEnumDebugProcesses2** ppEnum  
);  
```  
  
```c#  
int Clone(  
   out IEnumDebugProcesses2 ppEnum  
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
 [IEnumDebugProcesses2](../../../extensibility/debugger/reference/ienumdebugprocesses2.md)