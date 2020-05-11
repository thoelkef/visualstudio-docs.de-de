---
title: IDebugProgram3 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugProgram3 interface
ms.assetid: 4301ba23-c00c-4ce5-8b1e-3f27da312034
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 9da63d54f64a4ef7592fdbc4d36e2b31220f82df
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/06/2020
ms.locfileid: "80722647"
---
# <a name="idebugprogram3"></a>IDebugProgram3
Diese Schnittstelle stellt ein Programm dar, das in einem Prozess ausgeführt wird und [Execute](../../../extensibility/debugger/reference/idebugprogram2-execute.md) durch Bereitstellen von Threadinformationen erweitert.

## <a name="syntax"></a>Syntax

```
IDebugProgram3 : IDebugProgram3
```

## <a name="notes-for-implementers"></a>Hinweise für Implementierer
 Das Debugmodul (DE) und ein benutzerdefinierter Portlieferant implementieren diese Schnittstelle, um ein Programm in einem Prozess darzustellen. Der Sitzungsdebug-Manager (SDM) implementiert auch diese Schnittstelle, um Informationen an [Attach](../../../extensibility/debugger/reference/idebugprogram2-attach.md)bereitzustellen.

## <a name="notes-for-callers"></a>Hinweise für Anrufer
 Das [IDebugProgramCreateEvent2-Ereignis](../../../extensibility/debugger/reference/idebugprogramcreateevent2.md) gibt diese Schnittstelle für ein neues Programm zurück. Diese Schnittstelle wird auch als Parameter für viele Methoden auf mehreren Schnittstellen verwendet.

## <a name="methods-in-vtable-order"></a>Methoden in Vtable-Reihenfolge
 Die folgende Tabelle zeigt `IDebugProgram3`die Methoden von .

|Methode|BESCHREIBUNG|
|------------|-----------------|
|[ExecuteOnThread](../../../extensibility/debugger/reference/idebugprogram3-executeonthread.md)|Führt das Programm aus. Der Thread wird zurückgegeben, um den Debuggerinformationen darüber zu geben, welchen Thread der Benutzer beim Ausführen anzeigt.|

## <a name="requirements"></a>Requirements (Anforderungen)
 Kopfzeile: msdbg.h

 Namespace: Microsoft.VisualStudio.Debugger.Interop

 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="remarks"></a>Bemerkungen
 Ein Programm ist ein Threadcontainer, der in einer bestimmten Laufzeitarchitektur ausgeführt wird, während ein Prozess aus einem oder mehreren Programmen besteht.

## <a name="see-also"></a>Weitere Informationen
- [Wichtige Schnittstellen](../../../extensibility/debugger/reference/core-interfaces.md)
- [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)
- [GetProgram](../../../extensibility/debugger/reference/idebugthread2-getprogram.md)
- [Weiter](../../../extensibility/debugger/reference/ienumdebugprograms2-next.md)
- [Ereignis](../../../extensibility/debugger/reference/idebugportevents2-event.md)
- [Anfügen](../../../extensibility/debugger/reference/idebugengine2-attach.md)
- [DestroyProgram](../../../extensibility/debugger/reference/idebugengine2-destroyprogram.md)
- [Ereignis](../../../extensibility/debugger/reference/idebugeventcallback2-event.md)
- [Attach_V7](../../../extensibility/debugger/reference/idebugprogramnode2-attach-v7.md)
