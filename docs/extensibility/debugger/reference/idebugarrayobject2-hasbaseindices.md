---
title: "IDebugArrayObject2::HasBaseIndices | Microsoft Docs"
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
  - "HasBaseIndices"
  - "IDebugArrayObject2::HasBaseIndices"
ms.assetid: 51a5d145-ea53-422c-b5cf-c800cf64b8e6
caps.latest.revision: 9
caps.handback.revision: 9
ms.author: "gregvanl"
manager: "ghogen"
---
# IDebugArrayObject2::HasBaseIndices
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Bestimmt, ob das Array die Untergrenze Indizes \(Basis\-\) definiert hat.  
  
## Syntax  
  
```cpp#  
HRESULT HasBaseIndices (  
   BOOL* pfHasBaseIndices  
);  
```  
  
```c#  
int HasBaseIndices (  
   out bool pfHasBaseIndices  
);  
```  
  
#### Parameter  
 `pfHasBaseIndices`  
 \[out\]  Mit TRUE, dass das Array von Indizes \(die Untergrenze\) verfügt. andernfalls FALSE.  
  
## Rückgabewert  
 Bei Erfolg gibt `S_OK`zurück. andernfalls gibt einen Fehlercode zurück.