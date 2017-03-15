---
title: "IDebugDisassemblyStream2::GetDocument | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugDisassemblyStream2::GetDocument"
helpviewer_keywords: 
  - "IDebugDisassemblyStream2::GetDocument"
ms.assetid: 3d039a44-ebaa-4413-ac18-7cfd92c408bd
caps.latest.revision: 9
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 9
---
# IDebugDisassemblyStream2::GetDocument
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Ruft das Quelldokument ab, das diesem Schwellenwert zugeordnet ist.  
  
## Syntax  
  
```cpp#  
HRESULT GetDocument(   
   BSTR              bstrDocumentUrl,  
   IDebugDocument2** ppDocument  
);  
```  
  
```c#  
int GetDocument(   
   string              bstrDocumentUrl,  
   out IDebugDocument2 ppDocument  
);  
```  
  
#### Parameter  
 `bstrDocumentUrl`  
 \[in\]  Das Dokument URLs.  
  
 `ppDocument`  
 \[out\]  Gibt ein [IDebugDocument2](../../../extensibility/debugger/reference/idebugdocument2.md)\-Objekt zurück, das das Dokument darstellt.  
  
## Rückgabewert  
 Bei Erfolg gibt `S_OK`zurück. andernfalls gibt einen Fehlercode zurück.  
  
## Hinweise  
 Diese Methode wird von Debugsymbolinformationen auf Module implementiert, die Textdokumente haben, die nicht in einer tatsächlichen Datei gespeichert werden.  
  
## Siehe auch  
 [IDebugDisassemblyStream2](../../../extensibility/debugger/reference/idebugdisassemblystream2.md)   
 [IDebugDocument2](../../../extensibility/debugger/reference/idebugdocument2.md)