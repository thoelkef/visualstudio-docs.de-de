---
title: "IDebugProgramPublisher2::UnpublishProgram | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugProgramPublisher2::UnpublishProgram"
helpviewer_keywords: 
  - "IDebugProgramPublisher2::UnpublishProgram"
ms.assetid: 627e7d38-b2ac-4873-9a40-37ff7f47cd1d
caps.latest.revision: 9
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 9
---
# IDebugProgramPublisher2::UnpublishProgram
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Ermöglicht das Debuggen eines Programms nicht verfügbar.  
  
## Syntax  
  
```cpp  
HRESULT UnpublishProgram(  
   IUnknown* pDebuggeeInterface  
);  
```  
  
```c#  
int UnpublishProgram(  
   object pDebuggeeInterface  
);  
```  
  
#### Parameter  
 `pDebuggeeInterface`  
 \[in\]  Eine `IUnknown`\-Schnittstelle zum Programm.  Dies ist derselbe Wert, der der [PublishProgram](../../../extensibility/debugger/reference/idebugprogrampublisher2-publishprogram.md)\-Methode angegeben ist, und identifiziert eindeutig das Programm, das entfernt werden soll \(das heißt es als Cookie verwendet\).  
  
## Rückgabewert  
 Bei Erfolg gibt `S_OK`zurück. andernfalls gibt einen Fehlercode zurück.  
  
## Hinweise  
 Um ein Programm zur Verfügung zu stellen die Debugmodule und Debuggen von den Manager der Sitzung, verwenden Sie die [PublishProgram](../../../extensibility/debugger/reference/idebugprogrampublisher2-publishprogram.md)\-Methode.  
  
## Siehe auch  
 [IDebugProgramPublisher2](../../../extensibility/debugger/reference/idebugprogrampublisher2.md)   
 [PublishProgram](../../../extensibility/debugger/reference/idebugprogrampublisher2-publishprogram.md)