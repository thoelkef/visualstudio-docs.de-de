---
title: "REFERENCE_COMPARE | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "REFERENCE_COMPARE"
helpviewer_keywords: 
  - "REFERENCE_COMPARE-enumeration"
ms.assetid: e31cdc78-f621-498b-9ca4-aefa790b9f6f
caps.latest.revision: 8
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 8
---
# REFERENCE_COMPARE
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Gibt den Typ des Vergleichs nach Verweisen auf.  
  
## Syntax  
  
```cpp#  
enum enum_REFERENCE_COMPARE {   
   REF_COMPARE_EQUAL        = 0x0001,  
   REF_COMPARE_LESS_THAN    = 0x0002,  
   REF_COMPARE_GREATER_THAN = 0x0003  
};  
typedef DWORD REFERENCE_COMPARE;  
```  
  
```c#  
public enum enum_REFERENCE_COMPARE {   
   REF_COMPARE_EQUAL        = 0x0001,  
   REF_COMPARE_LESS_THAN    = 0x0002,  
   REF_COMPARE_GREATER_THAN = 0x0003  
};  
```  
  
## Mitglieder  
 REF\_COMPARE\_EQUAL  
 Gibt gleich Vergleich an.  
  
 REF\_COMPARE\_LESS\_THAN  
 Gibt ein " Kleiner als " \- Vergleich an.  
  
 REF\_COMPARE\_GREATER\_THAN  
 Gibt ein Größer\-als\-Vergleich an.  
  
## Hinweise  
 Übergabe als Argument an die [Vergleichen](../../../extensibility/debugger/reference/idebugreference2-compare.md)\-Methode.  
  
## Anforderungen  
 Header: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## Siehe auch  
 [Enumerationen](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [Vergleichen](../../../extensibility/debugger/reference/idebugreference2-compare.md)