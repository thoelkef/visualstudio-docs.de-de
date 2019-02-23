---
title: IDebugPortSupplier3 | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugPortSupplier3
helpviewer_keywords:
- IDebugPortSupplier3 interface
ms.assetid: e458cd02-2370-4435-8953-17d7a60ce152
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: ca7113a1b108713b5dd7cf0f17511cec39a1b8b6
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/22/2019
ms.locfileid: "56695491"
---
# <a name="idebugportsupplier3"></a>IDebugPortSupplier3
Diese Schnittstelle ermöglicht es einen Aufrufer, die bestimmen, ob ein portanbieters beizubehalten, die Ports (auf Datenträger schreiben) zwischen den Aufrufen des Debuggers und Sie anschließend eine Liste mit diesen beibehaltenen Ports rufen kann.

## <a name="syntax"></a>Syntax

```
IDebugPortSupplier3 : IDebugPortSupplier2
```

## <a name="notes-for-implementers"></a>Hinweise für Implementierer
 Ein benutzerdefinierten Port Lieferanten implementiert diese Schnittstelle zum beibehalten oder Speichern von Informationen auf dem Datenträger unterstützt. Diese Schnittstelle muss implementiert werden, auf das gleiche Objekt wie die [IDebugPortSupplier2](../../../extensibility/debugger/reference/idebugportsupplier2.md) Schnittstelle.

## <a name="notes-for-callers"></a>Hinweise für Aufrufer
 Rufen Sie [QueryInterface](/cpp/atl/queryinterface) auf die `IDebugPortSupplier2` Schnittstelle, um diese Schnittstelle zu erhalten.

## <a name="methods-in-vtable-order"></a>Methoden in Vtable-Reihenfolge
 Zusätzlich zu den von geerbten Methoden der [IDebugPortSupplier2](../../../extensibility/debugger/reference/idebugportsupplier2.md) Schnittstelle, die diese Schnittstelle unterstützt die folgenden:

|Methode|Beschreibung|
|------------|-----------------|
|[CanPersistPorts](../../../extensibility/debugger/reference/idebugportsupplier3-canpersistports.md)|Gibt zurück, ob die anschlusslieferant Ports gespeichert werden kann (indem sie auf den Datenträger geschrieben werden müssen) zwischen den Aufrufen des Debuggers.|
|[EnumPersistedPorts](../../../extensibility/debugger/reference/idebugportsupplier3-enumpersistedports.md)|Gibt ein Objekt, das verwendet werden kann zum Aufzählen über alle Ports, die auf den Datenträger geschrieben wurden, von diesem anschlusslieferant zurück.|

## <a name="remarks"></a>Hinweise
 Wenn ein portanbieters Ports über Aufrufe hinweg beibehalten kann, sollten sie diese Schnittstelle implementieren. Ports sollte geladen werden, wenn Anschlusslieferanten instanziiert ist, und wenn Anschlusslieferanten zerstört wird auf den Datenträger geschrieben.

 Eine Debug-Engine ist in der Regel interagiert nicht mit eines portanbieters und hat keine Verwendung für diese Schnittstelle.

## <a name="requirements"></a>Anforderungen
 Header: msdbg.h

 Namespace: Microsoft.VisualStudio.Debugger.Interop

 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Siehe auch
- [Wichtige Schnittstellen](../../../extensibility/debugger/reference/core-interfaces.md)
- [IDebugPortSupplier2](../../../extensibility/debugger/reference/idebugportsupplier2.md)