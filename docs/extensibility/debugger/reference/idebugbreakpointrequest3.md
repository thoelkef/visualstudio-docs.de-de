---
title: IDebugBreakpointRequest3 | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugBreakpointRequest3
helpviewer_keywords:
- IDebugBreakpointRequest3
ms.assetid: 8a042beb-b319-48e3-b3c8-9c8336ab371b
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 9101f1c2faeedf8b08b3b11044eaa22f6c6d512a
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/29/2019
ms.locfileid: "66352874"
---
# <a name="idebugbreakpointrequest3"></a>IDebugBreakpointRequest3
Diese Schnittstelle stellt die erforderlichen Informationen zum Erstellen und binden jeden Typ von Breakpoint. Es ist eine Erweiterung der [IDebugBreakpointRequest2](../../../extensibility/debugger/reference/idebugbreakpointrequest2.md).

## <a name="syntax"></a>Syntax

```
IDebugBreakpointRequest3 : IDebugBreakpointRequest2
```

## <a name="notes-for-implementers"></a>Hinweise für Implementierer
 Diese Schnittstelle wird von der Sitzungs-Manager (SDM) in der Regel implementiert.

## <a name="notes-for-callers"></a>Hinweise für Aufrufer
 Die Debug-Engine (DE) greift auf diese Schnittstelle durch den Aufruf [QueryInterface](/cpp/atl/queryinterface) für die IDebugBreakpointRequest2-Schnittstelle, die in einem Aufruf empfangen [CreatePendingBreakpoint](../../../extensibility/debugger/reference/idebugengine2-creatependingbreakpoint.md).

## <a name="methods-in-vtable-order"></a>Methoden in Vtable-Reihenfolge
 Zusätzlich zu den von geerbten Methoden [IDebugBreakpointRequest2](../../../extensibility/debugger/reference/idebugbreakpointrequest2.md), `IDebugBreakpointRequest3` Schnittstelle verfügbar macht, die folgende Methode.

|Methode|Beschreibung|
|------------|-----------------|
|[GetRequestInfo2](../../../extensibility/debugger/reference/idebugbreakpointrequest3-getrequestinfo2.md)|Ruft ab, der diese Anforderung Breakpoint beschreibt Informationen zu den Haltepunkt.|

## <a name="remarks"></a>Hinweise
 Diese Schnittstelle wird verwendet, um zusätzliche Informationen für das DE durch Bereitstellen der [BP_REQUEST_INFO2](../../../extensibility/debugger/reference/bp-request-info2.md) Struktur. Diese zusätzlichen Informationen enthält, die DE Anbieter-ID (in Form einer GUID), den Namen der Ablaufverfolgungspunkt und der Name einer Einschränkung Haltepunkt.

## <a name="requirements"></a>Anforderungen
 Header: msdbg.h

 Namespace: Microsoft.VisualStudio.Debugger.Interop

 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Siehe auch
- [IDebugBreakpointRequest2](../../../extensibility/debugger/reference/idebugbreakpointrequest2.md)
- [BP_REQUEST_INFO2](../../../extensibility/debugger/reference/bp-request-info2.md)