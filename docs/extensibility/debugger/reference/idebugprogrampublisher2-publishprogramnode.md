---
title: "IDebugProgramPublisher2::PublishProgramNode | Microsoft Docs"
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
  - "IDebugProgramPublisher2::PublishProgramNode"
helpviewer_keywords: 
  - "IDebugProgramPublisher2::PublishProgramNode"
ms.assetid: d4b72e04-f726-46cf-8e56-5203ff205b12
caps.latest.revision: 8
caps.handback.revision: 8
ms.author: "gregvanl"
manager: "ghogen"
---
# IDebugProgramPublisher2::PublishProgramNode
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Stellt einen Knoten für die Module Programm DES \(Debuggen\) und den Manager der Sitzung \(SDM\).  
  
## Syntax  
  
```cpp  
HRESULT PublishProgramNode(  
   IDebugProgramNode2 *pProgramNode  
);  
```  
  
```c#  
int PublishProgramNode(  
   IDebugProgramNode2 pProgramNode  
);  
```  
  
#### Parameter  
 `pProgramNode`  
 \[in\]  Ein [IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md)\-Objekt, das den Knoten darstellt, das Programm zur Verfügung zu stellen.  
  
## Rückgabewert  
 Bei Erfolg gibt `S_OK`zurück. andernfalls gibt einen Fehlercode zurück.  
  
## Hinweise  
 Diese Methode ermöglicht die Software Informationen abgefragt werden soll, bevor sie zum Debuggen ausgewählt und startet.  
  
 Um einen Knoten Programm von der Verfügbarkeit zu entfernen, rufen Sie die [UnpublishProgramNode](../../../extensibility/debugger/reference/idebugprogrampublisher2-unpublishprogramnode.md)\-Methode auf.  
  
## Siehe auch  
 [IDebugProgramPublisher2](../../../extensibility/debugger/reference/idebugprogrampublisher2.md)   
 [IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md)   
 [UnpublishProgramNode](../../../extensibility/debugger/reference/idebugprogrampublisher2-unpublishprogramnode.md)