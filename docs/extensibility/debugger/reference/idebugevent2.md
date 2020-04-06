---
title: IDebugEvent2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugEvent2
helpviewer_keywords:
- IDebugEvent2 interface
ms.assetid: de3d714d-96fb-4e12-b66b-a75391472153
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: a6341f8003b962a7f45420b076b23623ebdaf861
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/06/2020
ms.locfileid: "80729911"
---
# <a name="idebugevent2"></a>IDebugEvent2
Diese Schnittstelle wird verwendet, um sowohl wichtige Debuginformationen, z. B. das Anhalten an einem Haltepunkt, als auch nicht kritische Informationen, z. B. eine Debugnachricht, zu kommunizieren.

## <a name="syntax"></a>Syntax

```
IDebugEvent2 : IUnknown
```

## <a name="notes-for-implementers"></a>Hinweise für Implementierer
 Das Debugmodul (DE) und der benutzerdefinierte Portlieferant implementieren diese Schnittstelle auf demselben Objekt wie alle anderen Ereignisschnittstellen.

## <a name="notes-for-callers"></a>Hinweise für Anrufer
 Mithilfe des IID-Arguments (Interface ID), das [Ereignis](../../../extensibility/debugger/reference/idebugeventcallback2-event.md) oder [Ereignis](../../../extensibility/debugger/reference/idebugportevents2-event.md)angegeben wird, ruft der Sitzungsdebug-Manager (SDM) [QueryInterface](/cpp/atl/queryinterface) auf der `IDebugEvent2` Schnittstelle auf, um die entsprechende Ereignisschnittstelle abzufragen.

## <a name="methods-in-vtable-order"></a>Methoden in Vtable-Reihenfolge
 Die folgende Tabelle zeigt `IDebugEvent2`die Methoden von .

|Methode|BESCHREIBUNG|
|------------|-----------------|
|[Getattributes](../../../extensibility/debugger/reference/idebugevent2-getattributes.md)|Ruft die Attribute für dieses Debugereignis ab.|

## <a name="remarks"></a>Bemerkungen
 Die spezifischeren Ereignisschnittstellen, z. B. [IDebugBreakpointEvent2](../../../extensibility/debugger/reference/idebugbreakpointevent2.md), leiten sich nicht von der IDebugEvent2-Schnittstelle `IDebugEvent2`ab, sondern werden stattdessen als separate Schnittstelle für dasselbe Objekt wie implementiert.

## <a name="requirements"></a>Requirements (Anforderungen)
 Kopfzeile: msdbg.h

 Namespace: Microsoft.VisualStudio.Debugger.Interop

 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Weitere Informationen
- [Wichtige Schnittstellen](../../../extensibility/debugger/reference/core-interfaces.md)
- [Ereignis](../../../extensibility/debugger/reference/idebugportevents2-event.md)
- [Ereignis](../../../extensibility/debugger/reference/idebugeventcallback2-event.md)
