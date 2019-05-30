---
title: IDebugEngine2 | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugEngine2
helpviewer_keywords:
- IDebugEngine2 interface
ms.assetid: 1f0e9ac0-6dfb-461a-976c-888d82144cdb
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: ce60ffb1143dd763ea14390b0b55e105f74d1b53
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/29/2019
ms.locfileid: "66352554"
---
# <a name="idebugengine2"></a>IDebugEngine2
Diese Schnittstelle stellt eine Debug-Engine (DE). Es wird verwendet, um verschiedene Aspekte von einer Debugsitzung zu verwalten, erstellen Sie Haltepunkte festlegen und Löschen von Ausnahmen.

## <a name="syntax"></a>Syntax

```
IDebugEngine2 : IUnknown
```

## <a name="notes-for-implementers"></a>Hinweise für Implementierer
 Diese Schnittstelle wird von einer benutzerdefinierten DE zum Verwalten von Programmen Debuggen implementiert. Diese Schnittstelle muss von der DE implementiert werden.

## <a name="notes-for-callers"></a>Hinweise für Aufrufer
 Diese Schnittstelle wird von der Sitzungs-Manager (SDM) verwalten die Debugsitzung, einschließlich der Verwaltung von Ausnahmen, erstellen Haltepunkte und reagieren auf synchrone Ereignisse, die von der DE gesendet aufgerufen.

## <a name="methods-in-vtable-order"></a>Methoden in Vtable-Reihenfolge
 Die folgende Tabelle zeigt die Methoden der `IDebugEngine2`.

|Methode|Beschreibung|
|------------|-----------------|
|[EnumPrograms](../../../extensibility/debugger/reference/idebugengine2-enumprograms.md)|Erstellt einen Enumerator für alle Programme, die von einer bereitgestellten Kompatibilitätsrichtlinie gedebuggt wird.|
|[Anfügen](../../../extensibility/debugger/reference/idebugengine2-attach.md)|Fügt eine bereitgestellten Kompatibilitätsrichtlinie an ein Programm an.|
|[CreatePendingBreakpoint](../../../extensibility/debugger/reference/idebugengine2-creatependingbreakpoint.md)|Erstellt einen ausstehenden Haltepunkt in der DE.|
|[SetException](../../../extensibility/debugger/reference/idebugengine2-setexception.md)|Gibt an, wie die DE für eine bestimmte Ausnahme behandeln soll.|
|[RemoveSetException](../../../extensibility/debugger/reference/idebugengine2-removesetexception.md)|Entfernt die angegebene Ausnahme an, damit sie nicht mehr von der Debug-Engine verarbeitet wird.|
|[RemoveAllSetExceptions](../../../extensibility/debugger/reference/idebugengine2-removeallsetexceptions.md)|Entfernt die Liste der Ausnahmen, die die IDE für eine bestimmte Laufzeit-Architektur oder Sprache festgelegt hat.|
|[GetEngineID](../../../extensibility/debugger/reference/idebugengine2-getengineid.md)|Ruft die GUID des DE ab.|
|[DestroyProgram](../../../extensibility/debugger/reference/idebugengine2-destroyprogram.md)|Informiert eine bereitgestellten Kompatibilitätsrichtlinie, die das angegebene Programm ungewöhnlich beendet wurde und die DE sollten bereinigen Sie alle Verweise auf das Programm und senden Sie ein Programm, zerstören Ereignis.|
|[ContinueFromSynchronousEvent](../../../extensibility/debugger/reference/idebugengine2-continuefromsynchronousevent.md)|Wird aufgerufen, durch die SDM, um anzugeben, dass ein synchroner Debug-Ereignis, durch die DE zuvor gesendet werden, um die SDM empfangen und verarbeitet wurde.|
|[SetLocale](../../../extensibility/debugger/reference/idebugengine2-setlocale.md)|Legt das Gebietsschema des DE fest.|
|[SetRegistryRoot](../../../extensibility/debugger/reference/idebugengine2-setregistryroot.md)|Legt den Registrierungsstamm, die derzeit in Verwendung durch die DE fest.|
|[SetMetric](../../../extensibility/debugger/reference/idebugengine2-setmetric.md)|Legt eine Metrik fest.|
|[CauseBreak](../../../extensibility/debugger/reference/idebugengine2-causebreak.md)|Fordert an, dass alle von diesem DE gedebuggten Programme Ausführung das nächste Mal zu, die einer ihrer Threads versucht beenden zu starten.|

## <a name="requirements"></a>Anforderungen
 Header: Msdbg.h

 Namespace: Microsoft.VisualStudio.Debugger.Interop

 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Siehe auch
- [Event](../../../extensibility/debugger/reference/idebugeventcallback2-event.md)
- [GetEngine](../../../extensibility/debugger/reference/idebugenginecreateevent2-getengine.md)