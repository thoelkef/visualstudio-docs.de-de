---
title: IDebugPortEx2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugPortEx2
helpviewer_keywords:
- IDebugPortEx2 interface
ms.assetid: 144724d0-38ee-4c9b-87ca-8a504371182b
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 5789681b0da70f46dadac1e29d0d6bb9dc905d1a
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/06/2020
ms.locfileid: "80724998"
---
# <a name="idebugportex2"></a>IDebugPortEx2
Mit dieser Schnittstelle kann der Session-Debug-Manager (SDM) die Programme und Prozesse steuern, die auf einem Port ausgeführt werden.

## <a name="syntax"></a>Syntax

```
IDebugPortEx2 : IUnknown
```

## <a name="notes-for-implementers"></a>Hinweise für Implementierer
 Ein benutzerdefinierter Portlieferant implementiert diese Schnittstelle für dasselbe Objekt, das [IDebugPort2](../../../extensibility/debugger/reference/idebugport2.md)implementiert.

## <a name="notes-for-callers"></a>Hinweise für Anrufer
 Das SDM ruft [QueryInterface](/cpp/atl/queryinterface) auf der `IDebugPort2` Schnittstelle auf, um diese Schnittstelle zu erhalten.

## <a name="methods-in-vtable-order"></a>Methoden in Vtable-Reihenfolge
 Die folgende Tabelle zeigt `IDebugPortEx2`die Methoden von .

|Methode|BESCHREIBUNG|
|------------|-----------------|
|[LaunchSuspended](../../../extensibility/debugger/reference/idebugportex2-launchsuspended.md)|Startet eine ausführbare Datei.|
|[ResumeProcess](../../../extensibility/debugger/reference/idebugportex2-resumeprocess.md)|Setzt die Ausführung eines Prozesses fort.|
|[CanTerminateProcess](../../../extensibility/debugger/reference/idebugportex2-canterminateprocess.md)|Bestimmt, ob ein Prozess beendet werden kann.|
|[TerminateProcess](../../../extensibility/debugger/reference/idebugportex2-terminateprocess.md)|Beendet einen Prozess.|
|[GetPortProcessId](../../../extensibility/debugger/reference/idebugportex2-getportprocessid.md)|Ruft die Prozess-ID des Ports selbst ab.|
|[GetProgram](../../../extensibility/debugger/reference/idebugportex2-getprogram.md)|Ruft ein Programm ab, das einem Programmknoten zugeordnet ist.|

## <a name="remarks"></a>Bemerkungen
 Diese Schnittstelle ist normalerweise privat zwischen dem SDM und dem benutzerdefinierten Portanbieter.

 Falls gewünscht, kann ein Debugmodul (DE) nach dieser Schnittstelle auf der [IDebugPort2-Schnittstelle](../../../extensibility/debugger/reference/idebugport2.md) suchen, die an [LaunchSuspended](../../../extensibility/debugger/reference/idebugenginelaunch2-launchsuspended.md) übergeben wird, und [LaunchSuspended](../../../extensibility/debugger/reference/idebugportex2-launchsuspended.md) verwenden, um das Programm zu starten. Dies ist jedoch keine Anforderung, und eine DE kann alles tun, was sie tun muss, um das Anforderungsprogramm zu starten.

## <a name="requirements"></a>Requirements (Anforderungen)
 Kopfzeile: portpriv.h

 Namespace: Microsoft.VisualStudio.Debugger.Interop

 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Weitere Informationen
- [Wichtige Schnittstellen](../../../extensibility/debugger/reference/core-interfaces.md)
- [IDebugPort2](../../../extensibility/debugger/reference/idebugport2.md)
