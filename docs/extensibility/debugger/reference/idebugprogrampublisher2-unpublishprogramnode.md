---
title: "IDebugProgramPublisher2::UnpublishProgramNode | Microsoft Docs"
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
  - "IDebugProgramPublisher2::UnpublishProgramNode"
helpviewer_keywords: 
  - "IDebugProgramPublisher2::UnpublishProgramNode"
ms.assetid: 57c7e6e1-b84e-4e14-ad83-cbbb64e2f526
caps.latest.revision: 8
caps.handback.revision: 8
ms.author: "gregvanl"
manager: "ghogen"
---
# IDebugProgramPublisher2::UnpublishProgramNode
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Entfernt einen angegebenen Knoten Programm von der Verfügbarkeit von Modulen, um DES \(Debuggen\) und den Manager der Sitzung \(SDM\) zu debuggen.  
  
## Syntax  
  
```cpp  
HRESULT UnpublishProgramNode(  
   IDebugProgramNode2* pProgramNode  
);  
```  
  
```c#  
int UnpublishProgramNode(  
   IDebugProgramNode2 pProgramNode  
);  
```  
  
#### Parameter  
 `pProgramNode`  
 \[in\]  Ein [IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md)\-Objekt, das den Knoten darstellt. Entfernen des Programms  
  
## Rückgabewert  
 Bei Erfolg gibt `S_OK`zurück. andernfalls gibt einen Fehlercode zurück.  
  
## Hinweise  
 Sobald entfernt, ist der Knoten Programm nicht mehr verfügbar, auf Programm Informationen abgefragt werden soll.  
  
 Um ein Programm unter dem Knoten bereitzustellen, rufen Sie die [PublishProgramNode](../../../extensibility/debugger/reference/idebugprogrampublisher2-publishprogramnode.md)\-Methode auf.  
  
## Siehe auch  
 [IDebugProgramPublisher2](../../../extensibility/debugger/reference/idebugprogrampublisher2.md)   
 [IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md)   
 [PublishProgramNode](../../../extensibility/debugger/reference/idebugprogrampublisher2-publishprogramnode.md)