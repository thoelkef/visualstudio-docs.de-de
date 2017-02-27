---
title: "IDebugProgramEx2::GetProgramNode | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugProgramEx2::Attach"
helpviewer_keywords: 
  - "IDebugProgramEx2::Attach"
ms.assetid: 1545ffbf-1422-4b5d-9bb9-314ba8665041
caps.latest.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 10
---
# IDebugProgramEx2::GetProgramNode
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Ruft den Knoten ab, der die Programmierung mit einem Programm zugeordnet ist.  
  
## Syntax  
  
```cpp#  
HRESULT GetProgramNode(   
   IDebugProgramNode2** ppProgramNode  
);  
```  
  
```c#  
int GetProgramNode(   
   out IDebugProgramNode2 ppProgramNode  
);  
```  
  
#### Parameter  
 `ppProgramNode`  
 \[out\]  Gibt ein [IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md)\-Objekt zurück, das den Knoten darstellt, der die Programmierung mit diesem Programm zugeordnet ist.  
  
## Rückgabewert  
 Bei Erfolg gibt `S_OK`zurück. andernfalls gibt einen Fehlercode zurück.  
  
## Siehe auch  
 [IDebugProgramEx2](../../../extensibility/debugger/reference/idebugprogramex2.md)   
 [IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md)