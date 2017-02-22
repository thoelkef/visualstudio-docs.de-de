---
title: "BP_PASSCOUNT | Microsoft Docs"
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
  - "BP_PASSCOUNT"
helpviewer_keywords: 
  - "BP_PASSCOUNT-Struktur"
ms.assetid: 791ac175-b897-4c70-873e-240da7e0ac89
caps.latest.revision: 10
caps.handback.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
---
# BP_PASSCOUNT
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Beschreibt die Anzahl und Bedingungen, von denen ein bedingter Haltepunkt ausgelöst wird.  
  
## Syntax  
  
```cpp#  
typedef struct _BP_PASSCOUNT {   
   DWORD              dwPassCount;  
   BP_PASSCOUNT_STYLE stylePassCount;  
} BP_PASSCOUNT;  
```  
  
```c#  
public struct BP_PASSCOUNT {   
   public uint dwPassCount;  
   public uint stylePassCount;  
};  
```  
  
## Mitglieder  
 `dwPassCount`  
 Die über den Haltepunkt zu übergeben sind oft, bevor sie ausgelöst wird.  
  
 `stylePassCount`  
 Ein Wert aus der [BP\_PASSCOUNT\_STYLE](../../../extensibility/debugger/reference/bp-passcount-style.md)\-Enumeration, die das Format der Haltepunkt der haben.  
  
## Hinweise  
 Diese Struktur ist ein Mitglied der [BP\_REQUEST\_INFO](../../../extensibility/debugger/reference/bp-request-info.md) Struktur.  
  
 Diese Struktur wird auch als Parameter an die[SetPassCount](../../../extensibility/debugger/reference/idebugboundbreakpoint2-setpasscount.md) und[SetPassCount](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-setpasscount.md)\-Methode übergeben.  
  
## Anforderungen  
 Header: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## Siehe auch  
 [Strukturen und Unions](../../../extensibility/debugger/reference/structures-and-unions.md)   
 [BP\_REQUEST\_INFO](../../../extensibility/debugger/reference/bp-request-info.md)   
 [SetPassCount](../../../extensibility/debugger/reference/idebugboundbreakpoint2-setpasscount.md)   
 [SetPassCount](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-setpasscount.md)   
 [BP\_PASSCOUNT\_STYLE](../../../extensibility/debugger/reference/bp-passcount-style.md)