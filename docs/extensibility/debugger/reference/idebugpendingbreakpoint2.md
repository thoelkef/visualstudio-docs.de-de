---
title: IDebugPendingBreakpoint2 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IDebugPendingBreakpoint2
helpviewer_keywords:
- IDebugPendingBreakpoint2 interface
ms.assetid: d416b095-917e-475e-b796-ec0a03ffb8da
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 3e5e84180747a3e6a3b9e5a34e7694f4cd07867c
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/16/2018
ms.locfileid: "31121556"
---
# <a name="idebugpendingbreakpoint2"></a>IDebugPendingBreakpoint2
Diese Schnittstelle stellt einen Haltepunkt aus, der zum Binden an einen Speicherort bereit ist.  
  
## <a name="syntax"></a>Syntax  
  
```  
IDebugPendingBreakpoint2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Hinweise für Implementierer  
 Die Debugging-Modul (DE) implementiert diese Schnittstelle als Teil der Unterstützung für Haltepunkte.  
  
## <a name="notes-for-callers"></a>Hinweise für Aufrufer  
 Ein Aufruf von [CreatePendingBreakpoint](../../../extensibility/debugger/reference/idebugengine2-creatependingbreakpoint.md) erstellt einen ausstehenden Haltepunkt aus einer [IDebugBreakpointRequest2](../../../extensibility/debugger/reference/idebugbreakpointrequest2.md) Schnittstelle. Ein Aufruf von [binden](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-bind.md) erstellt eine `IDebugBreakpoint2` Schnittstelle, die einen gebundenen Haltepunkt in der Anwendung darstellt.  
  
## <a name="methods-in-vtable-order"></a>Methoden in Vtable-Reihenfolge  
 Die folgende Tabelle zeigt die Methoden der `IDebugPendingBreakpoint2`.  
  
|Methode|Beschreibung|  
|------------|-----------------|  
|[CanBind](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-canbind.md)|Bestimmt, ob diese ausstehenden Haltepunkts an einem Speicherort Code binden kann.|  
|[Binden](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-bind.md)|Diese ausstehenden Haltepunkts an eine oder mehrere Codepositionen gebunden.|  
|[GetState](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-getstate.md)|Ruft den Zustand dieses ausstehender Haltepunkt an.|  
|[GetBreakpointRequest](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-getbreakpointrequest.md)|Ruft das Haltepunkt-Anforderung, die mit diesem ausstehenden Haltepunkt erstellt wurde.|  
|[Virtualisieren](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-virtualize.md)|Schaltet das virtualisierte dieses ausstehender Haltepunkt.|  
|[Aktivieren](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-enable.md)|Schaltet den aktivierten Zustand dieses ausstehender Haltepunkt an.|  
|[SetCondition](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-setcondition.md)|Legt fest oder ändert die Bedingung, die zugeordneten ausstehenden Haltepunkts.|  
|[SetPassCount](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-setpasscount.md)|Legt fest oder ändert die Anzahl der Durchläufe ausstehender Haltepunkt zugeordnet.|  
|[EnumBoundBreakpoints](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-enumboundbreakpoints.md)|Listet alle Breakpoints, die von diesem ausstehender Haltepunkt gebunden.|  
|[EnumErrorBreakpoints](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-enumerrorbreakpoints.md)|Listet alle Fehler Breakpoints, die von diesem ausstehender Haltepunkt geführt haben.|  
|[Löschen](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-delete.md)|Löscht diese ausstehenden Haltepunkts und alle Breakpoints, die von ihm gebunden.|  
  
## <a name="remarks"></a>Hinweise  
 `IDebugPendingBreakpoint2` kann der betrachtet werden, als Anbieter von allen erforderlichen Informationen erforderlich, um einen Haltepunkt an Code zu binden, die auf einem oder mehreren Programmen angewendet werden können.  
  
 Ein ausstehender Haltepunkt kann möglicherweise mehr als einen gebundenen Haltepunkt erzeugen. Beispielsweise konnte ein Haltepunkt in einer C++-Formatvorlage einen gebundenen Haltepunkt für jede eindeutige Instanz dieser Vorlage erstellen.  
  
## <a name="requirements"></a>Anforderungen  
 Header: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Siehe auch  
 [CreatePendingBreakpoint](../../../extensibility/debugger/reference/idebugengine2-creatependingbreakpoint.md)   
 [GetPendingBreakpoint](../../../extensibility/debugger/reference/idebugbreakpointboundevent2-getpendingbreakpoint.md)   
 [GetPendingBreakpoint](../../../extensibility/debugger/reference/idebugboundbreakpoint2-getpendingbreakpoint.md)   
 [GetPendingBreakpoint](../../../extensibility/debugger/reference/idebugerrorbreakpoint2-getpendingbreakpoint.md)