---
title: IDebugProgramEngines2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProgramEngines2
helpviewer_keywords:
- IDebugProgramEngines2 interface
ms.assetid: 53d648f0-6c11-4337-badd-c43f3872b62c
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 94df9acc6a0478ba2cb36022bc8618c69be97b8c
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/06/2020
ms.locfileid: "80722403"
---
# <a name="idebugprogramengines2"></a>IDebugProgramEngines2
Diese Schnittstelle wird von Programmknoten verwendet, um alle möglichen Debug-Engines (DE) anzugeben, die dieses Programm debuggen können.

## <a name="syntax"></a>Syntax

```
IDebugProgramEngines2 : IUnknown
```

## <a name="notes-for-implementers"></a>Hinweise für Implementierer
 Ein DE oder ein benutzerdefinierter Portlieferant implementiert diese Schnittstelle für dasselbe Objekt, das [IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md) implementiert, um das Einrichten einer bestimmten DE zu unterstützen, die für ein bestimmtes Programm verwendet werden soll.

## <a name="notes-for-callers"></a>Hinweise für Anrufer
 Rufen Sie [QueryInterface](/cpp/atl/queryinterface) auf einer `IDebugProgramNode2` Schnittstelle auf, um diese Schnittstelle zu erhalten.

## <a name="methods-in-vtable-order"></a>Methoden in Vtable-Reihenfolge
 Die folgende Tabelle zeigt `IDebugProgramEngines2`die Methoden von .

|Methode|BESCHREIBUNG|
|------------|-----------------|
|[EnumPossibleEngines](../../../extensibility/debugger/reference/idebugprogramengines2-enumpossibleengines.md)|Gibt alle möglichen DEs an, die dieses Programm debuggen können.|
|[SetEngine](../../../extensibility/debugger/reference/idebugprogramengines2-setengine.md)|Wählt die DE aus, die zum Debuggen dieses Programms verwendet werden soll.|

## <a name="remarks"></a>Bemerkungen
 Sobald ein DE vom Benutzer ausgewählt wurde, wird diese Auswahl beim Programmknoten registriert, indem [SetEngine](../../../extensibility/debugger/reference/idebugprogramengines2-setengine.md)aufgerufen wird. Das ausgewählte Modul wird zum von [GetEngineInfo](../../../extensibility/debugger/reference/idebugprogramnode2-getengineinfo.md)zurückgegebenen Modul.

## <a name="requirements"></a>Requirements (Anforderungen)
 Kopfzeile: msdbg.h

 Namespace: Microsoft.VisualStudio.Debugger.Interop

 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Weitere Informationen
- [Wichtige Schnittstellen](../../../extensibility/debugger/reference/core-interfaces.md)
- [IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md)
- [GetEngineInfo](../../../extensibility/debugger/reference/idebugprogramnode2-getengineinfo.md)
