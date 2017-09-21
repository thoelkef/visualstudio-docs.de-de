---
title: "CONTEXT_COMPARE | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CONTEXT_COMPARE"
helpviewer_keywords: 
  - "CONTEXT_COMPARE-enumeration"
ms.assetid: 701ed61c-a320-4c20-a335-0b840024abc0
caps.latest.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 10
---
# CONTEXT_COMPARE
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Gibt die Kriterien zum Vergleichen von zwei Speicher kontexten an.  
  
## Syntax  
  
```cpp#  
enum enum_CONTEXT_COMPARE {   
   CONTEXT_EQUAL                 = 0x0001,  
   CONTEXT_LESS_THAN             = 0x0002,  
   CONTEXT_GREATER_THAN          = 0x0003,  
   CONTEXT_LESS_THAN_OR_EQUAL    = 0x0004,  
   CONTEXT_GREATER_THAN_OR_EQUAL = 0x0005,  
   CONTEXT_SAME_SCOPE            = 0x0006,  
   CONTEXT_SAME_FUNCTION         = 0x0007,  
   CONTEXT_SAME_MODULE           = 0x0008,  
   CONTEXT_SAME_PROCESS          = 0x0009  
};  
typedef DWORD CONTEXT_COMPARE;  
```  
  
```c#  
public enum enum_CONTEXT_COMPARE {   
   CONTEXT_EQUAL                 = 0x0001,  
   CONTEXT_LESS_THAN             = 0x0002,  
   CONTEXT_GREATER_THAN          = 0x0003,  
   CONTEXT_LESS_THAN_OR_EQUAL    = 0x0004,  
   CONTEXT_GREATER_THAN_OR_EQUAL = 0x0005,  
   CONTEXT_SAME_SCOPE            = 0x0006,  
   CONTEXT_SAME_FUNCTION         = 0x0007,  
   CONTEXT_SAME_MODULE           = 0x0008,  
   CONTEXT_SAME_PROCESS          = 0x0009  
};  
```  
  
## Mitglieder  
 CONTEXT\_EQUAL  
 Suchen Sie den ersten in der Liste Arbeitsspeicher, die gleich dem Ziel Arbeitsspeicher Elementkontext vorhanden ist.  
  
 CONTEXT\_LESS\_THAN  
 Suchen Sie den ersten in der Liste Arbeitsspeicher, die kleiner ist als der Ziel Arbeitsspeicher Elementkontext.  
  
 CONTEXT\_GREATER\_THAN  
 Suchen Sie den ersten in der Liste Arbeitsspeicher größer ist als der Ziel Arbeitsspeicher Elementkontext.  
  
 CONTEXT\_LESS\_THAN\_OR\_EQUAL  
 Suchen Sie den ersten in der Liste Arbeitsspeicher, die kleiner oder gleich dem Ziel Arbeitsspeicher Elementkontext vorhanden ist.  
  
 CONTEXT\_GREATER\_THAN\_OR\_EQUAL  
 Suchen Sie den ersten in der Liste Arbeitsspeicher größer oder gleich dem Ziel Arbeitsspeicher Elementkontext vorhanden ist.  
  
 CONTEXT\_SAME\_SCOPE  
 Suchen Sie den ersten in der Liste Arbeitsspeicher, die sich im selben Bereich wie der Speicher Ziel Kontext ist.  
  
 CONTEXT\_SAME\_FUNCTION  
 Suchen Sie den ersten in der Liste Speicher in derselben Funktion wie der Speicher Ziel Bereich befindet.  
  
 CONTEXT\_SAME\_MODULE  
 Suchen Sie den ersten in der Liste Arbeitsspeicher, die in demselben Modul als Ziel Arbeitsspeicher Elementkontext vorhanden ist.  
  
 CONTEXT\_SAME\_PROCESS  
 Suchen Sie den ersten in der Liste Arbeitsspeicher im gleichen Prozess wie der Speicher Ziel Kontext ist.  
  
## Hinweise  
 Übergabe als Argument an die [Vergleichen](../../../extensibility/debugger/reference/idebugmemorycontext2-compare.md)\-Methode.  
  
 Diese Werte werden verwendet, um den ersten Speicher in einer Liste zu suchen, die die angegebenen Vergleichs kriterien erfüllt.  Ein Kontext ist eine Liste von Speicher im Arbeitsspeicher kontexten angegeben, um sich durch die gegen `IDebugMemoryContext2::Compare`\-Methode verglichen werden soll.  Der erste in der Liste Arbeitsspeicher, für die der Vergleichsoperator `true` ist, wird anschließend zurückgegeben.  
  
## Anforderungen  
 Header: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## Siehe auch  
 [Enumerationen](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [Vergleichen](../../../extensibility/debugger/reference/idebugmemorycontext2-compare.md)