---
title: IDebugPortSupplier3 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugPortSupplier3
helpviewer_keywords:
- IDebugPortSupplier3 interface
ms.assetid: e458cd02-2370-4435-8953-17d7a60ce152
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: f015c21f71f064f2302660ebc75ef00a245348c3
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/06/2020
ms.locfileid: "80724438"
---
# <a name="idebugportsupplier3"></a>IDebugPortSupplier3
Diese Schnittstelle ermöglicht es einem Aufrufer zu bestimmen, ob ein Portlieferant Ports zwischen Aufrufen des Debuggers beibehalten (durch Schreiben auf den Datenträger) beibehalten und dann eine Liste dieser erhaltenen Ports abrufen kann.

## <a name="syntax"></a>Syntax

```
IDebugPortSupplier3 : IDebugPortSupplier2
```

## <a name="notes-for-implementers"></a>Hinweise für Implementierer
 Ein benutzerdefinierter Portlieferant implementiert diese Schnittstelle, um das Beibehalten oder Speichern von Portinformationen auf dem Datenträger zu unterstützen. Diese Schnittstelle muss für dasselbe Objekt wie die [IDebugPortSupplier2-Schnittstelle](../../../extensibility/debugger/reference/idebugportsupplier2.md) implementiert werden.

## <a name="notes-for-callers"></a>Hinweise für Anrufer
 Rufen Sie [QueryInterface](/cpp/atl/queryinterface) auf der `IDebugPortSupplier2` Schnittstelle auf, um diese Schnittstelle zu erhalten.

## <a name="methods-in-vtable-order"></a>Methoden in Vtable-Reihenfolge
 Zusätzlich zu den Methoden, die von der [IDebugPortSupplier2-Schnittstelle](../../../extensibility/debugger/reference/idebugportsupplier2.md) geerbt wurden, unterstützt diese Schnittstelle Folgendes:

|Methode|BESCHREIBUNG|
|------------|-----------------|
|[CanPersistPorts](../../../extensibility/debugger/reference/idebugportsupplier3-canpersistports.md)|Gibt zurück, ob der Portlieferant Ports zwischen Aufrufen des Debuggers beibehalten kann (durch Schreiben auf den Datenträger).|
|[EnumPersistedPorts](../../../extensibility/debugger/reference/idebugportsupplier3-enumpersistedports.md)|Gibt ein Objekt zurück, das zum Aufzählen aller Ports verwendet werden kann, die von diesem Portlieferanten auf den Datenträger geschrieben wurden.|

## <a name="remarks"></a>Bemerkungen
 Wenn ein Portlieferant Ports über Aufrufe hinweg beibehalten kann, sollte er diese Schnittstelle implementieren. Ports sollten geladen werden, wenn der Portlieferant instanziiert wird, und auf die Festplatte geschrieben werden, wenn der Portlieferant zerstört wird.

 Ein Debugmodul interagiert in der Regel nicht mit einem Portlieferanten und hat keine Verwendung für diese Schnittstelle.

## <a name="requirements"></a>Requirements (Anforderungen)
 Kopfzeile: msdbg.h

 Namespace: Microsoft.VisualStudio.Debugger.Interop

 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Weitere Informationen
- [Wichtige Schnittstellen](../../../extensibility/debugger/reference/core-interfaces.md)
- [IDebugPortSupplier2](../../../extensibility/debugger/reference/idebugportsupplier2.md)
