---
title: IDebugProcess2 | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: IDebugProcess2
helpviewer_keywords: IDebugProcess2 interface
ms.assetid: 99f6cd06-4076-45ee-b2ae-fa2ad627fd18
caps.latest.revision: "19"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: d8b349bee09f068a5777ecc212223c36951236ee
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/31/2017
---
# <a name="idebugprocess2"></a>IDebugProcess2
Diese Schnittstelle stellt einen Prozess auf einem Port ausgeführt wird. Wenn der Anschluss am lokalen Port, klicken Sie dann ist `IDebugProcess2` entspricht normalerweise einem physischen Prozess auf dem lokalen Computer.  
  
## <a name="syntax"></a>Syntax  
  
```  
IDebugProcess2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Hinweise für Implementierer  
 Diese Schnittstelle wird durch einen benutzerdefinierten Port Lieferanten Verwalten von Programmen als Gruppe implementiert. Diese Schnittstelle muss von den Lieferanten Port implementiert werden.  
  
 Ein Debugmodul implementiert diese Schnittstelle auch, sofern dies unterstützt, starten ein Programm über [LaunchSuspended](../../../extensibility/debugger/reference/idebugenginelaunch2-launchsuspended.md).  
  
## <a name="notes-for-callers"></a>Hinweise für Aufrufer  
 Diese Schnittstelle wird in erster Linie durch die Sitzung Debug-Manager (SDM) aufgerufen, um die Interaktion mit einer Gruppe von Programmen, die in diesem Prozess identifiziert.  
  
 Rufen Sie [GetProcess](../../../extensibility/debugger/reference/idebugprogram2-getprocess.md) oder [GetProcess](../../../extensibility/debugger/reference/idebugport2-getprocess.md) zum Abrufen von dieser Schnittstelle. Diese Schnittstelle wird auch zurückgegeben, durch den Aufruf `IDebugEngineLaunch2::LaunchSuspended`.  
  
## <a name="methods-in-vtable-order"></a>Methoden in Vtable-Reihenfolge  
 Die folgende Tabelle zeigt die Methoden der `IDebugProcess2`.  
  
|Methode|Beschreibung|  
|------------|-----------------|  
|[GetInfo](../../../extensibility/debugger/reference/idebugprocess2-getinfo.md)|Ruft eine Beschreibung des Prozesses ab.|  
|[EnumPrograms](../../../extensibility/debugger/reference/idebugprocess2-enumprograms.md)|Listet die Programme, die in diesem Prozess enthalten sind.|  
|[GetName](../../../extensibility/debugger/reference/idebugprocess2-getname.md)|Ruft den Titel, den Anzeigenamen oder den Dateinamen des Prozesses an.|  
|[GetServer](../../../extensibility/debugger/reference/idebugprocess2-getserver.md)|Ruft die Instanz von einem Computer, Server, auf den diesen Prozess ausgeführt wird.|  
|[Beenden](../../../extensibility/debugger/reference/idebugprocess2-terminate.md)|Beendet den Prozess.|  
|[Anfügen](../../../extensibility/debugger/reference/idebugprocess2-attach.md)|Fügt an den Prozess.|  
|[CanDetach](../../../extensibility/debugger/reference/idebugprocess2-candetach.md)|Bestimmt, ob die SDM Prozess trennen kann.|  
|[Trennen](../../../extensibility/debugger/reference/idebugprocess2-detach.md)|Wird den Debugger vom Prozess getrennt.|  
|[GetPhysicalProcessId](../../../extensibility/debugger/reference/idebugprocess2-getphysicalprocessid.md)|Ruft die System-Prozess-ID ab.|  
|[GetProcessId](../../../extensibility/debugger/reference/idebugprocess2-getprocessid.md)|Ruft einen global eindeutigen Bezeichner für diesen Prozess ab.|  
|[GetAttachedSessionName](../../../extensibility/debugger/reference/idebugprocess2-getattachedsessionname.md)<br /><br /> [VERALTET]|Ruft den Namen der Sitzung, die den Prozess zu Debuggen ist.<br /><br /> [VERALTET. SOLLTE IMMER RETURN `E_NOTIMPL`.]|  
|[EnumThreads](../../../extensibility/debugger/reference/idebugprocess2-enumthreads.md)|Listet die Threads im Prozess ausgeführt.|  
|[CauseBreak](../../../extensibility/debugger/reference/idebugprocess2-causebreak.md)|Fordert an, die das nächste Programm, das Ausführen von Code in diesem Prozess beenden.|  
|[GetPort](../../../extensibility/debugger/reference/idebugprocess2-getport.md)|Ruft den Port, den dieser Prozess ausgeführt wird.|  
  
## <a name="remarks"></a>Hinweise  
 Ein `IDebugProcess2` enthält ein oder mehrere [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md) Schnittstellen.  
  
## <a name="requirements"></a>Anforderungen  
 Header: Msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Siehe auch  
 [Core-Schnittstellen](../../../extensibility/debugger/reference/core-interfaces.md)   
 [GetProcess](../../../extensibility/debugger/reference/idebugport2-getprocess.md)   
 [LaunchSuspended](../../../extensibility/debugger/reference/idebugenginelaunch2-launchsuspended.md)   
 [GetProcess](../../../extensibility/debugger/reference/idebugprogram2-getprocess.md)   
 [Weiter](../../../extensibility/debugger/reference/ienumdebugprocesses2-next.md)   
 [Ereignis](../../../extensibility/debugger/reference/idebugportevents2-event.md)   
 [IDebugEngineLaunch2](../../../extensibility/debugger/reference/idebugenginelaunch2.md)   
 [Ereignis](../../../extensibility/debugger/reference/idebugeventcallback2-event.md)   
 [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)