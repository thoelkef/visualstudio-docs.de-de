---
title: IDebugBoundBreakpoint2 | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- IDebugBoundBreakpoint2
helpviewer_keywords:
- IDebugBoundBreakpoint2 interface
ms.assetid: df33c52e-ded2-48a0-951d-1f36c8fc922e
caps.latest.revision: 
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload:
- vssdk
ms.openlocfilehash: 6ce63ce7f7d6a4f438c0e9f622c34a2231afd6ef
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/22/2017
---
# <a name="idebugboundbreakpoint2"></a>IDebugBoundBreakpoint2
Diese Schnittstelle stellt einen Haltepunkt aus, der an einen Speicherort gebunden ist.  
  
## <a name="syntax"></a>Syntax  
  
```  
IDebugBoundBreakpoint2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Hinweise für Implementierer  
 Die Debugging-Modul (DE) implementiert diese Schnittstelle als Teil der Unterstützung für Haltepunkte.  
  
## <a name="notes-for-callers"></a>Hinweise für Aufrufer  
 Ein Aufruf von [binden](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-bind.md) erstellt diese Schnittstelle. Aufrufe von [GetBreakpoint](../../../extensibility/debugger/reference/idebugbreakpointunboundevent2-getbreakpoint.md) und [Weiter](../../../extensibility/debugger/reference/ienumdebugboundbreakpoints2-next.md) ist auch möglich, diese Schnittstelle.  
  
## <a name="methods-in-vtable-order"></a>Methoden in Vtable-Reihenfolge  
 Die folgende Tabelle zeigt die Methoden der `IDebugBoundBreakpoint2`.  
  
|Methode|Beschreibung|  
|------------|-----------------|  
|[GetPendingBreakpoint](../../../extensibility/debugger/reference/idebugboundbreakpoint2-getpendingbreakpoint.md)|Ruft den ausstehenden Haltepunkts aus dem angegebene gebundene Haltepunkt erstellt wurde.|  
|[GetState](../../../extensibility/debugger/reference/idebugboundbreakpoint2-getstate.md)|Ruft den Zustand dieser gebundenen Haltepunkt ab.|  
|[GetHitCount](../../../extensibility/debugger/reference/idebugboundbreakpoint2-gethitcount.md)|Ruft die aktuelle Trefferanzahl für diese gebundenen Haltepunkt an.|  
|[GetBreakpointResolution](../../../extensibility/debugger/reference/idebugboundbreakpoint2-getbreakpointresolution.md)|Ruft die Breakpoint-Lösung, die diesem Breakpoint beschreibt.|  
|[Aktivieren](../../../extensibility/debugger/reference/idebugboundbreakpoint2-enable.md)|Aktiviert oder deaktiviert den Haltepunkt.|  
|[SetHitCount](../../../extensibility/debugger/reference/idebugboundbreakpoint2-sethitcount.md)|Legt die Trefferanzahl für Haltepunkt gebunden.|  
|[SetCondition](../../../extensibility/debugger/reference/idebugboundbreakpoint2-setcondition.md)|Legt fest oder ändert die Bedingung dieser gebundenen Haltepunkt zugeordnet.|  
|[SetPassCount](../../../extensibility/debugger/reference/idebugboundbreakpoint2-setpasscount.md)|Legt fest oder ändern, die Anzahl der Durchläufe dieser gebundenen Haltepunkt zugeordnet.|  
|[Löschen](../../../extensibility/debugger/reference/idebugboundbreakpoint2-delete.md)|Löscht den Haltepunkt.|  
  
## <a name="requirements"></a>Anforderungen  
 Header: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Siehe auch  
 [GetBreakpoint](../../../extensibility/debugger/reference/idebugbreakpointunboundevent2-getbreakpoint.md)   
 [Weiter](../../../extensibility/debugger/reference/ienumdebugboundbreakpoints2-next.md)   
 [Binden](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-bind.md)