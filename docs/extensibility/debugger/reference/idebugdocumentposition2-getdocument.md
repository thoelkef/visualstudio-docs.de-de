---
title: "IDebugDocumentPosition2::GetDocument | Microsoft Docs"
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
  - "IDebugDocumentPosition2::GetDocument"
helpviewer_keywords: 
  - "IDebugDocumentPosition2::GetDocument"
ms.assetid: eaa172c9-5748-4ce1-a0e2-33c2063f6752
caps.latest.revision: 10
caps.handback.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
---
# IDebugDocumentPosition2::GetDocument
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Ruft das enthaltende Dokument ab.  
  
## Syntax  
  
```cpp#  
HRESULT GetDocument(   
   IDebugDocument2** ppDoc  
);  
```  
  
```c#  
int GetDocument(   
   out IDebugDocument2 ppDoc  
);  
```  
  
#### Parameter  
 `ppDoc`  
 \[out\]  Gibt ein [IDebugDocument2](../../../extensibility/debugger/reference/idebugdocument2.md)\-Objekt zurück, das das Dokument darstellt, das diese Position enthält.  
  
## Rückgabewert  
 Bei Erfolg gibt `S_OK`zurück. andernfalls gibt einen Fehlercode zurück.  
  
## Siehe auch  
 [IDebugDocumentPosition2](../../../extensibility/debugger/reference/idebugdocumentposition2.md)   
 [IDebugDocument2](../../../extensibility/debugger/reference/idebugdocument2.md)