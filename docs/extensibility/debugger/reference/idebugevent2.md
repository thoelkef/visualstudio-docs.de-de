---
title: IDebugEvent2 | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugEvent2
helpviewer_keywords:
- IDebugEvent2 interface
ms.assetid: de3d714d-96fb-4e12-b66b-a75391472153
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: f87184481c5d01e74d284b175078b67f6f2612d1
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/29/2019
ms.locfileid: "66310598"
---
# <a name="idebugevent2"></a>IDebugEvent2
Diese Schnittstelle wird verwendet, für die Kommunikation sowohl sehr wichtige Debuginformationen, z. B. an einem Haltepunkt beendet und nicht kritische Informationen, z. B. eine Debugmeldung.

## <a name="syntax"></a>Syntax

```
IDebugEvent2 : IUnknown
```

## <a name="notes-for-implementers"></a>Hinweise für Implementierer
 Die Debug-Engine (DE) und benutzerdefinierte anschlusslieferant implementieren diese Schnittstelle auf dasselbe Objekt wie alle anderen Event-Schnittstellen.

## <a name="notes-for-callers"></a>Hinweise für Aufrufer
 Mithilfe der Benutzeroberfläche-ID (IID)-Argument übergeben, um [Ereignis](../../../extensibility/debugger/reference/idebugeventcallback2-event.md) oder [Ereignis](../../../extensibility/debugger/reference/idebugportevents2-event.md), ruft die Sitzungs-Debug-Manager (SDM) [QueryInterface](/cpp/atl/queryinterface) auf die `IDebugEvent2` Schnittstelle zum Abrufen die entsprechende Schnittstelle.

## <a name="methods-in-vtable-order"></a>Methoden in Vtable-Reihenfolge
 Die folgende Tabelle zeigt die Methoden der `IDebugEvent2`.

|Methode|Beschreibung|
|------------|-----------------|
|[GetAttributes](../../../extensibility/debugger/reference/idebugevent2-getattributes.md)|Ruft die Attribute für dieses Ereignis Debuggen.|

## <a name="remarks"></a>Hinweise
 Schnittstellen für das spezifische Ereignis, z. B. [IDebugBreakpointEvent2](../../../extensibility/debugger/reference/idebugbreakpointevent2.md), leiten Sie nicht über die IDebugEvent2-Schnittstelle, sondern werden stattdessen als eine separate Schnittstelle auf dasselbe Objekt wie implementiert `IDebugEvent2`.

## <a name="requirements"></a>Anforderungen
 Header: msdbg.h

 Namespace: Microsoft.VisualStudio.Debugger.Interop

 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Siehe auch
- [Wichtige Schnittstellen](../../../extensibility/debugger/reference/core-interfaces.md)
- [Event](../../../extensibility/debugger/reference/idebugportevents2-event.md)
- [Event](../../../extensibility/debugger/reference/idebugeventcallback2-event.md)