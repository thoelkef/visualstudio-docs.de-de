---
title: "IDebugProcess2 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugProcess2"
helpviewer_keywords: 
  - "IDebugProcess2-Schnittstelle"
ms.assetid: 99f6cd06-4076-45ee-b2ae-fa2ad627fd18
caps.latest.revision: 19
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 19
---
# IDebugProcess2
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Diese Schnittstelle stellt einen Prozess, der auf einen Anschluss dar.  Wenn der Anschluss auf dem lokalen Port ist, stellt `IDebugProcess2` normalerweise einen physikalischen Prozess auf dem lokalen Computer dar.  
  
## Syntax  
  
```  
IDebugProcess2 : IUnknown  
```  
  
## Hinweise für Implementierer  
 Diese Schnittstelle wird von einem benutzerdefinierten Anschlusslieferanten implementiert, um Programme als Gruppe zu verwalten.  Diese Schnittstelle muss vom Anschlusslieferanten implementiert werden.  
  
 Ein Debuggen Modul implementiert diese Schnittstelle auch beim Starten eines Programms durch [LaunchSuspended](../../../extensibility/debugger/reference/idebugenginelaunch2-launchsuspended.md)unterstützt.  
  
## Hinweise für Aufrufer  
 Diese Schnittstelle wird hauptsächlich vom Debugbuild Manager der Sitzung \(SDM\) aufgerufen, um mit einer Gruppe von Programmen zu interagieren, die in diesem Prozess identifiziert werden.  
  
 Aufruf [GetProcess](../../../extensibility/debugger/reference/idebugprogram2-getprocess.md) oder [GetProcess](../../../extensibility/debugger/reference/idebugport2-getprocess.md) , wenn dieser Schnittstelle abgerufen.  Diese Schnittstelle wird auch zurückgegeben, indem `IDebugEngineLaunch2::LaunchSuspended`aufruft.  
  
## Methoden in die Vtable\-Reihenfolge  
 In der folgenden Tabelle werden die Methoden von `IDebugProcess2`an.  
  
|Methode|Beschreibung|  
|-------------|------------------|  
|[GetInfo](../../../extensibility/debugger/reference/idebugprocess2-getinfo.md)|Ruft eine Beschreibung des Prozesses ab.|  
|[EnumPrograms](../../../extensibility/debugger/reference/idebugprocess2-enumprograms.md)|Listet Programme aufgeführt, die in diesem Prozess enthalten sind.|  
|[GetName](../../../extensibility/debugger/reference/idebugprocess2-getname.md)|Ruft den Titel des Anzeigenamens, oder der Dateiname des Prozesses ab.|  
|[GetServer](../../../extensibility/debugger/reference/idebugprocess2-getserver.md)|Ruft die Instanz des Computers Servers ab, der von diesem Prozess ausgeführt wird.|  
|[Beenden](../../../extensibility/debugger/reference/idebugprocess2-terminate.md)|Beendet den Prozess.|  
|[Anfügen](../../../extensibility/debugger/reference/idebugprocess2-attach.md)|Fügt dem Prozess an.|  
|[CanDetach](../../../extensibility/debugger/reference/idebugprocess2-candetach.md)|Bestimmt, ob das SDM den Prozess trennen können.|  
|[Trennen](../../../extensibility/debugger/reference/idebugprocess2-detach.md)|Ordnet den Debugger vom Prozess ab.|  
|[GetPhysicalProcessId](../../../extensibility/debugger/reference/idebugprocess2-getphysicalprocessid.md)|Ruft die prozess\-id ab.|  
|[GetProcessId](../../../extensibility/debugger/reference/idebugprocess2-getprocessid.md)|Ruft einen GUID \(Globally Unique Identifier\) für diesen Prozess ab.|  
|[GetAttachedSessionName](../../../extensibility/debugger/reference/idebugprocess2-getattachedsessionname.md)<br /><br /> \[VERALTET\]|Ruft den Namen der Sitzung ab, die den Prozess gedebuggt wird.<br /><br /> \[VERALTET.  ALWAYS IF, GEBEN `E_NOTIMPL`zurück.\]|  
|[EnumThreads](../../../extensibility/debugger/reference/idebugprocess2-enumthreads.md)|Listet die Threads aufgeführt, die in den Prozess ausgeführt werden.|  
|[CauseBreak](../../../extensibility/debugger/reference/idebugprocess2-causebreak.md)|Anforderungen, die der ausgeführte Code des folgenden Prozesses in diesem Programm halt.|  
|[GetPort](../../../extensibility/debugger/reference/idebugprocess2-getport.md)|Ruft den Anschluss ab, die diesen Prozess ausgeführt wird.|  
  
## Hinweise  
 `IDebugProcess2` enthält eine oder mehrere Schnittstellen [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md) .  
  
## Anforderungen  
 Header: Msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## Siehe auch  
 [Core\-Schnittstellen](../../../extensibility/debugger/reference/core-interfaces.md)   
 [GetProcess](../../../extensibility/debugger/reference/idebugport2-getprocess.md)   
 [LaunchSuspended](../../../extensibility/debugger/reference/idebugenginelaunch2-launchsuspended.md)   
 [GetProcess](../../../extensibility/debugger/reference/idebugprogram2-getprocess.md)   
 [Weiter](../../../extensibility/debugger/reference/ienumdebugprocesses2-next.md)   
 [Ereignis](../../../extensibility/debugger/reference/idebugportevents2-event.md)   
 [IDebugEngineLaunch2](../../../extensibility/debugger/reference/idebugenginelaunch2.md)   
 [Ereignis](../../../extensibility/debugger/reference/idebugeventcallback2-event.md)   
 [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)