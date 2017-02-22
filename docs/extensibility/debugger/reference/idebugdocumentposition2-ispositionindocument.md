---
title: "IDebugDocumentPosition2::IsPositionInDocument | Microsoft Docs"
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
  - "IDebugDocumentPosition2::IsPositionInDocument"
helpviewer_keywords: 
  - "IDebugDocumentPosition2::IsPositionInDocument"
ms.assetid: d5cf57cb-b93b-4e1d-bec9-185f4fe8668d
caps.latest.revision: 10
caps.handback.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
---
# IDebugDocumentPosition2::IsPositionInDocument
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Bestimmt, ob die Position des Dokuments im bestimmten Dokument enthalten ist.  
  
## Syntax  
  
```cpp#  
HRESULT IsPositionInDocument(   
   IDebugDocument2* pDoc  
);  
```  
  
```c#  
int IsPositionInDocument(   
   IDebugDocument2 pDoc  
);  
```  
  
#### Parameter  
 `pDoc`  
 \[in\]  Das [IDebugDocument2](../../../extensibility/debugger/reference/idebugdocument2.md)\-Objekt, das den enthaltenen Dokumente kandidaten darstellt.  
  
## Rückgabewert  
 Bei Erfolg gibt `S_OK`zurück. andernfalls gibt einen Fehlercode zurück.  
  
## Hinweise  
 Diese Methode wird hauptsächlich in den Festlegen von Haltepunkten in [IDebugDocument2](../../../extensibility/debugger/reference/idebugdocument2.md)\-Schnittstellen verwendet.  Während Dokumente geladen werden, wird die Position des Haltepunkts bestimmen aufgerufen, wenn das Dokument über diese Position enthält.  
  
## Siehe auch  
 [IDebugDocumentPosition2](../../../extensibility/debugger/reference/idebugdocumentposition2.md)   
 [IDebugDocument2](../../../extensibility/debugger/reference/idebugdocument2.md)