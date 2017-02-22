---
title: "IDebugActivateDocumentEvent2::GetDocumentContext | Microsoft Docs"
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
  - "IDebugActivateDocumentEvent2::GetDocumentContext"
helpviewer_keywords: 
  - "GetDocumentContext-Methode"
  - "IDebugActivateDocumentEvent2::GetDocumentContext-Methode"
ms.assetid: e7472069-7337-4ef4-8f8a-8c027a2e22f4
caps.latest.revision: 10
caps.handback.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
---
# IDebugActivateDocumentEvent2::GetDocumentContext
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Ruft den Dokumentenkontext ab, der die Position im Dokument beschreibt, das durch das Debuggen aktiviert Paket ausgeführt werden soll.  
  
## Syntax  
  
```cpp#  
HRESULT GetDocumentContext (   
   IDebugDocumentContext2** ppDocContext  
);  
```  
  
```c#  
int GetDocumentContext (   
   out IDebugDocumentContext2 ppDocContext  
);  
```  
  
#### Parameter  
 `ppDocContext`  
 \[out\]  Gibt ein [IDebugDocumentContext2](../../../extensibility/debugger/reference/idebugdocumentcontext2.md)\-Objekt zurück, das eine Position in einer Quelldatei Dokument darstellt.  
  
## Hinweise  
 Diese Position kann verwendet werden, um die Einfügemarke anzuzeigen, z.  
  
## Rückgabewert  
 Bei Erfolg gibt `S_OK`zurück. andernfalls gibt einen Fehlercode zurück.  
  
## Siehe auch  
 [IDebugActivateDocumentEvent2](../../../extensibility/debugger/reference/idebugactivatedocumentevent2.md)   
 [IDebugDocumentContext2](../../../extensibility/debugger/reference/idebugdocumentcontext2.md)