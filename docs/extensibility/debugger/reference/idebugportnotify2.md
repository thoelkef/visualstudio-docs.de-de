---
title: IDebugPortnotify2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugPortNotify2
helpviewer_keywords:
- IDebugPortNotify2 interface
ms.assetid: 43278b79-bf16-4c08-bcf1-6f7f7a17feab
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 49d3d1161d488ed4a9e12b7af6b70bf336c9f286
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/06/2020
ms.locfileid: "80724921"
---
# <a name="idebugportnotify2"></a>IDebugPortNotify2
Diese Schnittstelle registriert oder entfällt die Registrierung eines Programms, das mit dem Port, auf dem es ausgeführt wird, gedebuggég werden kann.

## <a name="syntax"></a>Syntax

```
IDebugPortNotify2 : IUnknown
```

## <a name="notes-for-implementers"></a>Hinweise für Implementierer
 Ein benutzerdefinierter Portlieferant implementiert diese Schnittstelle, um das Hinzufügen und Entfernen von Programmen aus dem Port zu unterstützen. Es wird in der Regel auf demselben Objekt implementiert, das die [IDebugPort2-Schnittstelle](../../../extensibility/debugger/reference/idebugport2.md) implementiert.

## <a name="notes-for-callers"></a>Hinweise für Anrufer
 Ein Aufruf von [QueryInterface](/cpp/atl/queryinterface) auf der `IDebugPort2` Schnittstelle gibt diese Schnittstelle zurück. Außerdem gibt ein Aufruf von [GetPortNotify](../../../extensibility/debugger/reference/idebugdefaultport2-getportnotify.md) diese Schnittstelle zurück. Ein Debugmodul kann diese Schnittstelle als Parameter für [WatchForProviderEvents](../../../extensibility/debugger/reference/idebugprogramprovider2-watchforproviderevents.md)anzeigen.

## <a name="methods-in-vtable-order"></a>Methoden in Vtable-Reihenfolge
 Die folgende Tabelle zeigt `IDebugPortNotify2`die Methoden von .

|Methode|BESCHREIBUNG|
|------------|-----------------|
|[AddProgramNode](../../../extensibility/debugger/reference/idebugportnotify2-addprogramnode.md)|Registriert ein Programm, das mit dem Port, auf dem es ausgeführt wird, gedebuggég werden kann.|
|[RemoveProgramNode](../../../extensibility/debugger/reference/idebugportnotify2-removeprogramnode.md)|Entregistriert ein Programm, das von dem Port, auf dem es ausgeführt wird, gedebuggen werden kann.|

## <a name="remarks"></a>Bemerkungen
 Sofern ein Debugport nicht wissen kann, wann Programme geladen oder entladen werden, muss ein benutzerdefinierter Portlieferant diese Schnittstelle implementieren. Alle Programme, die zum Debuggen über einen bestimmten Port geladen werden, werden über diese Schnittstelle nachverfolgt.

## <a name="requirements"></a>Requirements (Anforderungen)
 Kopfzeile: msdbg.h

 Namespace: Microsoft.VisualStudio.Debugger.Interop

 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Weitere Informationen
- [Wichtige Schnittstellen](../../../extensibility/debugger/reference/core-interfaces.md)
- [IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md)
