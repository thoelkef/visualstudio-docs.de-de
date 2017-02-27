---
title: "IDebugDocumentTextEvents2::onInsertText | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugDocumentTextEvents2::OnInsertText"
helpviewer_keywords: 
  - "IDebugDocumentTextEvents2::onInsertText"
ms.assetid: 6040181f-7288-4a42-953c-d23f74200431
caps.latest.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 10
---
# IDebugDocumentTextEvents2::onInsertText
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Benachrichtigt das Debuggen Paket, das Text in das Dokument eingefügt wurde.  
  
## Syntax  
  
```cpp#  
HRESULT onInsert(   
   TEXT_POSITION pos,  
   DWORD         dwNumToInsert  
);  
```  
  
```c#  
int onInsert(   
   enum_TEXT_POSITION pos,  
   uint               dwNumToInsert  
);  
```  
  
#### Parameter  
 `pos`  
 \[in\]  Eine [TEXT\_POSITION](../../../extensibility/debugger/reference/text-position.md) Struktur, die angibt, wo der Text eingefügt wurde.  
  
 `dwNumToInsert`  
 \[in\]  Gibt die Anzahl der Zeichen des Texts an, die eingefügt wurden.  
  
## Rückgabewert  
 Bei Erfolg gibt `S_OK`zurück. andernfalls gibt einen Fehlercode zurück.  
  
## Siehe auch  
 [IDebugDocumentTextEvents2](../../../extensibility/debugger/reference/idebugdocumenttextevents2.md)   
 [TEXT\_POSITION](../../../extensibility/debugger/reference/text-position.md)