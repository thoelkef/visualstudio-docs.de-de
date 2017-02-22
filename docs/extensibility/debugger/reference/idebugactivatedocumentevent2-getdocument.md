---
title: "IDebugActivateDocumentEvent2::GetDocument | Microsoft Docs"
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
  - "IDebugActivateDocumentEvent2::GetDocument"
helpviewer_keywords: 
  - "GetDocument-Methode"
  - "IDebugActivateDocumentEvent2::GetDocument-Methode"
ms.assetid: b3c32f1b-f3de-409d-920d-ba7b3fa84fcd
caps.latest.revision: 10
caps.handback.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
---
# IDebugActivateDocumentEvent2::GetDocument
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Ruft das Dokument ab, um zu aktivieren.  
  
## Syntax  
  
```cpp#  
HRESULT GetDocument (   
   IDebugDocument2** ppDoc  
);  
```  
  
```c#  
int GetDocument (   
   out IDebugDocument2 ppDoc  
);  
```  
  
#### Parameter  
 `ppDoc`  
 \[out\]  Gibt ein [IDebugDocument2](../../../extensibility/debugger/reference/idebugdocument2.md)\-Objekt zurück, das das zu aktivierende Dokument darstellt.  
  
## Rückgabewert  
 Bei Erfolg gibt `S_OK`zurück. andernfalls gibt einen Fehlercode zurück.  
  
## Siehe auch  
 [IDebugActivateDocumentEvent2](../../../extensibility/debugger/reference/idebugactivatedocumentevent2.md)   
 [IDebugDocument2](../../../extensibility/debugger/reference/idebugdocument2.md)