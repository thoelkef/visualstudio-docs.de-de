---
title: "IDebugPortNotify2::RemoveProgramNode | Microsoft Docs"
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
  - "IDebugPortNotify2::RemoveProgramNode"
helpviewer_keywords: 
  - "IDebugPortNotify2::RemoveProgramNode"
ms.assetid: 3668157b-66d2-416e-a359-fc04dcd18a48
caps.latest.revision: 10
caps.handback.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
---
# IDebugPortNotify2::RemoveProgramNode
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Hebt die Registrierung eines Programms vom Port gedebuggt werden kann, den sie ausgeführt wird.  
  
## Syntax  
  
```cpp#  
HRESULT RemoveProgramNode(   
   IDebugProgramNode2* pProgramNode  
);  
```  
  
```c#  
int RemoveProgramNode(   
   IDebugProgramNode2 pProgramNode  
);  
```  
  
#### Parameter  
 `pProgramNode`  
 \[in\]  Ein [IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md) objecy, das das Programm darstellt, deren Registrierung aufgehoben werden soll.  
  
## Rückgabewert  
 Bei Erfolg gibt `S_OK`zurück. andernfalls gibt einen Fehlercode zurück.  
  
## Hinweise  
 Diese Methode entfernt einen Knoten Programm mit einem Aufruf der [AddProgramNode](../../../extensibility/debugger/reference/idebugportnotify2-addprogramnode.md)\-Methode hinzugefügt wurde.  
  
## Siehe auch  
 [IDebugPortNotify2](../../../extensibility/debugger/reference/idebugportnotify2.md)   
 [IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md)   
 [AddProgramNode](../../../extensibility/debugger/reference/idebugportnotify2-addprogramnode.md)