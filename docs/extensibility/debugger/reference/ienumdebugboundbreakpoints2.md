---
title: IEnumDebugBoundBreakpoints2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IEnumDebugBoundBreakpoints2
helpviewer_keywords:
- IEnumDebugBoundBreakpoints2
ms.assetid: ea03e7e1-28d6-40b7-8097-bbb61d3b7caa
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 421d46efbef189fd6ffc86812d2bfdd28f5da5ff
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/06/2020
ms.locfileid: "80717441"
---
# <a name="ienumdebugboundbreakpoints2"></a>IEnumDebugBoundBreakpoints2
Diese Schnittstelle zählt die gebundenen Haltepunkte auf, die einem ausstehenden Haltepunkt- oder Haltepunktgebundenen Ereignis zugeordnet sind.

## <a name="syntax"></a>Syntax

```
IEnumDebugBoundBreakpoints2 : IUnknown
```

## <a name="notes-for-implementers"></a>Hinweise für Implementierer
 Das Debug-Modul (DE) implementiert diese Schnittstelle als Teil ihrer Unterstützung für Haltepunkte. Diese Schnittstelle muss implementiert werden, wenn Haltepunkte unterstützt werden.

## <a name="notes-for-callers"></a>Hinweise für Anrufer
 Visual Studio-Aufrufe:

- [EnumBreakpoints,](../../../extensibility/debugger/reference/idebugbreakpointevent2-enumbreakpoints.md) um diese Schnittstelle zu erhalten, die eine Liste aller ausgelösten Haltepunkte darstellt.

- [EnumBoundBreakpoints,](../../../extensibility/debugger/reference/idebugbreakpointboundevent2-enumboundbreakpoints.md) um diese Schnittstelle abzuerhalten, die eine Liste aller gebundenen Haltepunkte darstellt.

- [EnumBoundBreakpoints,](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-enumboundbreakpoints.md) um diese Schnittstelle abzuerhalten, die eine Liste aller Haltepunkte darstellt, die an diesen ausstehenden Haltepunkt gebunden sind.

## <a name="methods-in-vtable-order"></a>Methoden in Vtable-Reihenfolge
 Die folgende Tabelle zeigt `IEnumDebugBoundBreakpoints2`die Methoden von .

|Methode|BESCHREIBUNG|
|------------|-----------------|
|[Weiter](../../../extensibility/debugger/reference/ienumdebugboundbreakpoints2-next.md)|Ruft eine angegebene Anzahl gebundener Haltepunkte in einer Enumerationssequenz ab.|
|[Überspringen](../../../extensibility/debugger/reference/ienumdebugboundbreakpoints2-skip.md)|Überspringt eine angegebene Anzahl gebundener Haltepunkte in einer Enumerationssequenz.|
|[Zurücksetzen](../../../extensibility/debugger/reference/ienumdebugboundbreakpoints2-reset.md)|Setzt eine Enumerationsfolge auf den Anfang zurück.|
|[Klon](../../../extensibility/debugger/reference/ienumdebugboundbreakpoints2-clone.md)|Erstellt einen Enumerator, der denselben Enumerationsstatus wie der aktuelle Enumerator enthält.|
|[GetCount](../../../extensibility/debugger/reference/ienumdebugboundbreakpoints2-getcount.md)|Ruft die Anzahl der gebundenen Haltepunkte in einem Enumerator ab.|

## <a name="remarks"></a>Bemerkungen
 Visual Studio verwendet die gebundenen Haltepunkte, die von dieser Schnittstelle dargestellt werden, um die Anzeige von Haltepunkten in der IDE zu aktualisieren.

## <a name="requirements"></a>Requirements (Anforderungen)
 Kopfzeile: msdbg.h

 Namespace: Microsoft.VisualStudio.Debugger.Interop

 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Weitere Informationen
- [Wichtige Schnittstellen](../../../extensibility/debugger/reference/core-interfaces.md)
- [EnumBoundBreakpoints](../../../extensibility/debugger/reference/idebugbreakpointboundevent2-enumboundbreakpoints.md)
- [EnumBoundBreakpoints](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-enumboundbreakpoints.md)
- [EnumBoundBreakpoints](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-enumboundbreakpoints.md)
