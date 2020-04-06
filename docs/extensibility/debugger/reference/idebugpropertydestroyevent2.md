---
title: IDebugPropertyDestroyEvent2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugPropertyDestroyEvent2
helpviewer_keywords:
- IDebugPropertyDestroyEvent2 interface
ms.assetid: 301b7a75-ecfa-46f1-9131-66cf3e4be147
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: ce15f389f22513e08b06c0d097cdac4aec3c35bf
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/06/2020
ms.locfileid: "80720905"
---
# <a name="idebugpropertydestroyevent2"></a>IDebugPropertyDestroyEvent2
Diese Schnittstelle wird vom Debugmodul (DE) an den Sitzungsdebug-Manager (SDM) gesendet, wenn eine Eigenschaft, die einem bestimmten Dokument zugeordnet ist, zerstört werden soll.

## <a name="syntax"></a>Syntax

```
IDebugPropertyDestroyEvent2 : IUnknown
```

## <a name="notes-for-implementers"></a>Hinweise für Implementierer
 Die DE implementiert diese Schnittstelle, um zu melden, dass eine Eigenschaft zerstört wurde. Die [IDebugEvent2-Schnittstelle](../../../extensibility/debugger/reference/idebugevent2.md) muss für dasselbe Objekt wie diese Schnittstelle implementiert werden. Das SDM verwendet [QueryInterface,](/cpp/atl/queryinterface) um auf die `IDebugEvent2` Schnittstelle zuzugreifen. Diese Schnittstelle wird implementiert, wenn die DE zuvor eine Eigenschaft erstellt hat, die einem Skript zugeordnet ist. Durch das Zerstören der Eigenschaft wird das zugehörige Skript aus der IDE entfernt.

## <a name="notes-for-callers"></a>Hinweise für Anrufer
 Die DE erstellt und sendet dieses Ereignisobjekt, um zu melden, dass eine Eigenschaft zerstört wurde. Das Ereignis wird mithilfe der [IDebugEventCallback2-Rückruffunktion](../../../extensibility/debugger/reference/idebugeventcallback2.md) gesendet, die vom SDM bereitgestellt wird, wenn es an das zu debuggende Programm angefügt wird.

## <a name="methods-in-vtable-order"></a>Methoden in Vtable-Reihenfolge
 Die folgende Tabelle zeigt `IDebugPropertyDestroyEvent2`die Methode von .

|Methode|BESCHREIBUNG|
|------------|-----------------|
|[GetDebugProperty](../../../extensibility/debugger/reference/idebugpropertydestroyevent2-getdebugproperty.md)|Ruft die zu zerstörende Eigenschaft ab.|

## <a name="remarks"></a>Bemerkungen
 Weitere Informationen zur Verwendung dieser Ereignisse finden Sie in den Anmerkungen zu [IDebugPropertyCreateEvent2.](../../../extensibility/debugger/reference/idebugpropertycreateevent2.md)

## <a name="requirements"></a>Requirements (Anforderungen)
 Kopfzeile: msdbg.h

 Namespace: Microsoft.VisualStudio.Debugger.Interop

 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Weitere Informationen
- [Wichtige Schnittstellen](../../../extensibility/debugger/reference/core-interfaces.md)
- [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md)
- [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md)
- [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)
- [IDebugPropertyCreateEvent2](../../../extensibility/debugger/reference/idebugpropertycreateevent2.md)
