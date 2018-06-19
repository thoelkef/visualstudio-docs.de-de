---
title: IDebugPropertyDestroyEvent2 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IDebugPropertyDestroyEvent2
helpviewer_keywords:
- IDebugPropertyDestroyEvent2 interface
ms.assetid: 301b7a75-ecfa-46f1-9131-66cf3e4be147
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: f5ae38bf190a88b91e61971b724893f35c652785
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/16/2018
ms.locfileid: "31120662"
---
# <a name="idebugpropertydestroyevent2"></a>IDebugPropertyDestroyEvent2
Diese Schnittstelle wird von Debugging-Modul (DE) gesendet, auf die Sitzung Debug-Manager (SDM), wird eine Eigenschaft, die einem bestimmten Dokument zugeordnet ist, die gelöscht werden.  
  
## <a name="syntax"></a>Syntax  
  
```  
IDebugPropertyDestroyEvent2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Hinweise für Implementierer  
 Die DE implementiert diese Schnittstelle, um zu melden, dass eine Eigenschaft zerstört wurde. Die [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md) -Schnittstelle muss auf das gleiche Objekt wie diese Schnittstelle implementiert werden. Verwendet die SDM [QueryInterface](/cpp/atl/queryinterface) für den Zugriff auf die `IDebugEvent2` Schnittstelle. Diese Schnittstelle wird implementiert, wenn DE zuvor eine Eigenschaft verknüpft sind mit einem Skript erstellt wurde; Zerstören von der Eigenschaft entfernt das zugeordnete Skript aus der IDE.  
  
## <a name="notes-for-callers"></a>Hinweise für Aufrufer  
 DE erstellt und sendet diese Ereignisobjekt zum Bericht, der eine Eigenschaft zerstört wurde. Das Ereignis wird gesendet, mit der [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md) Rückruffunktion, die durch die SDM bereitgestellt wird, wenn es an das derzeit debuggte Programm angefügt ist.  
  
## <a name="methods-in-vtable-order"></a>Methoden in Vtable-Reihenfolge  
 Die folgende Tabelle zeigt die Methode der `IDebugPropertyDestroyEvent2`.  
  
|Methode|Beschreibung|  
|------------|-----------------|  
|[GetDebugProperty](../../../extensibility/debugger/reference/idebugpropertydestroyevent2-getdebugproperty.md)|Ruft die Eigenschaft, die gelöscht werden.|  
  
## <a name="remarks"></a>Hinweise  
 Siehe die Hinweise für [IDebugPropertyCreateEvent2](../../../extensibility/debugger/reference/idebugpropertycreateevent2.md) Weitere Informationen dazu, warum diese Ereignisse verwendet werden.  
  
## <a name="requirements"></a>Anforderungen  
 Header: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Siehe auch  
 [Core-Schnittstellen](../../../extensibility/debugger/reference/core-interfaces.md)   
 [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md)   
 [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md)   
 [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)   
 [IDebugPropertyCreateEvent2](../../../extensibility/debugger/reference/idebugpropertycreateevent2.md)