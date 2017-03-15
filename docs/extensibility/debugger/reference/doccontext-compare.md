---
title: "DOCCONTEXT_COMPARE | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "DOCCONTEXT_COMPARE"
helpviewer_keywords: 
  - "DOCCONTEXT_COMPARE-enumeration"
ms.assetid: ed947c34-b07e-4b69-8381-b6e7cb842862
caps.latest.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 10
---
# DOCCONTEXT_COMPARE
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Gibt die Kriterien zum Vergleichen von zwei Dokumenten kontexten an.  
  
## Syntax  
  
```cpp#  
enum enum_DOCCONTEXT_COMPARE {   
   DOCCONTEXT_EQUAL         = 0x0001,  
   DOCCONTEXT_LESS_THAN     = 0x0002,  
   DOCCONTEXT_GREATER_THAN  = 0x0003,  
   DOCCONTEXT_SAME_DOCUMENT = 0x0004  
};  
typedef DWORD DOCCONTEXT_COMPARE;  
```  
  
```c#  
enum enum_DOCCONTEXT_COMPARE {   
   DOCCONTEXT_EQUAL         = 0x0001,  
   DOCCONTEXT_LESS_THAN     = 0x0002,  
   DOCCONTEXT_GREATER_THAN  = 0x0003,  
   DOCCONTEXT_SAME_DOCUMENT = 0x0004  
};  
```  
  
## Mitglieder  
 DOCCONTEXT\_EQUAL  
 Suchen Sie den ersten Dokumentenkontext in der Liste, die gleich dem Ziel Dokumente Elementkontext vorhanden ist.  
  
 DOCCONTEXT\_LESS\_THAN  
 Suchen Sie den ersten Dokumentenkontext in der Liste, die kleiner ist als der Kontext auf Dokumente.  
  
 DOCCONTEXT\_GREATER\_THAN  
 Suchen Sie den ersten Dokumentenkontext in der Liste, die größer ist als der Kontext auf Dokumente.  
  
 DOCCONTEXT\_SAME\_DOCUMENT  
 Suchen Sie den ersten Dokumentenkontext in der Liste, die im selben Dokument wie das Ziel Dokumente Elementkontext vorhanden ist.  
  
## Hinweise  
 Übergabe als Argument an die [Vergleichen](../../../extensibility/debugger/reference/idebugdocumentcontext2-compare.md)\-Methode.  
  
 Diese Werte werden verwendet, um Kriterien eines Vergleichs zum Suchen des ersten kontexts Dokumente in einer Liste anzugeben.  Ein Dokumentenkontext ist eine Liste von Dokumenten kontexten angegeben, um sich durch die gegen `IDebugDocumentContext2::Compare`\-Methode verglichen werden soll.  Der erste Dokumentenkontext in der Liste, für die der Vergleichsoperator `true` ist, wird anschließend zurückgegeben.  
  
## Anforderungen  
 Header: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## Siehe auch  
 [Enumerationen](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [Vergleichen](../../../extensibility/debugger/reference/idebugdocumentcontext2-compare.md)