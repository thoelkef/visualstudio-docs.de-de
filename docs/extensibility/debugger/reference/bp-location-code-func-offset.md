---
title: "BP_LOCATION_CODE_FUNC_OFFSET | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "BP_LOCATION_CODE_FUNC_OFFSET"
helpviewer_keywords: 
  - "BP_LOCATION_CODE_FUNC_OFFSET-Struktur"
ms.assetid: ab38f7ca-fa01-4cf3-a06c-56cbb7207617
caps.latest.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 10
---
# BP_LOCATION_CODE_FUNC_OFFSET
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Beschreibt die Offsetposition eines Haltepunkts in einer Funktion im Code.  
  
## Syntax  
  
```cpp#  
typedef struct _BP_LOCATION_CODE_FUNC_OFFSET {   
   BSTR                     bstrContext;  
   IDebugFunctionPosition2* pFuncPos;  
} BP_LOCATION_CODE_FUNC_OFFSET;  
```  
  
## Mitglieder  
 `bstrContext`  
 Der Kontext des Haltepunkts, i. d. R. eine Methode oder ein Funktionsname, wie auf einer Aufrufliste angezeigt.  
  
 `pFuncPos`  
 Das [IDebugFunctionPosition2](../../../extensibility/debugger/reference/idebugfunctionposition2.md)\-Objekt, das den Namen der Funktion und die relative Position am Anfang der Funktion beschreibt.  
  
## Hinweise  
 Diese Struktur ist ein Mitglied der [BP\_LOCATION](../../../extensibility/debugger/reference/bp-location.md) Struktur als Teil einer Union.  
  
 Der `pFuncPos`\-Member gibt an, wo der function breakpoint festzulegen.  
  
## Anforderungen  
 Header: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## Siehe auch  
 [Strukturen und Unions](../../../extensibility/debugger/reference/structures-and-unions.md)   
 [BP\_LOCATION](../../../extensibility/debugger/reference/bp-location.md)   
 [IDebugFunctionPosition2](../../../extensibility/debugger/reference/idebugfunctionposition2.md)