---
title: IDebugErrorBreakpointResolution2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugErrorBreakpointResolution2
helpviewer_keywords:
- IDebugErrorBreakpointResolution2
ms.assetid: b1234216-0ac8-461d-b2a7-54f60f8f3262
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: d922259034d4e99c43fc06cfef8228b013fb180f
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/06/2020
ms.locfileid: "80730021"
---
# <a name="idebugerrorbreakpointresolution2"></a>IDebugErrorBreakpointResolution2
Diese Schnittstelle stellt die Lösung eines Haltepunktfehlers dar.

## <a name="syntax"></a>Syntax

```
IDebugErrorBreakpointResolution2 : IUnknown
```

## <a name="notes-for-implementers"></a>Hinweise für Implementierer
 Ein Debugmodul implementiert diese Schnittstelle als Teil ihrer Unterstützung für Haltepunkte. Diese Schnittstelle wird verwendet, um zu melden, wo ein Haltepunkt nicht gebunden werden konnte.

## <a name="notes-for-callers"></a>Hinweise für Anrufer
 Ein Aufruf von [GetBreakpointResolution](../../../extensibility/debugger/reference/idebugerrorbreakpoint2-getbreakpointresolution.md) gibt diese Schnittstelle zurück, um Informationen darüber bereitzustellen, wo der Haltepunkt nicht gebunden werden konnte. Die [GetErrorBreakpoint-Methode](../../../extensibility/debugger/reference/idebugbreakpointerrorevent2-geterrorbreakpoint.md) ruft die [IDebugErrorBreakpoint2-Schnittstelle](../../../extensibility/debugger/reference/idebugerrorbreakpoint2.md) ab.

## <a name="methods-in-vtable-order"></a>Methoden in Vtable-Reihenfolge
 Die folgende Tabelle zeigt `IDebugErrorBreakpointResolution2`die Methoden von .

|Methode|BESCHREIBUNG|
|------------|-----------------|
|[GetBreakpointType](../../../extensibility/debugger/reference/idebugerrorbreakpointresolution2-getbreakpointtype.md)|Ruft den Haltepunkttyp ab.|
|[GetResolutionInfo](../../../extensibility/debugger/reference/idebugerrorbreakpointresolution2-getresolutioninfo.md)|Ruft die Informationen zur Haltepunktauflösung ab.|

## <a name="requirements"></a>Requirements (Anforderungen)
 Kopfzeile: msdbg.h

 Namespace: Microsoft.VisualStudio.Debugger.Interop

 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Weitere Informationen
- [IDebugErrorBreakpoint2](../../../extensibility/debugger/reference/idebugerrorbreakpoint2.md)
- [GetBreakpointResolution](../../../extensibility/debugger/reference/idebugerrorbreakpoint2-getbreakpointresolution.md)
- [GetErrorBreakpoint](../../../extensibility/debugger/reference/idebugbreakpointerrorevent2-geterrorbreakpoint.md)
