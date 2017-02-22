---
title: "IDebugBoundBreakpoint2 | Microsoft Docs"
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
  - "IDebugBoundBreakpoint2"
helpviewer_keywords: 
  - "IDebugBoundBreakpoint2-Schnittstelle"
ms.assetid: df33c52e-ded2-48a0-951d-1f36c8fc922e
caps.latest.revision: 11
caps.handback.revision: 11
ms.author: "gregvanl"
manager: "ghogen"
---
# IDebugBoundBreakpoint2
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Diese Schnittstelle stellt einen Haltepunkt dar, der an einem Speicherort des Codes gebunden ist.  
  
## Syntax  
  
```  
IDebugBoundBreakpoint2 : IUnknown  
```  
  
## Hinweise für Implementierer  
 Das Debugmodul \(DE\) implementiert diese Schnittstelle als Teil der Unterstützung für Haltepunkte.  
  
## Hinweise für Aufrufer  
 Ein Aufruf von [Binden](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-bind.md) erstellt diese Schnittstelle.  Aufrufe von [GetBreakpoint](../../../extensibility/debugger/reference/idebugbreakpointunboundevent2-getbreakpoint.md) und [Weiter](../../../extensibility/debugger/reference/ienumdebugboundbreakpoints2-next.md) können auch Abrufen dieser Schnittstelle.  
  
## Methoden in die Vtable\-Reihenfolge  
 In der folgenden Tabelle werden die Methoden von `IDebugBoundBreakpoint2`an.  
  
|Methode|Beschreibung|  
|-------------|------------------|  
|[GetPendingBreakpoint](../../../extensibility/debugger/reference/idebugboundbreakpoint2-getpendingbreakpoint.md)|Ruft den anstehenden Haltepunkt ab, von dem der angegebene gebundene Haltepunkt erstellt wurde.|  
|[GetState](../../../extensibility/debugger/reference/idebugboundbreakpoint2-getstate.md)|Ruft den Zustand dieses springen Haltepunkt ab.|  
|[GetHitCount](../../../extensibility/debugger/reference/idebugboundbreakpoint2-gethitcount.md)|Ruft die aktuelle Trefferanzahl für diese Bindung Haltepunkt ab.|  
|[GetBreakpointResolution](../../../extensibility/debugger/reference/idebugboundbreakpoint2-getbreakpointresolution.md)|Ruft die Auflösung von Haltepunkt ab, die diesen Haltepunkt beschreibt.|  
|[Aktivieren](../../../extensibility/debugger/reference/idebugboundbreakpoint2-enable.md)|Aktiviert oder deaktiviert den Haltepunkt.|  
|[SetHitCount](../../../extensibility/debugger/reference/idebugboundbreakpoint2-sethitcount.md)|Legt die Trefferanzahl für diese Bindung fest. Haltepunkte|  
|[SetCondition](../../../extensibility/debugger/reference/idebugboundbreakpoint2-setcondition.md)|Legt die Änderungen oder Bedingung, die mit diesem gebundenen Haltepunkt.|  
|[SetPassCount](../../../extensibility/debugger/reference/idebugboundbreakpoint2-setpasscount.md)|Legt ein Objekt fest oder ändern sich die Anzahl übergeben, die dieser gebundenen Haltepunkt zugeordnet ist.|  
|[Löschen](../../../extensibility/debugger/reference/idebugboundbreakpoint2-delete.md)|Löscht den Haltepunkt.|  
  
## Anforderungen  
 Header: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## Siehe auch  
 [GetBreakpoint](../../../extensibility/debugger/reference/idebugbreakpointunboundevent2-getbreakpoint.md)   
 [Weiter](../../../extensibility/debugger/reference/ienumdebugboundbreakpoints2-next.md)   
 [Binden](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-bind.md)