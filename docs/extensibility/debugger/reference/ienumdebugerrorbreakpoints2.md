---
title: IEnumDebugErrorBreakpoints2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IEnumDebugErrorBreakpoints2
helpviewer_keywords:
- IEnumDebugErrorBreakpoints2
ms.assetid: ffdad73d-969a-45ef-9ad1-7f5d3b814018
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: ea841a095964b71e301e966bfd0a10c8f7c0c65d
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/06/2020
ms.locfileid: "80716884"
---
# <a name="ienumdebugerrorbreakpoints2"></a>IEnumDebugErrorBreakpoints2
Diese Schnittstelle zählt die Fehlerhaltepunkte auf, die einem ausstehenden Haltepunkt zugeordnet sind.

## <a name="syntax"></a>Syntax

```
IEnumDebugErrorBreakpoints2 : IUnknown
```

## <a name="notes-for-implementers"></a>Hinweise für Implementierer
 Das Debug-Modul (DE) implementiert diese Schnittstelle als Teil ihrer Unterstützung für Haltepunkte.

## <a name="notes-for-callers"></a>Hinweise für Anrufer
 Visual Studio ruft [CanBind](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-canbind.md) auf, um diese Schnittstelle abzuerhalten, die eine Liste von Haltepunkten darstellt, die nicht gebunden werden können, oder [EnumErrorBreakpoints,](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-enumerrorbreakpoints.md) um diese Schnittstelle abzusondern, die eine Liste von Haltepunkten darstellt, die nicht gebunden waren.

## <a name="methods-in-vtable-order"></a>Methoden in Vtable-Reihenfolge
 Die folgende Tabelle zeigt `IEnumDebugErrorBreakpoints2`die Methoden von .

|Methode|BESCHREIBUNG|
|------------|-----------------|
|[Weiter](../../../extensibility/debugger/reference/ienumdebugerrorbreakpoints2-next.md)|Ruft eine angegebene Anzahl von Fehlerhaltepunkten in einer Enumerationssequenz ab.|
|[Überspringen](../../../extensibility/debugger/reference/ienumdebugerrorbreakpoints2-skip.md)|Überspringt eine angegebene Anzahl von Fehlerhaltepunkten in einer Enumerationssequenz.|
|[Zurücksetzen](../../../extensibility/debugger/reference/ienumdebugerrorbreakpoints2-reset.md)|Setzt eine Enumerationsfolge auf den Anfang zurück.|
|[Klon](../../../extensibility/debugger/reference/ienumdebugerrorbreakpoints2-clone.md)|Erstellt einen Enumerator, der denselben Enumerationsstatus wie der aktuelle Enumerator enthält.|
|[GetCount](../../../extensibility/debugger/reference/ienumdebugerrorbreakpoints2-getcount.md)|Ruft die Anzahl der Fehlerhaltepunkte in einem Enumerator ab.|

## <a name="remarks"></a>Bemerkungen
 Diese Schnittstelle enthält eine Liste von [IDebugErrorBreakpoint2-Schnittstellen,](../../../extensibility/debugger/reference/idebugerrorbreakpoint2.md) von denen jede einen Haltepunkt beschreibt, der nicht gebunden werden konnte und warum er nicht gebunden werden konnte. Visual Studio `IEnumDebugErrorBreakpoint2` verwendet die Schnittstelle, um die in der IDE angezeigten Haltepunkte zu aktualisieren.

## <a name="requirements"></a>Requirements (Anforderungen)
 Kopfzeile: msdbg.h

 Namespace: Microsoft.VisualStudio.Debugger.Interop

 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Weitere Informationen
- [Wichtige Schnittstellen](../../../extensibility/debugger/reference/core-interfaces.md)
- [CanBind](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-canbind.md)
- [EnumErrorBreakpoints](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-enumerrorbreakpoints.md)
- [IDebugErrorBreakpoint2](../../../extensibility/debugger/reference/idebugerrorbreakpoint2.md)
