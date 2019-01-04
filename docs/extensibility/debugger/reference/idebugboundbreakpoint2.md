---
title: IDebugBoundBreakpoint2 | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- IDebugBoundBreakpoint2
helpviewer_keywords:
- IDebugBoundBreakpoint2 interface
ms.assetid: df33c52e-ded2-48a0-951d-1f36c8fc922e
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 9d745bfb4682f92995145cc28967e416baaec35a
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/02/2019
ms.locfileid: "53950841"
---
# <a name="idebugboundbreakpoint2"></a>IDebugBoundBreakpoint2
Diese Schnittstelle stellt einen Haltepunkt an, der an einen Speicherort gebunden ist.  
  
## <a name="syntax"></a>Syntax  
  
```  
IDebugBoundBreakpoint2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Hinweise für Implementierer  
 Die Debug-Engine (DE) implementiert diese Schnittstelle als Teil der Unterstützung für Haltepunkte an.  
  
## <a name="notes-for-callers"></a>Hinweise für Aufrufer  
 Ein Aufruf von [binden](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-bind.md) erstellt diese Schnittstelle. Aufrufe von [GetBreakpoint](../../../extensibility/debugger/reference/idebugbreakpointunboundevent2-getbreakpoint.md) und [Weiter](../../../extensibility/debugger/reference/ienumdebugboundbreakpoints2-next.md) können auch abrufen, diese Schnittstelle.  
  
## <a name="methods-in-vtable-order"></a>Methoden in Vtable-Reihenfolge  
 Die folgende Tabelle zeigt die Methoden der `IDebugBoundBreakpoint2`.  
  
|Methode|Beschreibung|  
|------------|-----------------|  
|[GetPendingBreakpoint](../../../extensibility/debugger/reference/idebugboundbreakpoint2-getpendingbreakpoint.md)|Ruft den ausstehenden Haltepunkt, der aus dem der angegebene gebundene Haltepunkt erstellt wurde.|  
|[GetState](../../../extensibility/debugger/reference/idebugboundbreakpoint2-getstate.md)|Ruft den Zustand dieser gebundene Haltepunkt ab.|  
|[GetHitCount](../../../extensibility/debugger/reference/idebugboundbreakpoint2-gethitcount.md)|Ruft die aktuelle Trefferanzahl für dieser gebundene Haltepunkt ab.|  
|[GetBreakpointResolution](../../../extensibility/debugger/reference/idebugboundbreakpoint2-getbreakpointresolution.md)|Ruft die haltepunktauflösung, die diesem Breakpoint beschreibt.|  
|[Enable](../../../extensibility/debugger/reference/idebugboundbreakpoint2-enable.md)|Aktiviert oder deaktiviert den Haltepunkt.|  
|[SetHitCount](../../../extensibility/debugger/reference/idebugboundbreakpoint2-sethitcount.md)|Legt die Trefferanzahl für diesen gebundenen Haltepunkt fest.|  
|[SetCondition](../../../extensibility/debugger/reference/idebugboundbreakpoint2-setcondition.md)|Legt fest oder ändert die Bedingung, die dieser gebundene Haltepunkt zugeordnet.|  
|[SetPassCount](../../../extensibility/debugger/reference/idebugboundbreakpoint2-setpasscount.md)|Legt fest oder ändern, die Anzahl der Durchläufe dieser gebundene Haltepunkt zugeordnet.|  
|[Löschen](../../../extensibility/debugger/reference/idebugboundbreakpoint2-delete.md)|Löscht den Haltepunkt.|  
  
## <a name="requirements"></a>Anforderungen  
 Header: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Siehe auch  
 [GetBreakpoint](../../../extensibility/debugger/reference/idebugbreakpointunboundevent2-getbreakpoint.md)   
 [Weiter](../../../extensibility/debugger/reference/ienumdebugboundbreakpoints2-next.md)   
 [Bind](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-bind.md)