---
title: IDebugEvent2 | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- IDebugEvent2
helpviewer_keywords:
- IDebugEvent2 interface
ms.assetid: de3d714d-96fb-4e12-b66b-a75391472153
caps.latest.revision: 
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload:
- vssdk
ms.openlocfilehash: 0d783cb13ee227e317afe9b49abedb6f53e9fa76
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/22/2017
---
# <a name="idebugevent2"></a>IDebugEvent2
Diese Schnittstelle wird verwendet, kritische Debuginformationen, z. B. an einem Haltepunkt beendet und nicht kritische Informationen, z. B. einer Debugmeldung kommunizieren.  
  
## <a name="syntax"></a>Syntax  
  
```  
IDebugEvent2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Hinweise für Implementierer  
 Die Debugging-Modul (Deutschland) und den benutzerdefinierten Port Lieferanten implementieren diese Schnittstelle auf das gleiche Objekt wie alle anderen Ereignisschnittstellen.  
  
## <a name="notes-for-callers"></a>Hinweise für Aufrufer  
 Mithilfe der Benutzeroberfläche-ID (IID)-Argument übergeben, um [Ereignis](../../../extensibility/debugger/reference/idebugeventcallback2-event.md) oder [Ereignis](../../../extensibility/debugger/reference/idebugportevents2-event.md), ruft der Sitzung Debug-Manager (SDM) [QueryInterface](/cpp/atl/queryinterface) auf die `IDebugEvent2` Schnittstelle zum Abrufen die entsprechende Ereignis-Schnittstelle.  
  
## <a name="methods-in-vtable-order"></a>Methoden in Vtable-Reihenfolge  
 Die folgende Tabelle zeigt die Methoden der `IDebugEvent2`.  
  
|Methode|Beschreibung|  
|------------|-----------------|  
|[GetAttributes](../../../extensibility/debugger/reference/idebugevent2-getattributes.md)|Ruft die Attribute für dieses Ereignis Debuggen.|  
  
## <a name="remarks"></a>Hinweise  
 Schnittstellen für das spezifische Ereignis, wie z. B. [IDebugBreakpointEvent2](../../../extensibility/debugger/reference/idebugbreakpointevent2.md), leiten Sie nicht von der Schnittstelle IDebugEvent2 sind jedoch stattdessen als implementiert eine separate Schnittstelle für das gleiche Objekt als `IDebugEvent2`.  
  
## <a name="requirements"></a>Anforderungen  
 Header: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Siehe auch  
 [Core-Schnittstellen](../../../extensibility/debugger/reference/core-interfaces.md)   
 [Ereignis](../../../extensibility/debugger/reference/idebugportevents2-event.md)   
 [Event](../../../extensibility/debugger/reference/idebugeventcallback2-event.md)