---
title: IDebugBreakpointErrorEvent2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugBreakpointErrorEvent2
helpviewer_keywords:
- IDebugBreakpointErrorEvent2
ms.assetid: adee79df-8db5-4510-a7df-c50f4dbf5e35
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 09cb93f0f16420e56104f371d9caab262873390f
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/06/2020
ms.locfileid: "80735040"
---
# <a name="idebugbreakpointerrorevent2"></a>IDebugBreakpointErrorEvent2
Diese Schnittstelle teilt dem Sitzungsdebug-Manager (SDM) mit, dass ein ausstehender Haltepunkt aufgrund einer Warnung oder eines Fehlers nicht an ein geladenes Programm gebunden werden konnte.

## <a name="syntax"></a>Syntax

```
IDebugBreakpointErrorEvent2 : IUnknown
```

## <a name="notes-for-implementers"></a>Hinweise für Implementierer
 Die DE implementiert diese Schnittstelle als Teil ihrer Unterstützung für Haltepunkte. Die [IDebugEvent2-Schnittstelle](../../../extensibility/debugger/reference/idebugevent2.md) muss auf demselben Objekt wie diese Schnittstelle implementiert werden `IDebugEvent2` (das SDM verwendet [QueryInterface,](/cpp/atl/queryinterface) um auf die Schnittstelle zuzugreifen).

## <a name="notes-for-callers"></a>Hinweise für Anrufer
 Die DE erstellt und sendet dieses Ereignisobjekt, wenn ein ausstehender Haltepunkt nicht an das zu debuggende Programm gebunden werden kann. Das Ereignis wird mithilfe der [IDebugEventCallback2-Rückruffunktion](../../../extensibility/debugger/reference/idebugeventcallback2.md) gesendet, die vom SDM bereitgestellt wird, wenn es an das zu debuggende Programm angefügt wird.

## <a name="methods-in-vtable-order"></a>Methoden in Vtable-Reihenfolge
 Die folgende Tabelle zeigt `IDebugBreakpointErrorEvent2`die Methoden von .

|Methode|BESCHREIBUNG|
|------------|-----------------|
|[GetErrorBreakpoint](../../../extensibility/debugger/reference/idebugbreakpointerrorevent2-geterrorbreakpoint.md)|Ruft die [IDebugErrorBreakpoint2-Schnittstelle](../../../extensibility/debugger/reference/idebugerrorbreakpoint2.md) ab, die die Warnung oder den Fehler beschreibt.|

## <a name="remarks"></a>Bemerkungen
 Immer wenn ein Haltepunkt gebunden ist, wird ein Ereignis an das SDM gesendet. Wenn der Haltepunkt nicht `IDebugBreakpointErrorEvent2` gebunden werden kann, wird eine gesendet. Andernfalls wird ein [IDebugBreakpointBoundEvent2](../../../extensibility/debugger/reference/idebugbreakpointboundevent2.md) gesendet.

 Wenn z. B. die dem ausstehenden Haltepunkt zugeordnete Bedingung nicht analysiert oder ausgewertet werden kann, wird eine Warnung gesendet, dass der ausstehende Haltepunkt derzeit nicht gebunden werden kann. Dies kann auftreten, wenn der Code für den Haltepunkt noch nicht geladen wurde.

## <a name="requirements"></a>Requirements (Anforderungen)
 Kopfzeile: msdbg.h

 Namespace: Microsoft.VisualStudio.Debugger.Interop

 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Weitere Informationen
- [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md)
- [IDebugErrorBreakpoint2](../../../extensibility/debugger/reference/idebugerrorbreakpoint2.md)
- [IDebugPendingBreakpoint2](../../../extensibility/debugger/reference/idebugpendingbreakpoint2.md)
- [IDebugBreakpointBoundEvent2](../../../extensibility/debugger/reference/idebugbreakpointboundevent2.md)
- [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md)
