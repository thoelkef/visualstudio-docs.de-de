---
title: IDebugProgram3 | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugProgram3 interface
ms.assetid: 4301ba23-c00c-4ce5-8b1e-3f27da312034
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 0cfc29f300bc9f28f857424a7a91b4b6bfd3bf82
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/29/2019
ms.locfileid: "66331532"
---
# <a name="idebugprogram3"></a>IDebugProgram3
Diese Schnittstelle stellt dar, ein Programm, das in einem Prozess ausgeführt wird, und erweitert [Execute](../../../extensibility/debugger/reference/idebugprogram2-execute.md) durch die Bereitstellung von Threadinformationen.

## <a name="syntax"></a>Syntax

```
IDebugProgram3 : IDebugProgram3
```

## <a name="notes-for-implementers"></a>Hinweise für Implementierer
 Die Debug-Engine (DE) und einen benutzerdefinierten Port Lieferanten implementieren diese Schnittstelle, um ein Programm in einem Prozess darstellen. Sitzungsbasierter Debug-Manager (SDM) auch implementiert diese Schnittstelle, um Informationen zum Bereitstellen [Anfügen](../../../extensibility/debugger/reference/idebugprogram2-attach.md).

## <a name="notes-for-callers"></a>Hinweise für Aufrufer
 Die [IDebugProgramCreateEvent2](../../../extensibility/debugger/reference/idebugprogramcreateevent2.md) Ereignis gibt diese Schnittstelle für ein neues Programm zurück. Diese Schnittstelle wird auch als Parameter für viele Methoden auf mehreren Schnittstellen verwendet.

## <a name="methods-in-vtable-order"></a>Methoden in Vtable-Reihenfolge
 Die folgende Tabelle zeigt die Methoden der `IDebugProgram3`.

|Methode|Beschreibung|
|------------|-----------------|
|[ExecuteOnThread](../../../extensibility/debugger/reference/idebugprogram3-executeonthread.md)|Führt das Programm. Der Debuggerinformationen geben, in welchem, die Thread dem Benutzer, beim Ausführen angezeigt wird, wird der Thread zurückgegeben.|

## <a name="requirements"></a>Anforderungen
 Header: msdbg.h

 Namespace: Microsoft.VisualStudio.Debugger.Interop

 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="remarks"></a>Hinweise
 Ein Programm ist ein in einer bestimmten Laufzeit-Architektur ausgeführt werden, während ein Prozess aus einem oder mehreren Programmen besteht Thread-Container.

## <a name="see-also"></a>Siehe auch
- [Wichtige Schnittstellen](../../../extensibility/debugger/reference/core-interfaces.md)
- [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)
- [GetProgram](../../../extensibility/debugger/reference/idebugthread2-getprogram.md)
- [Nächste](../../../extensibility/debugger/reference/ienumdebugprograms2-next.md)
- [Event](../../../extensibility/debugger/reference/idebugportevents2-event.md)
- [Anfügen](../../../extensibility/debugger/reference/idebugengine2-attach.md)
- [DestroyProgram](../../../extensibility/debugger/reference/idebugengine2-destroyprogram.md)
- [Event](../../../extensibility/debugger/reference/idebugeventcallback2-event.md)
- [Attach_V7](../../../extensibility/debugger/reference/idebugprogramnode2-attach-v7.md)