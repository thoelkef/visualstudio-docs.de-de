---
title: "PENDING_BP_STATE_INFO | Microsoft Docs"
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
  - "PENDING_BP_STATE_INFO"
helpviewer_keywords: 
  - "PENDING_BP_STATE_INFO-Struktur"
ms.assetid: 4d73ceff-43f9-4e95-8dba-88e1fab2def3
caps.latest.revision: 8
caps.handback.revision: 8
ms.author: "gregvanl"
manager: "ghogen"
---
# PENDING_BP_STATE_INFO
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Enthält Informationen über den Zustand eines Haltepunkts, kann der Code an einen Speicherort zu binden.  
  
## Syntax  
  
```cpp#  
typedef struct _tagPENDING_BP_STATE_INFO {   
   PENDING_BP_STATE       state;  
   PENDING_BP_STATE_FLAGS flags;  
} PENDING_BP_STATE_INFO;  
```  
  
```c#  
public struct PENDING_BP_STATE_INFO {   
   public uint state;  
   public uint flags;  
};  
```  
  
## Mitglieder  
 \-Zustand  
 Ein Wert aus der [PENDING\_BP\_STATE](../../../extensibility/debugger/reference/pending-bp-state.md)\-Enumeration, der den Zustand des anstehenden Haltepunkts angibt.  
  
 flags  
 Eine Kombination von Flags aus der [PENDING\_BP\_STATE\_FLAGS](../../../extensibility/debugger/reference/pending-bp-state-flags.md)\-Enumeration, die angibt, ob der Haltepunkt virtualisiert wird.  
  
## Hinweise  
 Diese Struktur wird auf die [GetState](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-getstate.md)\-Methode übergeben, in der er eingetragen wird.  
  
## Anforderungen  
 Header: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## Siehe auch  
 [Strukturen und Unions](../../../extensibility/debugger/reference/structures-and-unions.md)   
 [GetState](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-getstate.md)   
 [PENDING\_BP\_STATE](../../../extensibility/debugger/reference/pending-bp-state.md)   
 [PENDING\_BP\_STATE\_FLAGS](../../../extensibility/debugger/reference/pending-bp-state-flags.md)