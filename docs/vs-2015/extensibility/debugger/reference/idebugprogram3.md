---
title: IDebugProgram3 | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
helpviewer_keywords:
- IDebugProgram3 interface
ms.assetid: 4301ba23-c00c-4ce5-8b1e-3f27da312034
caps.latest.revision: 6
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: ae6de25108cf93314db17a2ac8de9ce8b1dcaed2
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "68148606"
---
# <a name="idebugprogram3"></a>IDebugProgram3
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Diese Schnittstelle stellt ein Programm dar, das in einem Prozess ausgeführt wird und die [Ausführung](../../../extensibility/debugger/reference/idebugprogram2-execute.md) durch Bereitstellen von Thread Informationen erweitert.  
  
## <a name="syntax"></a>Syntax  
  
```  
IDebugProgram3 : IDebugProgram3  
```  
  
## <a name="notes-for-implementers"></a>Hinweise für Implementierer  
 Die Debug-Engine (de) und ein benutzerdefinierter Port Lieferant implementieren diese Schnittstelle, um ein Programm in einem Prozess darzustellen. Der Sitzungs-Debug-Manager (SDM) implementiert auch diese Schnittstelle, um die [anzufügenden](../../../extensibility/debugger/reference/idebugprogram2-attach.md)Informationen bereitzustellen.  
  
## <a name="notes-for-callers"></a>Hinweise für Aufrufer  
 Das [IDebugProgramCreateEvent2](../../../extensibility/debugger/reference/idebugprogramcreateevent2.md) -Ereignis gibt diese Schnittstelle für ein neues Programm zurück. Diese Schnittstelle wird auch als Parameter für viele Methoden in mehreren Schnittstellen verwendet.  
  
## <a name="methods-in-vtable-order"></a>Methoden in Vtable-Reihenfolge  
 In der folgenden Tabelle sind die Methoden von aufgeführt `IDebugProgram3` .  
  
|Methode|Beschreibung|  
|------------|-----------------|  
|[ExecuteOnThread](../../../extensibility/debugger/reference/idebugprogram3-executeonthread.md)|Führt das Programm aus. Der Thread wird zurückgegeben, um den Debuggerinformationen zu dem Thread zu übergeben, den der Benutzer beim Ausführen anzeigen kann.|  
  
## <a name="requirements"></a>Anforderungen  
 Header: msdbg. h  
  
 Namespace: Microsoft. VisualStudio. Debugger. Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="remarks"></a>Bemerkungen  
 Ein Programm ist ein Thread Container, der in einer bestimmten Lauf Zeit Architektur ausgeführt wird, während ein Prozess aus mindestens einem Programm besteht.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Kern Schnittstellen](../../../extensibility/debugger/reference/core-interfaces.md)   
 [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)   
 [Getprogram](../../../extensibility/debugger/reference/idebugthread2-getprogram.md)   
 [Weiter](../../../extensibility/debugger/reference/ienumdebugprograms2-next.md)   
 [Veranstalter](../../../extensibility/debugger/reference/idebugportevents2-event.md)   
 [An](../../../extensibility/debugger/reference/idebugengine2-attach.md)   
 [Destroyprogram](../../../extensibility/debugger/reference/idebugengine2-destroyprogram.md)   
 [Veranstalter](../../../extensibility/debugger/reference/idebugeventcallback2-event.md)   
 [Attach_V7](../../../extensibility/debugger/reference/idebugprogramnode2-attach-v7.md)
