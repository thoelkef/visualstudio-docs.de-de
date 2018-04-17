---
title: IDebugProgramCreateEvent2 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IDebugProgramCreateEvent2
helpviewer_keywords:
- IDebugProgramCreateEvent2 interface
ms.assetid: b19a7934-6179-4a68-9075-bd7dcd640b05
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 591a1e02be4ac96db75c0d43761d83910b89c019
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/16/2018
---
# <a name="idebugprogramcreateevent2"></a>IDebugProgramCreateEvent2
Diese Schnittstelle wird durch die Debugging-Modul (DE) auf dem Sitzungs-Manager (SDM) gesendet, wenn ein Programm angefügt ist.  
  
## <a name="syntax"></a>Syntax  
  
```  
IDebugProgramCreateEvent2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Hinweise für Implementierer  
 Die DE oder den benutzerdefinierten Port Lieferanten implementiert diese Schnittstelle, um zu melden, dass ein Programm, in der Regel zum Zeitpunkt erstellt wurde, an die Anwendung angefügt ist. Die [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md) -Schnittstelle muss auf das gleiche Objekt wie diese Schnittstelle implementiert werden. Die SDM verwendet die `QueryInterface` Methode, um die `IDebugEvent2` Schnittstelle.  
  
## <a name="notes-for-callers"></a>Hinweise für Aufrufer  
 Die DE oder den benutzerdefinierten Port Lieferanten erstellt und sendet diese Ereignisobjekt, um die Erstellung eines Programms zu melden. Die DE sendet dieses Ereignis mithilfe der [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md) Rückruffunktion, die durch die SDM bereitgestellt wird, wenn diese an die derzeit debuggte Programm angefügt. Der benutzerdefinierte Port Lieferant sendet diese Ereignis mit der [IDebugPortEvents2](../../../extensibility/debugger/reference/idebugportevents2.md) Schnittstelle.  
  
## <a name="remarks"></a>Hinweise  
 Die DE oder benutzerdefinierter Port Lieferanten veröffentlicht eine neue [IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md) Schnittstelle durch den Aufruf [PublishProgramNode](../../../extensibility/debugger/reference/idebugprogrampublisher2-publishprogramnode.md).  
  
## <a name="requirements"></a>Anforderungen  
 Header: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Siehe auch  
 [Core-Schnittstellen](../../../extensibility/debugger/reference/core-interfaces.md)   
 [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md)   
 [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md)   
 [IDebugPortEvents2](../../../extensibility/debugger/reference/idebugportevents2.md)   
 [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)