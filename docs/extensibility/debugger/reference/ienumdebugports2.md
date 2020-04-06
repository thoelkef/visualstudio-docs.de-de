---
title: IEnumDebugPorts2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IEnumDebugPorts2
helpviewer_keywords:
- IEnumDebugPorts2
ms.assetid: 1754eef3-cf62-42e0-b218-1911acba77d4
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: f3cc46ef8abb6ef1fbb8f072d97b0fc4a537af1a
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/06/2020
ms.locfileid: "80716105"
---
# <a name="ienumdebugports2"></a>IEnumDebugPorts2
Diese Schnittstelle zählt die Ports einer Maschine oder eines Portlieferanten auf.

## <a name="syntax"></a>Syntax

```
IEnumDebugPorts2 : IUnknown
```

## <a name="notes-for-implementers"></a>Hinweise für Implementierer
 Ein benutzerdefinierter Portlieferant implementiert diese Schnittstelle, um eine Liste der vom Lieferanten erstellten Ports darzustellen. Visual Studio implementiert diese Schnittstelle zur Unterstützung des eigenen Portanbieters.

## <a name="notes-for-callers"></a>Hinweise für Anrufer
 Rufen Sie [EnumPorts](../../../extensibility/debugger/reference/idebugportsupplier2-enumports.md) auf, um diese Schnittstelle abzurufen, die eine Liste der vom Portlieferanten erstellten Ports darstellt. Rufen Sie [EnumPersistedPorts](../../../extensibility/debugger/reference/idebugportsupplier3-enumpersistedports.md) auf, um diese Schnittstelle abzurufen, die eine Liste der Ports darstellt, die auf dem Datenträger gespeichert wurden.

## <a name="methods-in-vtable-order"></a>Methoden in Vtable-Reihenfolge
 Die folgende Tabelle zeigt `IEnumDebugPorts2`die Methoden von .

|Methode|BESCHREIBUNG|
|------------|-----------------|
|[Weiter](../../../extensibility/debugger/reference/ienumdebugports2-next.md)|Ruft eine angegebene Anzahl von Ports in einer Enumerationssequenz ab.|
|[Überspringen](../../../extensibility/debugger/reference/ienumdebugports2-skip.md)|Überspringt eine angegebene Anzahl von Ports in einer Enumerationssequenz.|
|[Zurücksetzen](../../../extensibility/debugger/reference/ienumdebugports2-reset.md)|Setzt eine Enumerationsfolge auf den Anfang zurück.|
|[Klon](../../../extensibility/debugger/reference/ienumdebugports2-clone.md)|Erstellt einen Enumerator, der denselben Enumerationsstatus wie der aktuelle Enumerator enthält.|
|[GetCount](../../../extensibility/debugger/reference/ienumdebugports2-getcount.md)|Ruft die Anzahl der Ports in einem Enumerator ab.|

## <a name="remarks"></a>Bemerkungen
 Visual Studio verwendet diese Schnittstelle, um eine Liste der Ports aufzufüllen, die zum Anfügen an Prozesse verwendet werden.

 Ein Debugmodul verwendet diese Schnittstelle in der Regel nicht.

## <a name="requirements"></a>Requirements (Anforderungen)
 Kopfzeile: msdbg.h

 Namespace: Microsoft.VisualStudio.Debugger.Interop

 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Weitere Informationen
- [Wichtige Schnittstellen](../../../extensibility/debugger/reference/core-interfaces.md)
- [EnumPorts](../../../extensibility/debugger/reference/idebugcoreserver2-enumports.md)
- [EnumPorts](../../../extensibility/debugger/reference/idebugportsupplier2-enumports.md)
