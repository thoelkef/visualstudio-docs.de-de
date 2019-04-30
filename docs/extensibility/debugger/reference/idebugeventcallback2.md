---
title: IDebugEventCallback2 | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugEventCallback2
helpviewer_keywords:
- IDebugEventCallback2
ms.assetid: 2c935ee0-2e22-4be0-a852-73736f33c8c9
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: d8d05ea232513a161b3123e08a20bc0f5b312b89
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62920282"
---
# <a name="idebugeventcallback2"></a>IDebugEventCallback2
Diese Schnittstelle wird von der Debug-Engine (DE) verwendet, um Debug-Ereignisse an die sitzungsbasierter Debug-Manager (SDM) zu senden.

## <a name="syntax"></a>Syntax

```
IDebugEventCallback2 : IUnknown
```

## <a name="notes-for-implementers"></a>Hinweise für Implementierer
 [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)] implementiert diese Schnittstelle zum Empfangen von Ereignissen aus einer Debug-Engine.

## <a name="notes-for-callers"></a>Hinweise für Aufrufer
 Eine Debug-Engine diese Schnittstelle in der Regel empfängt beim aufruft, des SDM [Anfügen](../../../extensibility/debugger/reference/idebugprogram2-attach.md), [Anfügen](../../../extensibility/debugger/reference/idebugengine2-attach.md), oder [LaunchSuspended](../../../extensibility/debugger/reference/idebugenginelaunch2-launchsuspended.md). Eine Debug-Engine sendet Ereignisse an das SDM, durch den Aufruf [Ereignis](../../../extensibility/debugger/reference/idebugeventcallback2-event.md).

## <a name="methods-in-vtable-order"></a>Methoden in Vtable-Reihenfolge
 Die folgende Tabelle zeigt die Methoden der `IDebugEventCallback2`.

|Methode|Beschreibung|
|------------|-----------------|
|[Event](../../../extensibility/debugger/reference/idebugeventcallback2-event.md)|Sendet eine Benachrichtigung der Ereignisse an das SDM-Debuggen.|

## <a name="remarks"></a>Hinweise
 Obwohl [EvaluateSync](../../../extensibility/debugger/reference/idebugexpression2-evaluatesync.md) und [EvaluateAsync](../../../extensibility/debugger/reference/idebugexpression2-evaluateasync.md) anzugeben, dass dafür ein `IDebugEventCallback2` -Schnittstelle, dies ist nicht der Fall ist, und der Schnittstellenzeiger wird immer ein null-Wert sein. Die Debug-Engine muss stattdessen die `IDebugEventCallback2` Schnittstelle empfangen, die im Aufruf von [Anfügen](../../../extensibility/debugger/reference/idebugprogram2-attach.md), [Anfügen](../../../extensibility/debugger/reference/idebugengine2-attach.md), oder [LaunchSuspended](../../../extensibility/debugger/reference/idebugenginelaunch2-launchsuspended.md).

 Wenn ein Paket implementiert [IDebugEventCallback](../../../extensibility/debugger/reference/idebugeventcallback2.md) in verwaltetem Code, es wird dringend empfohlen, die <xref:System.Runtime.InteropServices.Marshal.ReleaseComObject%2A> aufgerufen werden, auf die verschiedenen Schnittstellen, die übergeben werden [Ereignis](../../../extensibility/debugger/reference/idebugeventcallback2-event.md).

## <a name="requirements"></a>Anforderungen
 Header: msdbg.h

 Namespace: Microsoft.VisualStudio.Debugger.Interop

 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Siehe auch
- [Wichtige Schnittstellen](../../../extensibility/debugger/reference/core-interfaces.md)
- [LaunchSuspended](../../../extensibility/debugger/reference/idebugenginelaunch2-launchsuspended.md)
- [Anfügen](../../../extensibility/debugger/reference/idebugprogram2-attach.md)
- [Anfügen](../../../extensibility/debugger/reference/idebugengine2-attach.md)