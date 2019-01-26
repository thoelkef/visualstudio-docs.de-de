---
title: IDebugBreakpointRequest2 | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- IDebugBreakpointRequest2
helpviewer_keywords:
- IDebugBreakpointRequest2 interface
ms.assetid: 01ac4013-96f9-4235-b289-f55f9e99558f
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: e61b89fb889a2e274c482e083610b97a19f57f5c
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/25/2019
ms.locfileid: "55001981"
---
# <a name="idebugbreakpointrequest2"></a>IDebugBreakpointRequest2
Diese Schnittstelle stellt die erforderlichen Informationen zum Erstellen und binden jeden Typ von Breakpoint.  
  
## <a name="syntax"></a>Syntax  
  
```  
IDebugBreakpointRequest2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Hinweise für Implementierer  
 Diese Schnittstelle wird von der Sitzungs-Manager (SDM) in der Regel implementiert.  
  
## <a name="notes-for-callers"></a>Hinweise für Aufrufer  
 Die Debug-Engine (DE) empfängt, diese Schnittstelle durch einen Aufruf von [CreatePendingBreakpoint](../../../extensibility/debugger/reference/idebugengine2-creatependingbreakpoint.md) um ein ausstehender Haltepunkt zu erstellen. Ein Aufruf von [GetBreakpointRequest](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-getbreakpointrequest.md) können dieser Schnittstelle aus dem DE abrufen.  
  
## <a name="methods-in-vtable-order"></a>Methoden in Vtable-Reihenfolge  
 Die folgende Tabelle zeigt die Methoden der `IDebugBreakpointRequest2`.  
  
|Methode|Beschreibung|  
|------------|-----------------|  
|[GetLocationType](../../../extensibility/debugger/reference/idebugbreakpointrequest2-getlocationtype.md)|Ruft die Haltepunktpositionstyp dieser Haltepunkt-Anforderung ab.|  
|[GetRequestInfo](../../../extensibility/debugger/reference/idebugbreakpointrequest2-getrequestinfo.md)|Ruft ab, der diese Anforderung Breakpoint beschreibt Informationen zu den Haltepunkt.|  
  
## <a name="remarks"></a>Hinweise  
 Nachdem das Programm im Debugmodus befindlichen geladen wurde, einen Aufruf von [binden](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-bind.md) einen ausstehenden Haltepunkt an der angeforderte Speicherort im Programm gebunden.  
  
## <a name="requirements"></a>Anforderungen  
 Header: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Siehe auch  
 [CreatePendingBreakpoint](../../../extensibility/debugger/reference/idebugengine2-creatependingbreakpoint.md)   
 [GetBreakpointRequest](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-getbreakpointrequest.md)   
 [Bind](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-bind.md)