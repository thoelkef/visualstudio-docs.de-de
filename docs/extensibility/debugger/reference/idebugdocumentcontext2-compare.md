---
title: "IDebugDocumentContext2::Compare | Microsoft Docs"
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
  - "IDebugDocumentContext2::Compare"
helpviewer_keywords: 
  - "IDebugDocumentContext2::Compare"
ms.assetid: 2327b1ba-52d0-42fb-a01e-63cb4b332d2f
caps.latest.revision: 10
caps.handback.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
---
# IDebugDocumentContext2::Compare
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Vergleicht den Dokumentenkontext kontexten Dokumente in ein angegebenes Array.  
  
## Syntax  
  
```cpp#  
HRESULT Compare(   
   DOCCONTEXT_COMPARE       compare,  
   IDebugDocumentContext2** rgpDocContextSet,  
   DWORD                    dwDocContextSetLen,  
   DWORD*                   pdwDocContext  
);  
```  
  
```c#  
int Compare(   
   enum_ DOCCONTEXT_COMPARE compare,  
   IDebugDocumentContext2[] rgpDocContextSet,  
   uint                     dwDocContextSetLen,  
   out uint                 pdwDocContext  
);  
```  
  
#### Parameter  
 `compare`  
 \[in\]  Ein Wert aus der [DOCCONTEXT\_COMPARE](../../../extensibility/debugger/reference/doccontext-compare.md)\-Enumeration, der den Typ des Vergleichs angibt.  
  
 `rgpDocContextSet`  
 \[in\]  Ein Array [IDebugDocumentContext2](../../../extensibility/debugger/reference/idebugdocumentcontext2.md)\-Objekte, die die kontexte vorhanden, die verglichen werden.  
  
 `dwDocContextSetLen`  
 \[in\]  Die Länge des Arrays verglichen werden soll kontexte der Dokumentsequenz.  
  
 `pdwDocContext`  
 \[out\]  Gibt den Index in das `rgpDocContextSet` Array des ersten Dokumenten kontexts zurück, der den Vergleich erfüllt.  
  
## Rückgabewert  
 Gibt `S_OK` zurück, wenn keine Übereinstimmung gefunden wurde.  Gibt `S_FALSE` zurück, wenn keine Übereinstimmung gefunden wurde.  Andernfalls gibt einen Fehlercode zurück.  
  
## Hinweise  
 Die [IDebugDocumentContext2](../../../extensibility/debugger/reference/idebugdocumentcontext2.md)\-Objekte, die in das Array übergeben werden, müssen vom gleichen Debugmodul implementiert werden, um das das `IDebugDocumentContext2`\-Objekt implementiert, die aufgerufen wird. Andernfalls ist der Vergleich nicht gültig.  
  
## Siehe auch  
 [IDebugDocumentContext2](../../../extensibility/debugger/reference/idebugdocumentcontext2.md)   
 [DOCCONTEXT\_COMPARE](../../../extensibility/debugger/reference/doccontext-compare.md)