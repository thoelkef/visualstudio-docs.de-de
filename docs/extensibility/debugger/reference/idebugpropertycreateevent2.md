---
title: IDebugPropertyCreateEvent2 | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- IDebugPropertyCreateEvent2
helpviewer_keywords:
- IDebugPropertyCreateEvent2 interface
ms.assetid: 33b3082b-a42e-488a-a1e4-dadf506f922c
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: b86ac1ba81a7d203177afdde302e8f32599ea698
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/02/2019
ms.locfileid: "53854970"
---
# <a name="idebugpropertycreateevent2"></a>IDebugPropertyCreateEvent2
Diese Schnittstelle wird von der Debug-Engine (DE) für die Sitzung Debug-Manager (SDM) gesendet, wenn es sich um eine Eigenschaft erstellt, die mit einem bestimmten Dokument zugeordnet ist.  
  
## <a name="syntax"></a>Syntax  
  
```  
IDebugPropertyCreateEvent2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Hinweise für Implementierer  
 Die DE implementiert diese Schnittstelle, um zu melden, dass eine Eigenschaft erstellt wurde. Die [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md) Schnittstelle muss auf dasselbe Objekt wie diese Schnittstelle implementiert werden. Wird verwendet, das SDM [QueryInterface](/cpp/atl/queryinterface) für den Zugriff auf die `IDebugEvent2` Schnittstelle. Diese Schnittstelle wird implementiert, wenn die DE Erstellung eine Eigenschaft, mit einem Skript, das geladen oder erstellt wurde und das Skript in der IDE angezeigt muss.  
  
## <a name="notes-for-callers"></a>Hinweise für Aufrufer  
 Die DE erstellt und sendet dieses Ereignisobjekt an den Bericht, den eine Eigenschaft erstellt wurde. Das Ereignis gesendet wird, mithilfe der [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md) Callback-Funktion, die durch die SDM bereitgestellt wird, wenn es um das derzeit debuggte Programm angefügt wird.  
  
## <a name="methods-in-vtable-order"></a>Methoden in Vtable-Reihenfolge  
 Die folgende Tabelle zeigt die Methode die `IDebugPropertyCreateEvent2` Schnittstelle.  
  
|Methode|Beschreibung|  
|------------|-----------------|  
|[GetDebugProperty](../../../extensibility/debugger/reference/idebugpropertycreateevent2-getdebugproperty.md)|Ruft die neue Eigenschaft ab.|  
  
## <a name="remarks"></a>Hinweise  
 Wenn eine Eigenschaft einem bestimmten Dokument oder damit verbundene Skript verfügt, die DE kann senden dieses Ereignis, das SDM zum Aktualisieren der **Skriptdokumente** Fenster mit dem Namen des Dokuments. Ruft das SDM [GetExtendedInfo](../../../extensibility/debugger/reference/idebugproperty2-getextendedinfo.md) mit dem Argument `guidDocument` zum Abrufen einer `VARIANT` , enthält ein [IUnknown](/cpp/atl/iunknown) Zeiger. Ruft das SDM [QueryInterface](/cpp/atl/queryinterface) für diesen Zeiger zum Abrufen der [IDebugDocument2](../../../extensibility/debugger/reference/idebugdocument2.md) -Schnittstelle, die zum Aktualisieren von der **Skriptdokumente** Fenster.  
  
## <a name="requirements"></a>Anforderungen  
 Header: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Siehe auch  
 [Wichtige Schnittstellen](../../../extensibility/debugger/reference/core-interfaces.md)   
 [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md)   
 [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md)   
 [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)