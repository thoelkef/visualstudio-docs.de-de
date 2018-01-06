---
title: IDebugBreakpointUnboundEvent2 | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: IDebugBreakpointUnboundEvent2
helpviewer_keywords: IDebugBreakpointUnboundEvent2
ms.assetid: 6b1e1863-0c64-4d85-8ab9-aface522fdea
caps.latest.revision: "11"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 148840222521e85c5cf71991eb5acc3823b74331
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/22/2017
---
# <a name="idebugbreakpointunboundevent2"></a>IDebugBreakpointUnboundEvent2
Diese Schnittstelle weist dem Sitzungs-Manager (SDM), dass ein gebundener Haltepunkt ein Programm geladen wurde aufgehoben wurde.  
  
## <a name="syntax"></a>Syntax  
  
```  
IDebugBreakpointUnboundEvent2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Hinweise für Implementierer  
 Die Debugging-Modul (DE) implementiert diese Schnittstelle als Teil der Unterstützung für Haltepunkte. Die [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md) -Schnittstelle muss implementiert werden, auf das gleiche Objekt wie diese Schnittstelle (verwendet die SDM [QueryInterface](/cpp/atl/queryinterface) für den Zugriff auf die `IDebugEvent2` Schnittstelle).  
  
## <a name="notes-for-callers"></a>Hinweise für Aufrufer  
 Die DE erstellt und sendet diese Ereignisobjekt ein gebundener Haltepunkt aufgehoben wurde. Das Ereignis wird gesendet, mit der [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md) Rückruffunktion, die durch die SDM angegeben werden, wenn es an das derzeit debuggte Programm angefügt.  
  
## <a name="methods-in-vtable-order"></a>Methoden in Vtable-Reihenfolge  
 Die folgende Tabelle zeigt die Methoden der `IDebugBreakpointUnboundEvent2`.  
  
|Methode|Beschreibung|  
|------------|-----------------|  
|[GetBreakpoint](../../../extensibility/debugger/reference/idebugbreakpointunboundevent2-getbreakpoint.md)|Ruft ab, die nicht gebundenen Haltepunkt.|  
|[GetReason](../../../extensibility/debugger/reference/idebugbreakpointunboundevent2-getreason.md)|Ruft den Grund für den der Haltepunkt aufgehoben wurde.|  
  
## <a name="remarks"></a>Hinweise  
 Wenn ein Debugging-Modul-DLL oder Klasse entladen wurde, muss alle Breakpoints, die an den Code in diesem Modul gebunden wurden zu debuggenden Programms wurde aufgehoben. Ein `IDebugBreakpointUnboundEvent2` wird für jeden ungebundenen Breakpoint gesendet.  
  
## <a name="requirements"></a>Anforderungen  
 Header: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Siehe auch  
 [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md)   
 [IDebugBoundBreakpoint2](../../../extensibility/debugger/reference/idebugboundbreakpoint2.md)   
 [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md)