---
title: IDebugEngine2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugEngine2
helpviewer_keywords:
- IDebugEngine2 interface
ms.assetid: 1f0e9ac0-6dfb-461a-976c-888d82144cdb
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 5e00751db052adeefee828829ec89309a3adba4b
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/06/2020
ms.locfileid: "80730864"
---
# <a name="idebugengine2"></a>IDebugEngine2
Diese Schnittstelle stellt ein Debugmodul (DE) dar. Es wird verwendet, um verschiedene Aspekte einer Debugsitzung zu verwalten, vom Erstellen von Haltepunkten bis hin zum Festlegen und Löschen von Ausnahmen.

## <a name="syntax"></a>Syntax

```
IDebugEngine2 : IUnknown
```

## <a name="notes-for-implementers"></a>Hinweise für Implementierer
 Diese Schnittstelle wird von einer benutzerdefinierten DE implementiert, um das Debuggen von Programmen zu verwalten. Diese Schnittstelle muss von der DE implementiert werden.

## <a name="notes-for-callers"></a>Hinweise für Anrufer
 Diese Schnittstelle wird vom Sitzungsdebug-Manager (SDM) aufgerufen, um die Debugsitzung zu verwalten, einschließlich der Verwaltung von Ausnahmen, dem Erstellen von Haltepunkten und dem Reagieren auf synchrone Ereignisse, die von der DE gesendet werden.

## <a name="methods-in-vtable-order"></a>Methoden in Vtable-Reihenfolge
 Die folgende Tabelle zeigt `IDebugEngine2`die Methoden von .

|Methode|BESCHREIBUNG|
|------------|-----------------|
|[EnumPrograms](../../../extensibility/debugger/reference/idebugengine2-enumprograms.md)|Erstellt einen Enumerator für alle Programme, die von einem DE gedebuggt werden.|
|[Anfügen](../../../extensibility/debugger/reference/idebugengine2-attach.md)|Fügt eine DE an ein Programm an.|
|[CreatePendingBreakpoint](../../../extensibility/debugger/reference/idebugengine2-creatependingbreakpoint.md)|Erstellt einen ausstehenden Haltepunkt in der DE.|
|[SetException](../../../extensibility/debugger/reference/idebugengine2-setexception.md)|Gibt an, wie die DE eine bestimmte Ausnahme behandeln soll.|
|[RemoveSetException](../../../extensibility/debugger/reference/idebugengine2-removesetexception.md)|Entfernt die angegebene Ausnahme, sodass sie nicht mehr vom Debugmodul behandelt wird.|
|[RemoveAllSetExceptions](../../../extensibility/debugger/reference/idebugengine2-removeallsetexceptions.md)|Entfernt die Liste der Ausnahmen, die die IDE für eine bestimmte Laufzeitarchitektur oder -sprache festgelegt hat.|
|[GetEngineID](../../../extensibility/debugger/reference/idebugengine2-getengineid.md)|Ruft die GUID der DE ab.|
|[DestroyProgram](../../../extensibility/debugger/reference/idebugengine2-destroyprogram.md)|Informiert eine DE, dass das angegebene Programm atypisch beendet wurde und dass die DE alle Verweise auf das Programm bereinigen und ein Programm-Zerstörungsereignis senden sollte.|
|[ContinueFromSynchronousEvent](../../../extensibility/debugger/reference/idebugengine2-continuefromsynchronousevent.md)|Wird vom SDM aufgerufen, um anzugeben, dass ein synchrones Debugereignis, das zuvor von der DE an das SDM gesendet wurde, empfangen und verarbeitet wurde.|
|[SetLocale](../../../extensibility/debugger/reference/idebugengine2-setlocale.md)|Legt das Gebietsschema der DE fest.|
|[SetRegistryRoot](../../../extensibility/debugger/reference/idebugengine2-setregistryroot.md)|Legt den Registrierungsstamm fest, der derzeit von der DE verwendet wird.|
|[SetMetric](../../../extensibility/debugger/reference/idebugengine2-setmetric.md)|Legt eine Metrik fest.|
|[CauseBreak](../../../extensibility/debugger/reference/idebugengine2-causebreak.md)|Fordert an, dass alle Programme, die von dieser DE gedebuggiert werden, die Ausführung beenden, wenn einer ihrer Threads das nächste Mal versucht, ausgeführt zu werden.|

## <a name="requirements"></a>Requirements (Anforderungen)
 Kopfzeile: Msdbg.h

 Namespace: Microsoft.VisualStudio.Debugger.Interop

 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Weitere Informationen
- [Ereignis](../../../extensibility/debugger/reference/idebugeventcallback2-event.md)
- [GetEngine](../../../extensibility/debugger/reference/idebugenginecreateevent2-getengine.md)
