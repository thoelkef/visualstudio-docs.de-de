---
title: "IDebugDocumentContext2::GetStatementRange | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugDocumentContext2::GetStatementRange"
helpviewer_keywords: 
  - "IDebugDocumentContext2::GetStatementRange"
ms.assetid: bc94851a-0ec4-47ea-99c7-0a585e54e726
caps.latest.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 10
---
# IDebugDocumentContext2::GetStatementRange
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Ruft den Bereich für Datei kontexts Dokumente ab oder legt diese fest.  
  
## Syntax  
  
```cpp#  
HRESULT GetStatementRange(   
   TEXT_POSITION* pBegPosition,  
   TEXT_POSITION* pEndPosition  
);  
```  
  
```c#  
int GetStatementRange(   
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
 Ein Bereich ist der Bereich der Anweisung Zeilen mit dem Code einbezogen wurden, an den dieser Dokumentenkontext verweist.  
  
 Zum Abrufen der Bereich des Quellcodes \(z. B. Kommentare\) innerhalb von Dokumenten, rufen Sie die [GetSourceRange](../../../extensibility/debugger/reference/idebugdocumentcontext2-getsourcerange.md)\-Methode auf.  
  
## Beispiel  
 Im folgenden Beispiel wird veranschaulicht, wie diese Methode für ein einfaches `CDebugContext`\-Objekt implementiert, das die [IDebugDocumentContext2](../../../extensibility/debugger/reference/idebugdocumentcontext2.md)\-Schnittstelle verfügbar macht.  In diesem Beispiel wird die Endposition nur ausgeführt, wenn die Anfangsposition kein NULL\-Wert ist.  
  
```cpp#  
HRESULT CDebugContext::GetStatementRange(TEXT_POSITION* pBegPosition,  
                                         TEXT_POSITION* pEndPosition)    
{    
   HRESULT hr;    
  
   // Check for a valid beginning position argument pointer.    
   if (pBegPosition)    
   {    
      // Copy the member TEXT_POSITION into the local pBegPosition.    
      memcpy(pBegPosition, &m_pos, sizeof (TEXT_POSITION));    
  
      // Check for a valid ending position argument pointer.   
     if (pEndPosition)    
      {    
         // Copy the member TEXT_POSITION into the local pEndPosition.    
         memcpy(pEndPosition, &m_pos, sizeof (TEXT_POSITION));    
      }    
      hr = S_OK;    
   }    
   else    
   {    
      hr = E_INVALIDARG;    
   }    
  
   return hr;    
}    
```  
  
## Siehe auch  
 [IDebugDocumentContext2](../../../extensibility/debugger/reference/idebugdocumentcontext2.md)   
 [GetSourceRange](../../../extensibility/debugger/reference/idebugdocumentcontext2-getsourcerange.md)   
 [TEXT\_POSITION](../../../extensibility/debugger/reference/text-position.md)