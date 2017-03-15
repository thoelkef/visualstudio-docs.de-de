---
title: "IDebugDocumentContext2::GetSourceRange | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugDocumentContext2::GetSourceRange"
helpviewer_keywords: 
  - "IDebugDocumentContext2::GetSourceRange"
ms.assetid: 5903c75e-5390-4d13-9314-1ee276255313
caps.latest.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 10
---
# IDebugDocumentContext2::GetSourceRange
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Ruft den Quellcode kontexts Bereich dieses Dokument ab oder legt diese fest.  
  
## Syntax  
  
```cpp#  
HRESULT GetSourceRange(   
   TEXT_POSITION* pBegPosition,  
   TEXT_POSITION* pEndPosition  
);  
```  
  
```c#  
int GetSourceRange(   
   TEXT_POSITION[] pBegPosition,  
   TEXT_POSITION[] pEndPosition  
);  
```  
  
#### Parameter  
 `pBegPosition`  
 \[in, out\]  Eine [TEXT\_POSITION](../../../extensibility/debugger/reference/text-position.md) Struktur, die mit der Anfangsposition gefüllt wird.  Legen Sie dieses Argument mit einem NULL\-Wert fest, wenn diese Informationen nicht benötigt werden.  
  
 `pEndPosition`  
 \[in, out\]  Eine [TEXT\_POSITION](../../../extensibility/debugger/reference/text-position.md) Struktur, die mit der Endposition gefüllt wird.  Legen Sie dieses Argument mit einem NULL\-Wert fest, wenn diese Informationen nicht benötigt werden.  
  
## Rückgabewert  
 Bei Erfolg gibt `S_OK`zurück. andernfalls gibt einen Fehlercode zurück.  
  
## Hinweise  
 Ein Quellbereich wird der gesamte Bereich des Quellcodes, von der aktuellen Anweisung wieder direkt nach der vorherigen Anweisung, die beitrug Code.  Der Quellbereich wird normalerweise zum Kombinieren von Anweisungen Quelle mit Kommentaren, einschließlich Disassemblys Code im Fenster verwendet.  
  
 Um den Bereich für die Codeanweisungen abzurufen, die innerhalb von Dokumenten kontexts enthalten sind, rufen Sie die [GetStatementRange](../../../extensibility/debugger/reference/idebugdocumentcontext2-getstatementrange.md)\-Methode auf.  
  
## Siehe auch  
 [IDebugDocumentContext2](../../../extensibility/debugger/reference/idebugdocumentcontext2.md)   
 [GetStatementRange](../../../extensibility/debugger/reference/idebugdocumentcontext2-getstatementrange.md)   
 [TEXT\_POSITION](../../../extensibility/debugger/reference/text-position.md)