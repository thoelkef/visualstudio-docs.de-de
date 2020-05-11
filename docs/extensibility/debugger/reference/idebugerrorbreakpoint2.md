---
title: IDebugErrorBreakpoint2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugErrorBreakpoint2
helpviewer_keywords:
- IDebugErrorBreakpoint2 interface
ms.assetid: 1f2a4b94-3713-46e9-8272-3917187792bd
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 17b20d0f3545b0f7266ad6d0c6423d581233dd3c
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/06/2020
ms.locfileid: "80730081"
---
# <a name="idebugerrorbreakpoint2"></a>IDebugErrorBreakpoint2
Diese Schnittstelle stellt einen Fehler oder Warnhaltepunkt dar, z. B. einen ungültigen Speicherort, einen ungültigen Ausdruck oder die Gründe, aus denen der ausstehende Haltepunkt nicht gebunden wurde (Code noch nicht geladen usw.).

## <a name="syntax"></a>Syntax

```
IDebugErrorBreakpoint2 : IUnknown
```

## <a name="notes-for-implementers"></a>Hinweise für Implementierer
 Ein Debugmodul implementiert diese Schnittstelle als Teil ihrer Unterstützung für Haltepunkte. Diese Schnittstelle wird verwendet, um Probleme beim Binden eines Haltepunkts zu melden.

## <a name="notes-for-callers"></a>Hinweise für Anrufer
 Ein Aufruf von [GetErrorBreakpoint](../../../extensibility/debugger/reference/idebugbreakpointerrorevent2-geterrorbreakpoint.md) ruft diese Schnittstelle ab. Diese Schnittstelle kann auch zurückgegeben werden (als Teil einer Liste, die durch eine [IEnumDebugErrorBreakpoints2-Schnittstelle](../../../extensibility/debugger/reference/ienumdebugerrorbreakpoints2.md) dargestellt wird) durch einen Aufruf von [CanBind](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-canbind.md) oder [EnumErrorBreakpoints](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-enumerrorbreakpoints.md).

## <a name="methods-in-vtable-order"></a>Methoden in Vtable-Reihenfolge
 Die folgende Tabelle zeigt `IDebugErrorBreakpoint2`die Methoden von .

|Methode|BESCHREIBUNG|
|------------|-----------------|
|[GetPendingBreakpoint](../../../extensibility/debugger/reference/idebugerrorbreakpoint2-getpendingbreakpoint.md)|Ruft den ausstehenden Haltepunkt ab, der den Fehler verursacht hat.|
|[GetBreakpointResolution](../../../extensibility/debugger/reference/idebugerrorbreakpoint2-getbreakpointresolution.md)|Ruft die Breakpoint-Fehlerauflösung ab, die den Fehler beschreibt.|

## <a name="requirements"></a>Requirements (Anforderungen)
 Kopfzeile: msdbg.h

 Namespace: Microsoft.VisualStudio.Debugger.Interop

 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Weitere Informationen
- [IDebugBreakpointErrorEvent2](../../../extensibility/debugger/reference/idebugbreakpointerrorevent2.md)
- [GetErrorBreakpoint](../../../extensibility/debugger/reference/idebugbreakpointerrorevent2-geterrorbreakpoint.md)
- [IEnumDebugErrorBreakpoints2](../../../extensibility/debugger/reference/ienumdebugerrorbreakpoints2.md)
- [Weiter](../../../extensibility/debugger/reference/ienumdebugerrorbreakpoints2-next.md)
- [IDebugPendingBreakpoint2](../../../extensibility/debugger/reference/idebugpendingbreakpoint2.md)
- [IDebugErrorBreakpointResolution2](../../../extensibility/debugger/reference/idebugerrorbreakpointresolution2.md)
