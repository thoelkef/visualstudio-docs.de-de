---
title: IDebugBreakpointRequest2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugBreakpointRequest2
helpviewer_keywords:
- IDebugBreakpointRequest2 interface
ms.assetid: 01ac4013-96f9-4235-b289-f55f9e99558f
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: f30f9698c9c81322edd6935b40c16cad6f46024c
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/06/2020
ms.locfileid: "80734917"
---
# <a name="idebugbreakpointrequest2"></a>IDebugBreakpointRequest2
Diese Schnittstelle stellt die Informationen dar, die zum Erstellen und Binden eines beliebigen Haltepunkts erforderlich sind.

## <a name="syntax"></a>Syntax

```
IDebugBreakpointRequest2 : IUnknown
```

## <a name="notes-for-implementers"></a>Hinweise für Implementierer
 Der Sitzungsdebug-Manager (SDM) implementiert diese Schnittstelle in der Regel.

## <a name="notes-for-callers"></a>Hinweise für Anrufer
 Das Debugmodul (DE) empfängt diese Schnittstelle über einen Aufruf von [CreatePendingBreakpoint,](../../../extensibility/debugger/reference/idebugengine2-creatependingbreakpoint.md) um einen ausstehenden Haltepunkt zu erstellen. Ein Aufruf von [GetBreakpointRequest](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-getbreakpointrequest.md) kann diese Schnittstelle aus der DE abrufen.

## <a name="methods-in-vtable-order"></a>Methoden in Vtable-Reihenfolge
 Die folgende Tabelle zeigt `IDebugBreakpointRequest2`die Methoden von .

|Methode|BESCHREIBUNG|
|------------|-----------------|
|[GetLocationType](../../../extensibility/debugger/reference/idebugbreakpointrequest2-getlocationtype.md)|Ruft den Haltepunktpositionstyp dieser Haltepunktanforderung ab.|
|[GetRequestInfo](../../../extensibility/debugger/reference/idebugbreakpointrequest2-getrequestinfo.md)|Ruft die Haltepunktanforderungsinformationen ab, die diese Haltepunktanforderung beschreiben.|

## <a name="remarks"></a>Bemerkungen
 Nachdem das zu debuggende Programm geladen wurde, bindet ein Aufruf von [Bind](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-bind.md) einen ausstehenden Haltepunkt an den angeforderten Speicherort im Programm.

## <a name="requirements"></a>Requirements (Anforderungen)
 Kopfzeile: msdbg.h

 Namespace: Microsoft.VisualStudio.Debugger.Interop

 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Weitere Informationen
- [CreatePendingBreakpoint](../../../extensibility/debugger/reference/idebugengine2-creatependingbreakpoint.md)
- [GetBreakpointRequest](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-getbreakpointrequest.md)
- [Binden](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-bind.md)
