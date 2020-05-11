---
title: IDebugBoundBreakpoint2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugBoundBreakpoint2
helpviewer_keywords:
- IDebugBoundBreakpoint2 interface
ms.assetid: df33c52e-ded2-48a0-951d-1f36c8fc922e
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: f4d22b10085baefeb3a0286c1b4edcb5876c0dac
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/06/2020
ms.locfileid: "80735424"
---
# <a name="idebugboundbreakpoint2"></a>IDebugBoundBreakpoint2
Diese Schnittstelle stellt einen Haltepunkt dar, der an einen Codespeicherort gebunden ist.

## <a name="syntax"></a>Syntax

```
IDebugBoundBreakpoint2 : IUnknown
```

## <a name="notes-for-implementers"></a>Hinweise für Implementierer
 Das Debug-Modul (DE) implementiert diese Schnittstelle als Teil ihrer Unterstützung für Haltepunkte.

## <a name="notes-for-callers"></a>Hinweise für Anrufer
 Ein Aufruf von [Bind](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-bind.md) erstellt diese Schnittstelle. Aufrufe von [GetBreakpoint](../../../extensibility/debugger/reference/idebugbreakpointunboundevent2-getbreakpoint.md) und [Next](../../../extensibility/debugger/reference/ienumdebugboundbreakpoints2-next.md) können diese Schnittstelle ebenfalls abrufen.

## <a name="methods-in-vtable-order"></a>Methoden in Vtable-Reihenfolge
 Die folgende Tabelle zeigt `IDebugBoundBreakpoint2`die Methoden von .

|Methode|BESCHREIBUNG|
|------------|-----------------|
|[GetPendingBreakpoint](../../../extensibility/debugger/reference/idebugboundbreakpoint2-getpendingbreakpoint.md)|Ruft den ausstehenden Haltepunkt ab, von dem aus der angegebene gebundene Haltepunkt erstellt wurde.|
|[GetState](../../../extensibility/debugger/reference/idebugboundbreakpoint2-getstate.md)|Ruft den Status dieses gebundenen Haltepunkts ab.|
|[GetHitCount](../../../extensibility/debugger/reference/idebugboundbreakpoint2-gethitcount.md)|Ruft die aktuelle Trefferanzahl für diesen gebundenen Haltepunkt ab.|
|[GetBreakpointResolution](../../../extensibility/debugger/reference/idebugboundbreakpoint2-getbreakpointresolution.md)|Ruft die Haltepunktauflösung ab, die diesen Haltepunkt beschreibt.|
|[Aktivieren](../../../extensibility/debugger/reference/idebugboundbreakpoint2-enable.md)|Aktiviert oder deaktiviert den Haltepunkt.|
|[SetHitCount](../../../extensibility/debugger/reference/idebugboundbreakpoint2-sethitcount.md)|Legt die Trefferanzahl für diesen gebundenen Haltepunkt fest.|
|[SetCondition](../../../extensibility/debugger/reference/idebugboundbreakpoint2-setcondition.md)|Legt die Bedingung fest, die diesem gebundenen Haltepunkt zugeordnet ist, oder ändert sie.|
|[SetPassCount](../../../extensibility/debugger/reference/idebugboundbreakpoint2-setpasscount.md)|Legt die Passanzahl fest, die diesem gebundenen Haltepunkt zugeordnet ist, oder ändert sie.|
|[Richtlinie](../../../extensibility/debugger/reference/idebugboundbreakpoint2-delete.md)|Löscht den Haltepunkt.|

## <a name="requirements"></a>Requirements (Anforderungen)
 Kopfzeile: msdbg.h

 Namespace: Microsoft.VisualStudio.Debugger.Interop

 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Weitere Informationen
- [GetBreakpoint](../../../extensibility/debugger/reference/idebugbreakpointunboundevent2-getbreakpoint.md)
- [Weiter](../../../extensibility/debugger/reference/ienumdebugboundbreakpoints2-next.md)
- [Binden](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-bind.md)
