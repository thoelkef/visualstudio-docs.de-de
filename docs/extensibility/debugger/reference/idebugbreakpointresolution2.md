---
title: IDebugBreakpointResolution2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugBreakpointResolution2
helpviewer_keywords:
- IDebugBreakpointRequest2 interface
ms.assetid: 451d5bce-b9c1-48ff-beaa-2b4c3e1ceea0
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: bb5e4f9e32017cfb493aae00a24f9f8184605d1d
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/06/2020
ms.locfileid: "80734744"
---
# <a name="idebugbreakpointresolution2"></a>IDebugBreakpointResolution2
Diese Schnittstelle stellt die Informationen dar, die einen gebundenen Haltepunkt beschreiben.

## <a name="syntax"></a>Syntax

```
IDebugBreakpointResolution2 : IUnknown
```

## <a name="notes-for-implementers"></a>Hinweise für Implementierer
 Das Debug-Modul (DE) implementiert diese Schnittstelle als Teil ihrer Unterstützung für Haltepunkte. Diese Schnittstelle enthält eine Beschreibung eines gebundenen Haltepunkts, den der Sitzungsdebug-Manager verwendet, wenn ein Benutzer die Eigenschaften eines Haltepunkts anzeigt.

## <a name="notes-for-callers"></a>Hinweise für Anrufer
 Ein Aufruf von [GetBreakpointResolution](../../../extensibility/debugger/reference/idebugboundbreakpoint2-getbreakpointresolution.md) gibt diese Schnittstelle zurück.

## <a name="methods-in-vtable-order"></a>Methoden in Vtable-Reihenfolge
 Die folgende Tabelle zeigt `IDebugBreakpointResolution2`die Methoden von .

|Methode|BESCHREIBUNG|
|------------|-----------------|
|[GetBreakpointType](../../../extensibility/debugger/reference/idebugbreakpointresolution2-getbreakpointtype.md)|Ruft den Typ des Haltepunkts ab, der durch diese Auflösung dargestellt wird.|
|[GetResolutionInfo](../../../extensibility/debugger/reference/idebugbreakpointresolution2-getresolutioninfo.md)|Ruft die Informationen zur Haltepunktauflösung ab, die diesen Haltepunkt beschreiben.|

## <a name="requirements"></a>Requirements (Anforderungen)
 Kopfzeile: msdbg.h

 Namespace: Microsoft.VisualStudio.Debugger.Interop

 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Weitere Informationen
- [GetBreakpointResolution](../../../extensibility/debugger/reference/idebugboundbreakpoint2-getbreakpointresolution.md)
