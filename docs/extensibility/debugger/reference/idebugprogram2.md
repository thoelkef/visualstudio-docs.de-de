---
title: IDebugProgram2 | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProgram2
helpviewer_keywords:
- IDebugProgram2 interface
ms.assetid: 8d73df73-cfff-4b8b-b426-d6051edb1939
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: daad54225170366d98a2df3465c7dba952098c4e
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62870101"
---
# <a name="idebugprogram2"></a>IDebugProgram2
Diese Schnittstelle stellt ein Programm, das in einem Prozess ausgeführt wird.

## <a name="syntax"></a>Syntax

```
IDebugProgram2 : IUnknown
```

## <a name="notes-for-implementers"></a>Hinweise für Implementierer
 Die Debug-Engine (DE) und einen benutzerdefinierten Port Lieferanten implementieren diese Schnittstelle, um ein Programm in einem Prozess darstellen. Sitzungsbasierter Debug-Manager (SDM) auch implementiert diese Schnittstelle, um Informationen zum Bereitstellen [Anfügen](../../../extensibility/debugger/reference/idebugprogram2-attach.md).

## <a name="notes-for-callers"></a>Hinweise für Aufrufer
 Die [IDebugProgramCreateEvent2](../../../extensibility/debugger/reference/idebugprogramcreateevent2.md) Ereignis gibt diese Schnittstelle für ein neues Programm zurück. Diese Schnittstelle wird auch als Parameter für viele Methoden auf mehreren Schnittstellen verwendet.

## <a name="methods-in-vtable-order"></a>Methoden in Vtable-Reihenfolge
 Die folgende Tabelle zeigt die Methoden der `IDebugProgram2`.

|Methode|Beschreibung|
|------------|-----------------|
|[EnumThreads](../../../extensibility/debugger/reference/idebugprogram2-enumthreads.md)|Listet die Threads, die in diesem Programm ausgeführt werden.|
|[GetName](../../../extensibility/debugger/reference/idebugprogram2-getname.md)|Ruft den Namen des Programms.|
|[GetProcess](../../../extensibility/debugger/reference/idebugprogram2-getprocess.md)|Ruft den Prozess, den dieses Programm ausgeführt wird.|
|[Terminate](../../../extensibility/debugger/reference/idebugprogram2-terminate.md)|Dieses Programm wird beendet.|
|[Anfügen](../../../extensibility/debugger/reference/idebugprogram2-attach.md)|Fügt an dieses Programm an.|
|[CanDetach](../../../extensibility/debugger/reference/idebugprogram2-candetach.md)|Bestimmt, ob die Anwendung eine Debug-Engine (DE) trennen kann.|
|[Trennen](../../../extensibility/debugger/reference/idebugprogram2-detach.md)|Trennt den Debugger von diesem Programm.|
|[GetProgramId](../../../extensibility/debugger/reference/idebugprogram2-getprogramid.md)|Ruft einen global eindeutigen Bezeichner für dieses Programm an.|
|[GetDebugProperty](../../../extensibility/debugger/reference/idebugprogram2-getdebugproperty.md)|Ruft die Programmeigenschaften an.|
|[Execute](../../../extensibility/debugger/reference/idebugprogram2-execute.md)|Weiterhin die Ausführung dieses Programms aus einem beendeten Zustand. Alle vorherigen Ausführungsstatus wird gelöscht.|
|[Continue](../../../extensibility/debugger/reference/idebugprogram2-continue.md)|Weiterhin die Ausführung dieses Programms aus einem beendeten Zustand. Alle vorherigen Ausführungsstatus wird beibehalten.|
|[Step](../../../extensibility/debugger/reference/idebugprogram2-step.md)|Führt einen Schritt aus.|
|[CauseBreak](../../../extensibility/debugger/reference/idebugprogram2-causebreak.md)|Fordert an, dass dieses Programm die Ausführung der nächsten beenden Zeitpunkt eins Code Threads ausgeführt wird.|
|[GetEngineInfo](../../../extensibility/debugger/reference/idebugprogram2-getengineinfo.md)|Ruft den Namen und Bezeichner des Debug-Engine (DE) dieses Programm ausführen.|
|[EnumCodeContexts](../../../extensibility/debugger/reference/idebugprogram2-enumcodecontexts.md)|Listet die Codekontexte für eine bestimmte Position in einer Quelldatei an.|
|[GetMemoryBytes](../../../extensibility/debugger/reference/idebugprogram2-getmemorybytes.md)|Ruft die Arbeitsspeicherbytes für dieses Programm ab.|
|[GetDisassemblyStream](../../../extensibility/debugger/reference/idebugprogram2-getdisassemblystream.md)|Ruft den Stream Disassembly für dieses Programm oder einen Teil dieses Programms ab.|
|[EnumModules](../../../extensibility/debugger/reference/idebugprogram2-enummodules.md)|Listet die Module, die dieses Programm wurde geladen und ausgeführt wird.|
|[GetENCUpdate](../../../extensibility/debugger/reference/idebugprogram2-getencupdate.md)|Ruft das Update bearbeiten und Fortfahren "(ENC) für dieses Programm an.<br /><br /> Eine benutzerdefinierten Debug-Engine diese Methode nicht implementiert (es sollte immer zurückgeben `E_NOTIMPL`).|
|[EnumCodePaths](../../../extensibility/debugger/reference/idebugprogram2-enumcodepaths.md)|Listet die Codepfade dieses Programms.|
|[WriteDump](../../../extensibility/debugger/reference/idebugprogram2-writedump.md)|Schreibt einen Dump in eine Datei an.|

## <a name="requirements"></a>Anforderungen
 Header: msdbg.h

 Namespace: Microsoft.VisualStudio.Debugger.Interop

 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="remarks"></a>Hinweise
 Ein Programm ist ein in einer bestimmten Laufzeit-Architektur ausgeführt werden, während ein Prozess aus einem oder mehreren Programmen besteht Thread-Container.

## <a name="see-also"></a>Siehe auch
- [Wichtige Schnittstellen](../../../extensibility/debugger/reference/core-interfaces.md)
- [GetProgram](../../../extensibility/debugger/reference/idebugthread2-getprogram.md)
- [Nächste](../../../extensibility/debugger/reference/ienumdebugprograms2-next.md)
- [Event](../../../extensibility/debugger/reference/idebugportevents2-event.md)
- [Anfügen](../../../extensibility/debugger/reference/idebugengine2-attach.md)
- [DestroyProgram](../../../extensibility/debugger/reference/idebugengine2-destroyprogram.md)
- [Event](../../../extensibility/debugger/reference/idebugeventcallback2-event.md)
- [Attach_V7](../../../extensibility/debugger/reference/idebugprogramnode2-attach-v7.md)