---
title: "IDebugDocumentContext2::GetDocument | Microsoft Docs"
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
  - "IDebugDocumentContext2::GetDocument"
helpviewer_keywords: 
  - "IDebugDocumentContext2::GetDocument"
ms.assetid: c6d46c5d-ade8-4dc8-9862-8fc7876658c4
caps.latest.revision: 10
caps.handback.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
---
# IDebugDocumentContext2::GetDocument
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Ruft das Dokument ab, das den Dokumentenkontext enthält.  
  
## Syntax  
  
```cpp#  
HRESULT GetDocument(   
   IDebugDocument2** ppDocument  
);  
```  
  
```c#  
int GetDocument(   
   out IDebugDocument2 ppDocument  
);  
```  
  
#### Parameter  
 `ppDocument`  
 \[out\]  Gibt ein [IDebugDocument2](../../../extensibility/debugger/reference/idebugdocument2.md)\-Objekt zurück, das das Dokument darstellt, das den Dokumentenkontext enthält.  
  
## Rückgabewert  
 Bei Erfolg gibt `S_OK`zurück. andernfalls gibt einen Fehlercode zurück.  
  
## Hinweise  
 Diese Methode ist für die Debugmodule, die Dokumente direkt an die IDE bereitstellen.  Andernfalls gibt diese Methode `E_NOTIMPL`zurückgeben.  
  
## Siehe auch  
 [IDebugDocumentContext2](../../../extensibility/debugger/reference/idebugdocumentcontext2.md)   
 [IDebugDocument2](../../../extensibility/debugger/reference/idebugdocument2.md)