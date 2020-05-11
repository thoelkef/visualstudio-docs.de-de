---
title: IDebugBreakpointRequest3 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugBreakpointRequest3
helpviewer_keywords:
- IDebugBreakpointRequest3
ms.assetid: 8a042beb-b319-48e3-b3c8-9c8336ab371b
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 505b0c0b05fa0f14578d770abec6c43ed6b80b01
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/06/2020
ms.locfileid: "80734827"
---
# <a name="idebugbreakpointrequest3"></a>IDebugBreakpointRequest3
Diese Schnittstelle stellt die Informationen dar, die zum Erstellen und Binden eines beliebigen Haltepunkts erforderlich sind. Es ist eine Erweiterung von [IDebugBreakpointRequest2](../../../extensibility/debugger/reference/idebugbreakpointrequest2.md).

## <a name="syntax"></a>Syntax

```
IDebugBreakpointRequest3 : IDebugBreakpointRequest2
```

## <a name="notes-for-implementers"></a>Hinweise für Implementierer
 Der Sitzungsdebug-Manager (SDM) implementiert diese Schnittstelle in der Regel.

## <a name="notes-for-callers"></a>Hinweise für Anrufer
 Das Debugmodul (DE) greift auf diese Schnittstelle zu, indem [QueryInterface](/cpp/atl/queryinterface) auf der IDebugBreakpointRequest2-Schnittstelle aufgerufen wird, die in einem Aufruf von [CreatePendingBreakpoint](../../../extensibility/debugger/reference/idebugengine2-creatependingbreakpoint.md)empfangen wurde.

## <a name="methods-in-vtable-order"></a>Methoden in Vtable-Reihenfolge
 Zusätzlich zu den Methoden, die von [IDebugBreakpointRequest2](../../../extensibility/debugger/reference/idebugbreakpointrequest2.md)geerbt wurden, macht die `IDebugBreakpointRequest3` Schnittstelle die folgende Methode verfügbar.

|Methode|BESCHREIBUNG|
|------------|-----------------|
|[GetRequestInfo2](../../../extensibility/debugger/reference/idebugbreakpointrequest3-getrequestinfo2.md)|Ruft die Haltepunktanforderungsinformationen ab, die diese Haltepunktanforderung beschreiben.|

## <a name="remarks"></a>Bemerkungen
 Diese Schnittstelle wird verwendet, um der DE über die [BP_REQUEST_INFO2](../../../extensibility/debugger/reference/bp-request-info2.md) Struktur zusätzliche Informationen zur Verfügung zu stellen. Zu diesen zusätzlichen Informationen gehören die Kreditoren-ID der DE (in Form einer GUID), der Name eines Ablaufverfolgungspunkts und der Name einer Haltepunkteinschränkung.

## <a name="requirements"></a>Requirements (Anforderungen)
 Kopfzeile: msdbg.h

 Namespace: Microsoft.VisualStudio.Debugger.Interop

 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Weitere Informationen
- [IDebugBreakpointRequest2](../../../extensibility/debugger/reference/idebugbreakpointrequest2.md)
- [BP_REQUEST_INFO2](../../../extensibility/debugger/reference/bp-request-info2.md)
