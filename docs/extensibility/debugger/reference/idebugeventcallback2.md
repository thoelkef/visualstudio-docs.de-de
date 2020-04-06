---
title: IDebugEventCallback2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugEventCallback2
helpviewer_keywords:
- IDebugEventCallback2
ms.assetid: 2c935ee0-2e22-4be0-a852-73736f33c8c9
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: a74825a955afdde03e63673c4b1b6afda5904953
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/06/2020
ms.locfileid: "80729883"
---
# <a name="idebugeventcallback2"></a>IDebugEventCallback2
Diese Schnittstelle wird vom Debugmodul (DE) verwendet, um Debugereignisse an den Sitzungsdebug-Manager (SDM) zu senden.

## <a name="syntax"></a>Syntax

```
IDebugEventCallback2 : IUnknown
```

## <a name="notes-for-implementers"></a>Hinweise für Implementierer
 [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)]implementiert diese Schnittstelle, um Ereignisse von einem Debugmodul zu empfangen.

## <a name="notes-for-callers"></a>Hinweise für Anrufer
 Ein Debugmodul empfängt diese Schnittstelle in der Regel, wenn das SDM [Attach](../../../extensibility/debugger/reference/idebugprogram2-attach.md), [Attach](../../../extensibility/debugger/reference/idebugengine2-attach.md)oder [LaunchSuspended](../../../extensibility/debugger/reference/idebugenginelaunch2-launchsuspended.md)aufruft. Ein Debugmodul sendet Ereignisse an das SDM, indem [ereignisgebunden](../../../extensibility/debugger/reference/idebugeventcallback2-event.md)aufgerufen wird.

## <a name="methods-in-vtable-order"></a>Methoden in Vtable-Reihenfolge
 Die folgende Tabelle zeigt `IDebugEventCallback2`die Methoden von .

|Methode|BESCHREIBUNG|
|------------|-----------------|
|[Ereignis](../../../extensibility/debugger/reference/idebugeventcallback2-event.md)|Sendet Benachrichtigungen über das Debuggen von Ereignissen an das SDM.|

## <a name="remarks"></a>Bemerkungen
 [Obwohl EvaluateSync](../../../extensibility/debugger/reference/idebugexpression2-evaluatesync.md) und [EvaluateAsync](../../../extensibility/debugger/reference/idebugexpression2-evaluateasync.md) angeben, dass sie eine `IDebugEventCallback2` Schnittstelle annehmen, ist dies nicht der Fall, und der Schnittstellenzeiger ist immer ein NULL-Wert. Stattdessen muss das Debugmodul `IDebugEventCallback2` die Schnittstelle verwenden, die im Aufruf von [Attach](../../../extensibility/debugger/reference/idebugprogram2-attach.md), [Attach](../../../extensibility/debugger/reference/idebugengine2-attach.md)oder [LaunchSuspended](../../../extensibility/debugger/reference/idebugenginelaunch2-launchsuspended.md)empfangen wurde.

 Wenn ein Paket [IDebugEventCallback](../../../extensibility/debugger/reference/idebugeventcallback2.md) in verwaltetem Code <xref:System.Runtime.InteropServices.Marshal.ReleaseComObject%2A> implementiert, wird dringend empfohlen, auf den verschiedenen Schnittstellen, die an [Event](../../../extensibility/debugger/reference/idebugeventcallback2-event.md)übergeben werden, aufgerufen zu werden.

## <a name="requirements"></a>Requirements (Anforderungen)
 Kopfzeile: msdbg.h

 Namespace: Microsoft.VisualStudio.Debugger.Interop

 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Weitere Informationen
- [Wichtige Schnittstellen](../../../extensibility/debugger/reference/core-interfaces.md)
- [LaunchSuspended](../../../extensibility/debugger/reference/idebugenginelaunch2-launchsuspended.md)
- [Anfügen](../../../extensibility/debugger/reference/idebugprogram2-attach.md)
- [Anfügen](../../../extensibility/debugger/reference/idebugengine2-attach.md)
