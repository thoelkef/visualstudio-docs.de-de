---
title: IDebugProcess2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProcess2
helpviewer_keywords:
- IDebugProcess2 interface
ms.assetid: 99f6cd06-4076-45ee-b2ae-fa2ad627fd18
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: c72659491ec6718397a4fbb494175eea0896c7f7
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/06/2020
ms.locfileid: "80723796"
---
# <a name="idebugprocess2"></a>IDebugProcess2
Diese Schnittstelle stellt einen Prozess dar, der auf einem Port ausgeführt wird. Wenn der Port der lokale `IDebugProcess2` Port ist, stellt er in der Regel einen physischen Prozess auf dem lokalen Computer dar.

## <a name="syntax"></a>Syntax

```
IDebugProcess2 : IUnknown
```

## <a name="notes-for-implementers"></a>Hinweise für Implementierer
 Diese Schnittstelle wird von einem benutzerdefinierten Portanbieter implementiert, um Programme als Gruppe zu verwalten. Diese Schnittstelle muss vom Portlieferanten implementiert werden.

 Ein Debugmodul implementiert diese Schnittstelle auch, wenn es das Starten eines Programms über [LaunchSuspended](../../../extensibility/debugger/reference/idebugenginelaunch2-launchsuspended.md)unterstützt.

## <a name="notes-for-callers"></a>Hinweise für Anrufer
 Diese Schnittstelle wird in erster Linie vom Sitzungsdebug-Manager (SDM) aufgerufen, um mit einer Gruppe von Programmen zu interagieren, die in diesem Prozess identifiziert wurden.

 Rufen Sie [GetProcess](../../../extensibility/debugger/reference/idebugprogram2-getprocess.md) oder [GetProcess](../../../extensibility/debugger/reference/idebugport2-getprocess.md) auf, um diese Schnittstelle abzurufen. Diese Schnittstelle wird auch `IDebugEngineLaunch2::LaunchSuspended`durch Aufrufen zurückgegeben.

## <a name="methods-in-vtable-order"></a>Methoden in Vtable-Reihenfolge
 Die folgende Tabelle zeigt `IDebugProcess2`die Methoden von .

|Methode|BESCHREIBUNG|
|------------|-----------------|
|[GetInfo](../../../extensibility/debugger/reference/idebugprocess2-getinfo.md)|Ruft eine Beschreibung des Prozesses ab.|
|[EnumPrograms](../../../extensibility/debugger/reference/idebugprocess2-enumprograms.md)|Zählt die Programme auf, die in diesem Prozess enthalten sind.|
|[GetName](../../../extensibility/debugger/reference/idebugprocess2-getname.md)|Ruft den Titel, den Anzeigenamen oder den Dateinamen des Prozesses ab.|
|[GetServer](../../../extensibility/debugger/reference/idebugprocess2-getserver.md)|Ruft die Instanz eines Computerservers ab, auf dem dieser Prozess ausgeführt wird.|
|[Terminate](../../../extensibility/debugger/reference/idebugprocess2-terminate.md)|Beendet den Prozess.|
|[Anfügen](../../../extensibility/debugger/reference/idebugprocess2-attach.md)|Fügt an den Prozess an.|
|[CanDetach](../../../extensibility/debugger/reference/idebugprocess2-candetach.md)|Bestimmt, ob das SDM den Prozess trennen kann.|
|[Trennen](../../../extensibility/debugger/reference/idebugprocess2-detach.md)|Trennt den Debugger vom Prozess.|
|[GetPhysicalProcessId](../../../extensibility/debugger/reference/idebugprocess2-getphysicalprocessid.md)|Ruft den Systemprozessbezeichner ab.|
|[GetProcessId](../../../extensibility/debugger/reference/idebugprocess2-getprocessid.md)|Ruft einen global eindeutigen Bezeichner für diesen Prozess ab.|
|[GetAttachedSessionName](../../../extensibility/debugger/reference/idebugprocess2-getattachedsessionname.md)<br /><br /> [VERALTET]|Ruft den Namen der Sitzung ab, die den Prozess debugg.<br /><br /> [VERALTET. SOLLTE IMMER `E_NOTIMPL`ZURÜCKGEBEN .]|
|[EnumThreads](../../../extensibility/debugger/reference/idebugprocess2-enumthreads.md)|Zählt die Threads auf, die im Prozess ausgeführt werden.|
|[CauseBreak](../../../extensibility/debugger/reference/idebugprocess2-causebreak.md)|Fordert an, dass das nächste Programm, das Code in diesem Prozess ausführt, beendet wird.|
|[GetPort](../../../extensibility/debugger/reference/idebugprocess2-getport.md)|Ruft den Port ab, auf dem dieser Prozess ausgeführt wird.|

## <a name="remarks"></a>Bemerkungen
 Ein `IDebugProcess2` enthält eine oder mehrere [IDebugProgram2-Schnittstellen.](../../../extensibility/debugger/reference/idebugprogram2.md)

## <a name="requirements"></a>Requirements (Anforderungen)
 Kopfzeile: Msdbg.h

 Namespace: Microsoft.VisualStudio.Debugger.Interop

 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Weitere Informationen
- [Wichtige Schnittstellen](../../../extensibility/debugger/reference/core-interfaces.md)
- [Getprocess](../../../extensibility/debugger/reference/idebugport2-getprocess.md)
- [LaunchSuspended](../../../extensibility/debugger/reference/idebugenginelaunch2-launchsuspended.md)
- [Getprocess](../../../extensibility/debugger/reference/idebugprogram2-getprocess.md)
- [Weiter](../../../extensibility/debugger/reference/ienumdebugprocesses2-next.md)
- [Ereignis](../../../extensibility/debugger/reference/idebugportevents2-event.md)
- [IDebugEngineLaunch2](../../../extensibility/debugger/reference/idebugenginelaunch2.md)
- [Ereignis](../../../extensibility/debugger/reference/idebugeventcallback2-event.md)
- [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)
