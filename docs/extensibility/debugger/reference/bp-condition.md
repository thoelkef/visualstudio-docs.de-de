---
title: "BP_CONDITION | Microsoft Docs"
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
  - "BP_CONDITION"
helpviewer_keywords: 
  - "BP_CONDITION-Struktur"
ms.assetid: 407f87a3-2878-429b-8c65-b68feb36622a
caps.latest.revision: 10
caps.handback.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
---
# BP_CONDITION
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Beschreibt die Bedingungen, unter denen ein Haltepunkt auslöst.  
  
## Syntax  
  
```cpp#  
typedef struct _BP_CONDITION {   
   IDebugThread2* pThread;  
   BP_COND_STYLE  styleCondition;  
   BSTR           bstrContext;  
   BSTR           bstrCondition;  
   UINT           nRadix;  
} BP_CONDITION;  
```  
  
```c#  
public struct BP_CONDITION {   
   public IDebugThread2 pThread;  
   public uint          styleCondition;  
   public string        bstrContext;  
   public string        bstrCondition;  
   public uint          nRadix;  
};  
```  
  
## Mitglieder  
 `pThread`  
 Das [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md)\-Objekt, das den aktiven Thread für die Anwendung darstellt, die den Haltepunkt enthält.  
  
 `styleCondition`  
 Ein Wert aus der [BP\_COND\_STYLE](../../../extensibility/debugger/reference/bp-cond-style.md)\-Enumeration, die das Format dieser Haltepunkt zustandes beschreibt.  
  
 `bstrContext`  
 Die Position des Haltepunkts.  
  
 `bstrCondition`  
 Die Auslösung Zustand des Haltepunkts.  
  
 `nRadix`  
 Wenn zu verwendende Basisklasse, die alle numerischen Daten ausgewertet werden.  
  
## Hinweise  
 Diese Struktur ist ein Mitglied der [BP\_REQUEST\_INFO](../../../extensibility/debugger/reference/bp-request-info.md) und [BP\_REQUEST\_INFO2](../../../extensibility/debugger/reference/bp-request-info2.md) Strukturen.  
  
 Diese Struktur wird auch als Parameter an die [SetCondition](../../../extensibility/debugger/reference/idebugboundbreakpoint2-setcondition.md) und [SetCondition](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-setcondition.md)\-Methode übergeben.  
  
## Anforderungen  
 Header: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## Siehe auch  
 [Strukturen und Unions](../../../extensibility/debugger/reference/structures-and-unions.md)   
 [BP\_REQUEST\_INFO](../../../extensibility/debugger/reference/bp-request-info.md)   
 [BP\_REQUEST\_INFO2](../../../extensibility/debugger/reference/bp-request-info2.md)   
 [SetCondition](../../../extensibility/debugger/reference/idebugboundbreakpoint2-setcondition.md)   
 [SetCondition](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-setcondition.md)   
 [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md)   
 [BP\_COND\_STYLE](../../../extensibility/debugger/reference/bp-cond-style.md)