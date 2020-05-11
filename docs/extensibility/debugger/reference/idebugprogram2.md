---
title: IDebugProgram2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProgram2
helpviewer_keywords:
- IDebugProgram2 interface
ms.assetid: 8d73df73-cfff-4b8b-b426-d6051edb1939
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 150746197be4945b012717bef08e18ea57168177
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/06/2020
ms.locfileid: "80722718"
---
# <a name="idebugprogram2"></a>IDebugProgram2
Diese Schnittstelle stellt ein Programm dar, das in einem Prozess ausgeführt wird.

## <a name="syntax"></a>Syntax

```
IDebugProgram2 : IUnknown
```

## <a name="notes-for-implementers"></a>Hinweise für Implementierer
 Das Debugmodul (DE) und ein benutzerdefinierter Portlieferant implementieren diese Schnittstelle, um ein Programm in einem Prozess darzustellen. Der Sitzungsdebug-Manager (SDM) implementiert auch diese Schnittstelle, um Informationen an [Attach](../../../extensibility/debugger/reference/idebugprogram2-attach.md)bereitzustellen.

## <a name="notes-for-callers"></a>Hinweise für Anrufer
 Das [IDebugProgramCreateEvent2-Ereignis](../../../extensibility/debugger/reference/idebugprogramcreateevent2.md) gibt diese Schnittstelle für ein neues Programm zurück. Diese Schnittstelle wird auch als Parameter für viele Methoden auf mehreren Schnittstellen verwendet.

## <a name="methods-in-vtable-order"></a>Methoden in Vtable-Reihenfolge
 Die folgende Tabelle zeigt `IDebugProgram2`die Methoden von .

|Methode|BESCHREIBUNG|
|------------|-----------------|
|[EnumThreads](../../../extensibility/debugger/reference/idebugprogram2-enumthreads.md)|Zählt die Threads auf, die in diesem Programm ausgeführt werden.|
|[GetName](../../../extensibility/debugger/reference/idebugprogram2-getname.md)|Ruft den Namen des Programms ab.|
|[Getprocess](../../../extensibility/debugger/reference/idebugprogram2-getprocess.md)|Ruft den Prozess ab, in dem dieses Programm ausgeführt wird.|
|[Terminate](../../../extensibility/debugger/reference/idebugprogram2-terminate.md)|Beendet dieses Programm.|
|[Anfügen](../../../extensibility/debugger/reference/idebugprogram2-attach.md)|Anfügt an dieses Programm.|
|[CanDetach](../../../extensibility/debugger/reference/idebugprogram2-candetach.md)|Legt fest, ob sich ein Debugmodul (DE) vom Programm lösen kann.|
|[Trennen](../../../extensibility/debugger/reference/idebugprogram2-detach.md)|Detachiert den Debugger von diesem Programm.|
|[GetProgramId](../../../extensibility/debugger/reference/idebugprogram2-getprogramid.md)|Ruft einen global eindeutigen Bezeichner für dieses Programm ab.|
|[GetDebugProperty](../../../extensibility/debugger/reference/idebugprogram2-getdebugproperty.md)|Ruft Programmeigenschaften ab.|
|[Ausführen](../../../extensibility/debugger/reference/idebugprogram2-execute.md)|Setzt die Ausführung dieses Programms unter einem angehaltenen Zustand fort. Jeder vorherige Ausführungsstatus wird gelöscht.|
|[Continue](../../../extensibility/debugger/reference/idebugprogram2-continue.md)|Setzt die Ausführung dieses Programms unter einem angehaltenen Zustand fort. Alle vorherigen Ausführungsstatus bleiben erhalten.|
|[Schritt](../../../extensibility/debugger/reference/idebugprogram2-step.md)|Führt einen Schritt aus.|
|[CauseBreak](../../../extensibility/debugger/reference/idebugprogram2-causebreak.md)|Fordert an, dass dieses Programm die Ausführung beendet, wenn einer seiner Threads das nächste Mal Code ausführt.|
|[GetEngineInfo](../../../extensibility/debugger/reference/idebugprogram2-getengineinfo.md)|Ruft den Namen und den Bezeichner des Debugmoduls (DE) ab, das dieses Programm ausführt.|
|[EnumCodeContexts](../../../extensibility/debugger/reference/idebugprogram2-enumcodecontexts.md)|Zählt die Codekontexte für eine bestimmte Position in einer Quelldatei auf.|
|[GetMemoryBytes](../../../extensibility/debugger/reference/idebugprogram2-getmemorybytes.md)|Ruft die Speicherbytes für dieses Programm ab.|
|[GetDisassemblyStream](../../../extensibility/debugger/reference/idebugprogram2-getdisassemblystream.md)|Ruft den Demontagestream für dieses Programm oder einen Teil dieses Programms ab.|
|[EnumModules](../../../extensibility/debugger/reference/idebugprogram2-enummodules.md)|Zählt die Module auf, die dieses Programm geladen hat und ausführt.|
|[GetENCUpdate](../../../extensibility/debugger/reference/idebugprogram2-getencupdate.md)|Ruft das Update Bearbeiten und Fortfahren (ENC) für dieses Programm ab.<br /><br /> Ein benutzerdefiniertes Debugmodul implementiert diese Methode `E_NOTIMPL`nicht (es sollte immer zurückgegeben werden).|
|[EnumCodePaths](../../../extensibility/debugger/reference/idebugprogram2-enumcodepaths.md)|Zählt die Codepfade dieses Programms auf.|
|[WriteDump](../../../extensibility/debugger/reference/idebugprogram2-writedump.md)|Schreibt ein Dump in eine Datei.|

## <a name="requirements"></a>Requirements (Anforderungen)
 Kopfzeile: msdbg.h

 Namespace: Microsoft.VisualStudio.Debugger.Interop

 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="remarks"></a>Bemerkungen
 Ein Programm ist ein Threadcontainer, der in einer bestimmten Laufzeitarchitektur ausgeführt wird, während ein Prozess aus einem oder mehreren Programmen besteht.

## <a name="see-also"></a>Weitere Informationen
- [Wichtige Schnittstellen](../../../extensibility/debugger/reference/core-interfaces.md)
- [GetProgram](../../../extensibility/debugger/reference/idebugthread2-getprogram.md)
- [Weiter](../../../extensibility/debugger/reference/ienumdebugprograms2-next.md)
- [Ereignis](../../../extensibility/debugger/reference/idebugportevents2-event.md)
- [Anfügen](../../../extensibility/debugger/reference/idebugengine2-attach.md)
- [DestroyProgram](../../../extensibility/debugger/reference/idebugengine2-destroyprogram.md)
- [Ereignis](../../../extensibility/debugger/reference/idebugeventcallback2-event.md)
- [Attach_V7](../../../extensibility/debugger/reference/idebugprogramnode2-attach-v7.md)
