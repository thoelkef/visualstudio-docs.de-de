---
title: IDebugProcess2 | Microsoft-Dokumentation
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- IDebugProcess2
helpviewer_keywords:
- IDebugProcess2 interface
ms.assetid: 99f6cd06-4076-45ee-b2ae-fa2ad627fd18
caps.latest.revision: 20
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: e5d1fcdb6df958a62ed23b3bc7e812e1f4a7e15f
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/12/2018
ms.locfileid: "49218776"
---
# <a name="idebugprocess2"></a>IDebugProcess2
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Diese Schnittstelle stellt einen Prozess auf einem Port ausgeführt wird. Wenn der Port der lokale Port, dann ist `IDebugProcess2` in der Regel einen physischen Prozess auf dem lokalen Computer darstellt.  
  
## <a name="syntax"></a>Syntax  
  
```  
IDebugProcess2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Hinweise für Implementierer  
 Diese Schnittstelle wird von einem benutzerdefinierten Port Lieferanten zum Verwalten von Programmen als Gruppe implementiert. Diese Schnittstelle muss von den Anschlusslieferanten implementiert werden.  
  
 Ein Debugmodul implementiert diese Schnittstelle auch, falls dies unterstützt das Starten eines Programms durch [LaunchSuspended](../../../extensibility/debugger/reference/idebugenginelaunch2-launchsuspended.md).  
  
## <a name="notes-for-callers"></a>Hinweise für Aufrufer  
 Diese Schnittstelle ist in erster Linie durch die sitzungsbasierter Debug-Manager (SDM) aufgerufen, um die Interaktion mit einer Gruppe von Programmen, die in diesem Prozess identifiziert.  
  
 Rufen Sie [GetProcess](../../../extensibility/debugger/reference/idebugprogram2-getprocess.md) oder [GetProcess](../../../extensibility/debugger/reference/idebugport2-getprocess.md) auf dieser Schnittstelle abzurufen. Diese Schnittstelle wird auch zurückgegeben, durch den Aufruf `IDebugEngineLaunch2::LaunchSuspended`.  
  
## <a name="methods-in-vtable-order"></a>Methoden in Vtable-Reihenfolge  
 Die folgende Tabelle zeigt die Methoden der `IDebugProcess2`.  
  
|Methode|Beschreibung|  
|------------|-----------------|  
|[GetInfo](../../../extensibility/debugger/reference/idebugprocess2-getinfo.md)|Ruft eine Beschreibung des Prozesses.|  
|[EnumPrograms](../../../extensibility/debugger/reference/idebugprocess2-enumprograms.md)|Listet die Programme, die in diesem Prozess enthalten sind.|  
|[GetName](../../../extensibility/debugger/reference/idebugprocess2-getname.md)|Ruft ab, der Titel, der Anzeigename oder der Dateiname des Prozesses.|  
|[GetServer](../../../extensibility/debugger/reference/idebugprocess2-getserver.md)|Ruft die Instanz von einem Computer, Server, die, den diesen Prozess ausgeführt wird.|  
|[Terminate](../../../extensibility/debugger/reference/idebugprocess2-terminate.md)|Beendet den Prozess.|  
|[Anfügen](../../../extensibility/debugger/reference/idebugprocess2-attach.md)|Fügt an den Prozess.|  
|[CanDetach](../../../extensibility/debugger/reference/idebugprocess2-candetach.md)|Bestimmt, ob das SDM den Prozess trennen kann.|  
|[Trennen](../../../extensibility/debugger/reference/idebugprocess2-detach.md)|Trennt den Debugger aus dem Prozess.|  
|[GetPhysicalProcessId](../../../extensibility/debugger/reference/idebugprocess2-getphysicalprocessid.md)|Ruft die System-Prozess-ID ab.|  
|[GetProcessId](../../../extensibility/debugger/reference/idebugprocess2-getprocessid.md)|Ruft einen global eindeutigen Bezeichner für diesen Prozess ab.|  
|[GetAttachedSessionName](../../../extensibility/debugger/reference/idebugprocess2-getattachedsessionname.md)<br /><br /> [VERALTET]|Ruft den Namen der Sitzung, die Debuggen des Prozesses.<br /><br /> [ALS VERALTET MARKIERT. SOLLTEN SIE IMMER RÜCKGABE `E_NOTIMPL`.]|  
|[EnumThreads](../../../extensibility/debugger/reference/idebugprocess2-enumthreads.md)|Listet die Threads im Prozess ausgeführt wird.|  
|[CauseBreak](../../../extensibility/debugger/reference/idebugprocess2-causebreak.md)|Fordert an, die das nächste Programm, das Ausführen von Code in diesem Prozess beenden.|  
|[GetPort](../../../extensibility/debugger/reference/idebugprocess2-getport.md)|Ruft ab, der Port, den diesem Prozess ausgeführt wird.|  
  
## <a name="remarks"></a>Hinweise  
 Ein `IDebugProcess2` enthält ein oder mehrere [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md) Schnittstellen.  
  
## <a name="requirements"></a>Anforderungen  
 Header: Msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Siehe auch  
 [Wichtige Schnittstellen](../../../extensibility/debugger/reference/core-interfaces.md)   
 [GetProcess](../../../extensibility/debugger/reference/idebugport2-getprocess.md)   
 [LaunchSuspended](../../../extensibility/debugger/reference/idebugenginelaunch2-launchsuspended.md)   
 [GetProcess](../../../extensibility/debugger/reference/idebugprogram2-getprocess.md)   
 [Weiter](../../../extensibility/debugger/reference/ienumdebugprocesses2-next.md)   
 [Ereignis](../../../extensibility/debugger/reference/idebugportevents2-event.md)   
 [IDebugEngineLaunch2](../../../extensibility/debugger/reference/idebugenginelaunch2.md)   
 [Ereignis](../../../extensibility/debugger/reference/idebugeventcallback2-event.md)   
 [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)

