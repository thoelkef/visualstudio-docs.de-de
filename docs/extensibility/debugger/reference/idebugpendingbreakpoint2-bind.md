---
title: "IDebugPendingBreakpoint2::Bind | Microsoft Docs"
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
  - "IDebugPendingBreakpoint2::Bind"
helpviewer_keywords: 
  - "Bind-Methode"
  - "IDebugPendingBreakpoint2::Bind-Methode"
ms.assetid: 46e3f307-219d-40cd-a929-d41399c60ecf
caps.latest.revision: 8
caps.handback.revision: 8
ms.author: "gregvanl"
manager: "ghogen"
---
# IDebugPendingBreakpoint2::Bind
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Umschließt den anstehenden Haltepunkt zu einem oder mehreren Code speicherorten.  
  
## Syntax  
  
```cpp#  
HRESULT Bind(   
   void   
);  
```  
  
```c#  
int Bind();  
```  
  
## Rückgabewert  
 Bei Erfolg gibt `S_OK`zurück. andernfalls gibt einen Fehlercode zurück.  Gibt `E_BP_DELETED` zurück, wenn der Haltepunkt gelöscht wurde.  
  
## Hinweise  
 Wenn diese Methode aufgerufen wird, sollte eine Debug\- Modul \(DE\) versuchen, diesen anstehenden Haltepunkt zu den gesamten Code speicherorten binden, die übereinstimmen.  
  
 Nach dem Beenden dieser Methode muss der Aufrufer auf Ereignisse jeweils darauf warten, dass der ausstehenden Haltepunkt gebunden hat, oder es handelt sich um Fehler geschlossen, bevor dieser Aufrufe davon ausgegangen wird, [EnumBoundBreakpoints](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-enumboundbreakpoints.md) oder [EnumErrorBreakpoints](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-enumerrorbreakpoints.md).methods alle Grenzen\- oder Misserfolg von Haltepunkten auflistet.  
  
## Siehe auch  
 [IDebugPendingBreakpoint2](../../../extensibility/debugger/reference/idebugpendingbreakpoint2.md)   
 [IDebugBreakpointBoundEvent2](../../../extensibility/debugger/reference/idebugbreakpointboundevent2.md)   
 [IDebugBreakpointErrorEvent2](../../../extensibility/debugger/reference/idebugbreakpointerrorevent2.md)   
 [EnumBoundBreakpoints](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-enumboundbreakpoints.md)   
 [EnumErrorBreakpoints](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-enumerrorbreakpoints.md)