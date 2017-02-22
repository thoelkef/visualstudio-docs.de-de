---
title: "IDebugCodeContext2::GetDocumentContext | Microsoft Docs"
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
  - "IDebugCodeContext2::GetDocumentContext"
helpviewer_keywords: 
  - "IDebugCodeContext2::GetDocumentContext"
ms.assetid: d552cc92-963f-43c1-949f-ae6b63a427b8
caps.latest.revision: 9
caps.handback.revision: 9
ms.author: "gregvanl"
manager: "ghogen"
---
# IDebugCodeContext2::GetDocumentContext
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Ruft den Dokumentenkontext ab, der für diesen Code Elementkontext entspricht.  Der Dokumentenkontext stellt eine Position in der Quelldatei dar, die zum Quellcode entspricht, der diese Anweisung generiert hat.  
  
## Syntax  
  
```cpp#  
HRESULT GetDocumentContext(   
   IDebugDocumentContext2** ppSrcCxt  
);  
```  
  
```c#  
int GetDocumentContext(   
   out IDebugDocumentContext2 ppSrcCxt  
);  
```  
  
#### Parameter  
 `ppSrcCxt`  
 \[out\]  Gibt das [IDebugDocumentContext2](../../../extensibility/debugger/reference/idebugdocumentcontext2.md)\-Objekt zurück, das dem Code Elementkontext entspricht.  
  
## Rückgabewert  
 Bei Erfolg gibt `S_OK`zurück. andernfalls gibt einen Fehlercode zurück.  
  
## Hinweise  
 Im Allgemeinen kann es sich um den Dokumentenkontext für eine Position in einer Quelldatei gespeichert werden, während der Code Elementkontext eine Position einer Code in einem datenstrom Ausführen der Anweisung.  
  
## Siehe auch  
 [IDebugCodeContext2](../../../extensibility/debugger/reference/idebugcodecontext2.md)   
 [IDebugDocumentContext2](../../../extensibility/debugger/reference/idebugdocumentcontext2.md)