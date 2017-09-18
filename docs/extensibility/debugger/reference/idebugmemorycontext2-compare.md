---
title: "IDebugMemoryContext2::Compare | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugMemoryContext2::Compare"
helpviewer_keywords: 
  - "IDebugMemoryContext2::Compare-Methode"
  - "Compare-Methode"
ms.assetid: c51b5128-848e-4d8e-b2e9-1161339763c3
caps.latest.revision: 14
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 14
---
# IDebugMemoryContext2::Compare
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Vergleicht den Arbeitsspeicher Elementkontext zu jedem Kontext im angegebenen Array nach der Art und Weise, in der angegeben wird, vergleicht die Flags und gibt den Index des ersten Kontext zurück, der übereinstimmt.  
  
## Syntax  
  
```cpp#  
HRESULT Compare(   
   CONTEXT_COMPARE        compare,  
   IDebugMemoryContext2** rgpMemoryContextSet,  
   DWORD                  dwMemoryContextSetLen,  
   DWORD*                 pdwMemoryContext  
);  
```  
  
```c#  
int Compare(  
   enum_CONTEXT_COMPARE   compare,   
   IDebugMemoryContext2[] rgpMemoryContextSet,   
   uint                   dwMemoryContextSetLen,   
   out uint               pdwMemoryContext  
);  
```  
  
#### Parameter  
 `compare`  
 \[in\]  Ein Wert aus der [CONTEXT\_COMPARE](../../../extensibility/debugger/reference/context-compare.md)\-Enumeration, der den Typ des Vergleiches bestimmt.  
  
 `rgpMemoryContextSet`  
 \[in\]  Ein Array von Verweisen auf die zu vergleichende [IDebugMemoryContext2](../../../extensibility/debugger/reference/idebugmemorycontext2.md)\-Objekten.  
  
 `dwMemoryContextSetLen`  
 \[in\]  Die Anzahl von Kontexten im `rgpMemoryContextSet` Array.  
  
 `pdwMemoryContext`  
 \[out\]  Gibt den Index des ersten kontexts Arbeitsspeicher zurück, der den Vergleich erfüllt.  
  
## Rückgabewert  
 Bei Erfolg gibt `S_OK`zurück. andernfalls gibt einen Fehlercode zurück.  Gibt `E_COMPARE_CANNOT_COMPARE` zurück, wenn die beiden Kontexte nicht verglichen werden können.  
  
## Hinweise  
 Ein Modul \(Debug\) DE muss alle Typen werden nicht unterstützt, aber es muss `CONTEXT_EQUAL`, `CONTEXT_LESS_THAN`, `CONTEXT_GREATER_THAN` und mindestens `CONTEXT_SAME_SCOPE`unterstützen.  
  
## Siehe auch  
 [IDebugMemoryContext2](../../../extensibility/debugger/reference/idebugmemorycontext2.md)   
 [CONTEXT\_COMPARE](../../../extensibility/debugger/reference/context-compare.md)