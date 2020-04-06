---
title: IDebugBreakpointBoundEvent2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugBreakpointBoundEvent2
helpviewer_keywords:
- IDebugBreakpointBoundEvent2
ms.assetid: 24ba362e-5be1-481a-b071-e1ebd3cae6e8
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 7943addb4334710da3252a4d822330e45b6e0f80
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/06/2020
ms.locfileid: "80735313"
---
# <a name="idebugbreakpointboundevent2"></a>IDebugBreakpointBoundEvent2
Diese Schnittstelle teilt dem Sitzungsdebug-Manager (SDM) mit, dass ein ausstehender Haltepunkt erfolgreich an ein geladenes Programm gebunden wurde.

## <a name="syntax"></a>Syntax

```
IDebugBreakpointBoundEvent2 : IUnknown
```

## <a name="notes-for-implementers"></a>Hinweise für Implementierer
 Die DE implementiert diese Schnittstelle als Teil ihrer Unterstützung für Haltepunkte. Die [IDebugEvent2-Schnittstelle](../../../extensibility/debugger/reference/idebugevent2.md) muss auf demselben Objekt wie diese Schnittstelle implementiert werden `IDebugEvent2` (das SDM verwendet [QueryInterface,](/cpp/atl/queryinterface) um auf die Schnittstelle zuzugreifen).

## <a name="notes-for-callers"></a>Hinweise für Anrufer
 Die DE erstellt und sendet dieses Ereignisobjekt, wenn ein ausstehender Haltepunkt erfolgreich an das zu debuggende Programm gebunden ist. Das Ereignis wird mithilfe der [IDebugEventCallback2-Rückruffunktion](../../../extensibility/debugger/reference/idebugeventcallback2.md) gesendet, die vom SDM bereitgestellt wird, wenn es an das zu debuggende Programm angefügt wird.

## <a name="methods-in-vtable-order"></a>Methoden in Vtable-Reihenfolge
 Die folgende Tabelle zeigt `IDebugBreakpointBoundEvent2`die Methoden von .

|Methode|BESCHREIBUNG|
|------------|-----------------|
|[GetPendingBreakpoint](../../../extensibility/debugger/reference/idebugbreakpointboundevent2-getpendingbreakpoint.md)|Ruft den ausstehenden Haltepunkt ab, der gebunden wird.|
|[EnumBoundBreakpoints](../../../extensibility/debugger/reference/idebugbreakpointboundevent2-enumboundbreakpoints.md)|Erstellt einen Enumerator von Haltepunkten, die an dieses Ereignis gebunden waren.|

## <a name="remarks"></a>Bemerkungen
 Immer wenn ein Haltepunkt gebunden ist, wird ein Ereignis an das SDM gesendet. Wenn der Haltepunkt nicht gebunden werden kann, wird ein [IDebugBreakpointErrorEvent2](../../../extensibility/debugger/reference/idebugbreakpointerrorevent2.md) gesendet. andernfalls wird `IDebugBreakpointBoundEvent2` ein gesendet.

## <a name="requirements"></a>Requirements (Anforderungen)
 Kopfzeile: msdbg.h

 Namespace: Microsoft.VisualStudio.Debugger.Interop

 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Weitere Informationen
- [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md)
- [IDebugPendingBreakpoint2](../../../extensibility/debugger/reference/idebugpendingbreakpoint2.md)
- [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md)
- [IDebugBreakpointErrorEvent2](../../../extensibility/debugger/reference/idebugbreakpointerrorevent2.md)
