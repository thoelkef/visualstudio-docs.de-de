---
title: IDebugCoreServer2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugCoreServer2
helpviewer_keywords:
- IDebugCoreServer2 interface
ms.assetid: 9c47d0a6-9eb1-464e-bd44-fa2b552d4d36
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 7a5990c84fbaeb5ebb3b1e188d3317234afda06b
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/06/2020
ms.locfileid: "80733036"
---
# <a name="idebugcoreserver2"></a>IDebugCoreServer2
Diese Schnittstelle wird verwendet, um Informationen von einem Server auf einem Computer im Netzwerk darzustellen und zu erhalten.

## <a name="syntax"></a>Syntax

```
IDebugCoreServer2 : IUknown
```

## <a name="notes-for-implementers"></a>Hinweise für Implementierer
 Visual Studio implementiert diese Schnittstelle, um einen Server darzustellen. Jede Instanz von Visual Studio erstellt eine Instanz dieser Schnittstelle.

## <a name="notes-for-callers"></a>Hinweise für Anrufer
 Ein benutzerdefinierter Portlieferant empfängt diese Schnittstelle in einem Aufruf von [Event](../../../extensibility/debugger/reference/idebugportevents2-event.md).

 Ein Debugmodul kann diese Schnittstelle indirekt über einen Aufruf von [GetServer](../../../extensibility/debugger/reference/idebugdefaultport2-getserver.md) abrufen (der `IDebugCoreServer2` [IDebugCoreServer3](../../../extensibility/debugger/reference/idebugcoreserver3.md)zurückgibt , eine Schnittstelle, die von abgeleitet wird).

## <a name="methods-in-vtable-order"></a>Methoden in Vtable-Reihenfolge
 Die folgende Tabelle zeigt `IDebugCoreServer2`die Methoden von .

|Methode|BESCHREIBUNG|
|------------|-----------------|
|[GetMachineInfo](../../../extensibility/debugger/reference/idebugcoreserver2-getmachineinfo.md)|Ruft den Namen und die Attribute eines Computers ab.|
|[GetMachineName](../../../extensibility/debugger/reference/idebugcoreserver2-getmachinename.md)|Ruft den Namen eines Computers ab.|
|[GetPortSupplier](../../../extensibility/debugger/reference/idebugcoreserver2-getportsupplier.md)|Ruft einen Portlieferanten ab, der auf einem Computer vorhanden ist.|
|[GetPort](../../../extensibility/debugger/reference/idebugcoreserver2-getport.md)|Ruft einen Port ab, der bereits auf einem Computer vorhanden ist.|
|[EnumPorts](../../../extensibility/debugger/reference/idebugcoreserver2-enumports.md)|Erstellt einen Enumerator für alle Ports auf einem Computer.|
|[EnumPortSuppliers](../../../extensibility/debugger/reference/idebugcoreserver2-enumportsuppliers.md)|Erstellt einen Enumerator für alle Hafenlieferanten auf einer Maschine.|
|[GetMachineUtilities_V7](../../../extensibility/debugger/reference/idebugcoreserver2-getmachineutilities-v7.md)|Ruft die Computerdienstprogramme für einen Computer ab.|

## <a name="remarks"></a>Bemerkungen
 Diese Schnittstelle wird auch von Visual Studio verwendet, um Prozesse zu durchsuchen, die auf Computern im Netzwerk ausgeführt werden.

## <a name="requirements"></a>Requirements (Anforderungen)
 Kopfzeile: msdbg.h

 Namespace: Microsoft.VisualStudio.Debugger.Interop

 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Weitere Informationen
- [IDebugPort2](../../../extensibility/debugger/reference/idebugport2.md)
- [Ereignis](../../../extensibility/debugger/reference/idebugportevents2-event.md)
- [GetServer](../../../extensibility/debugger/reference/idebugdefaultport2-getserver.md)
- [IDebugCoreServer3](../../../extensibility/debugger/reference/idebugcoreserver3.md)
