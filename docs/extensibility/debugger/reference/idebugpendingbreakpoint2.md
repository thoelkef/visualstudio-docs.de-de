---
title: IDebugPendingBreakpoint2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugPendingBreakpoint2
helpviewer_keywords:
- IDebugPendingBreakpoint2 interface
ms.assetid: d416b095-917e-475e-b796-ec0a03ffb8da
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 4e6f2c1df37e953a5d8c66bad9d0a3574a463fad
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/06/2020
ms.locfileid: "80725651"
---
# <a name="idebugpendingbreakpoint2"></a>IDebugPendingBreakpoint2
Diese Schnittstelle stellt einen Haltepunkt dar, der an einen Codespeicherort gebunden werden kann.

## <a name="syntax"></a>Syntax

```
IDebugPendingBreakpoint2 : IUnknown
```

## <a name="notes-for-implementers"></a>Hinweise für Implementierer
 Das Debug-Modul (DE) implementiert diese Schnittstelle als Teil ihrer Unterstützung für Haltepunkte.

## <a name="notes-for-callers"></a>Hinweise für Anrufer
 Ein Aufruf von [CreatePendingBreakpoint](../../../extensibility/debugger/reference/idebugengine2-creatependingbreakpoint.md) erstellt einen ausstehenden Haltepunkt aus einer [IDebugBreakpointRequest2-Schnittstelle.](../../../extensibility/debugger/reference/idebugbreakpointrequest2.md) Ein Aufruf [Bind](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-bind.md) von `IDebugBreakpoint2` Bind erstellt eine Schnittstelle, die einen gebundenen Haltepunkt im Programm darstellt.

## <a name="methods-in-vtable-order"></a>Methoden in Vtable-Reihenfolge
 Die folgende Tabelle zeigt `IDebugPendingBreakpoint2`die Methoden von .

|Methode|BESCHREIBUNG|
|------------|-----------------|
|[CanBind](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-canbind.md)|Bestimmt, ob dieser ausstehende Haltepunkt an einen Codespeicherort gebunden werden kann.|
|[Binden](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-bind.md)|Bindet diesen ausstehenden Haltepunkt an einen oder mehrere Codespeicherorte.|
|[GetState](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-getstate.md)|Ruft den Status dieses ausstehenden Haltepunkts ab.|
|[GetBreakpointRequest](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-getbreakpointrequest.md)|Ruft die Haltepunktanforderung ab, die zum Erstellen dieses ausstehenden Haltepunkts verwendet wurde.|
|[Virtualisieren](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-virtualize.md)|Schaltet den virtualisierten Zustand dieses ausstehenden Haltepunkts um.|
|[Aktivieren](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-enable.md)|Schaltet den aktivierten Status dieses ausstehenden Haltepunkts um.|
|[SetCondition](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-setcondition.md)|Legt die Bedingung fest, die diesem ausstehenden Haltepunkt zugeordnet ist, oder ändert sie.|
|[SetPassCount](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-setpasscount.md)|Legt die Passanzahl fest, die diesem ausstehenden Haltepunkt zugeordnet ist, oder ändert sie.|
|[EnumBoundBreakpoints](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-enumboundbreakpoints.md)|Zählt alle Haltepunkte auf, die von diesem ausstehenden Haltepunkt gebunden sind.|
|[EnumErrorBreakpoints](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-enumerrorbreakpoints.md)|Zählt alle Fehlerhaltepunkte auf, die aus diesem ausstehenden Haltepunkt resultierten.|
|[Richtlinie](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-delete.md)|Löscht diesen ausstehenden Haltepunkt und alle haltepunkte, die davon gebunden sind.|

## <a name="remarks"></a>Bemerkungen
 `IDebugPendingBreakpoint2`kann als Anbieter aller erforderlichen Informationen betrachtet werden, um einen Haltepunkt an Code zu binden, der auf ein oder mehrere Programme angewendet werden kann.

 Ein ausstehender Haltepunkt kann möglicherweise mehr als einen gebundenen Haltepunkt erzeugen. Beispielsweise kann ein Haltepunkt in einer Vorlage im C++-Stil einen gebundenen Haltepunkt für jede eindeutige Instanz dieser Vorlage erzeugen.

## <a name="requirements"></a>Requirements (Anforderungen)
 Kopfzeile: msdbg.h

 Namespace: Microsoft.VisualStudio.Debugger.Interop

 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Weitere Informationen
- [CreatePendingBreakpoint](../../../extensibility/debugger/reference/idebugengine2-creatependingbreakpoint.md)
- [GetPendingBreakpoint](../../../extensibility/debugger/reference/idebugbreakpointboundevent2-getpendingbreakpoint.md)
- [GetPendingBreakpoint](../../../extensibility/debugger/reference/idebugboundbreakpoint2-getpendingbreakpoint.md)
- [GetPendingBreakpoint](../../../extensibility/debugger/reference/idebugerrorbreakpoint2-getpendingbreakpoint.md)
