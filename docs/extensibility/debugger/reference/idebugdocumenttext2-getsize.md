---
title: "IDebugDocumentText2::GetSize | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugDocumentText2::GetSize"
helpviewer_keywords: 
  - "IDebugDocumentText2::GetSize"
ms.assetid: bf515a8f-dcee-4004-8f81-543d547ceaae
caps.latest.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 10
---
# IDebugDocumentText2::GetSize
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Ruft die Größe des Texts an dieser Position im Dokument ab.  
  
## Syntax  
  
```cpp#  
HRESULT GetSize(   
   ULONG* pcNumLines,  
   ULONG* pcNumChars  
);  
```  
  
```c#  
int GetSize(   
   ref uint pcNumLines,  
   ref uint pcNumChars  
);  
```  
  
#### Parameter  
 `pcNumLines`  
 \[out\]  Gibt die Anzahl von Textzeilen zurückgegeben.  
  
 `pcNumChars`  
 \[out\]  Gibt die Anzahl der Zeichen des Texts zurück.  
  
## Rückgabewert  
 Bei Erfolg gibt `S_OK`zurück. andernfalls gibt einen Fehlercode zurück.  
  
## Hinweise  
 \[C\+\+\] Es wenn ein bestimmter Wert nicht erwünscht ist, führen Sie NULL für den Parameter.  
  
 \[Nur C\#\] müssen beide Parameter angegeben werden.  
  
## Siehe auch  
 [IDebugDocumentText2](../../../extensibility/debugger/reference/idebugdocumenttext2.md)