---
title: "PARSEFLAGS | Microsoft Docs"
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
  - "PARSEFLAGS"
helpviewer_keywords: 
  - "PARSEFLAGS-enumeration"
ms.assetid: 47943f0a-54cb-4493-a62e-5dba97bd4c35
caps.latest.revision: 9
caps.handback.revision: 9
ms.author: "gregvanl"
manager: "ghogen"
---
# PARSEFLAGS
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Gibt an, wie ein Ausdruck analysiert wird.  
  
## Syntax  
  
```cpp#  
enum enum_PARSEFLAGS {   
   PARSE_EXPRESSION            = 0x0001,  
   PARSE_FUNCTION_AS_ADDRESS   = 0x0002,  
   PARSE_DESIGN_TIME_EXPR_EVAL = 0x1000  
};  
typedef DWORD PARSEFLAGS;  
```  
  
```c#  
public enum enum_PARSEFLAGS {   
   PARSE_EXPRESSION            = 0x0001,  
   PARSE_FUNCTION_AS_ADDRESS   = 0x0002,  
   PARSE_DESIGN_TIME_EXPR_EVAL = 0x1000  
};  
```  
  
## Mitglieder  
 PARSE\_EXPRESSION  
 Gibt an, dass der Ausdruck keine Anweisung ist.  
  
 PARSE\_FUNCTION\_AS\_ADDRESS  
 Gibt an, dass der Ausdruck\) als Adresse analysiert werden \(und später ausgewertet werden soll.  
  
 PARSE\_DESIGN\_TIME\_EXPR\_EVAL  
 Gibt an, dass der Ausdruck während der Entwurfszeit analysiert wird \(das heißt wenn ein Designer geöffnet ist\).  
  
## Hinweise  
 Übergabe als Parameter an die [ParseText](../../../extensibility/debugger/reference/idebugexpressioncontext2-parsetext.md) und [Parse](../../../extensibility/debugger/reference/idebugexpressionevaluator-parse.md)\-Methoden.  
  
## Anforderungen  
 Header: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## Siehe auch  
 [Enumerationen](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [ParseText](../../../extensibility/debugger/reference/idebugexpressioncontext2-parsetext.md)   
 [Parse](../../../extensibility/debugger/reference/idebugexpressionevaluator-parse.md)