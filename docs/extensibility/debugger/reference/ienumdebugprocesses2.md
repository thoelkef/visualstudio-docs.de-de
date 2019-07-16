---
title: IEnumDebugProcesses2 | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IEnumDebugProcesses2
helpviewer_keywords:
- IEnumDebugProcesses2
ms.assetid: 06a1368f-10f0-44eb-af61-e388c2327111
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 0b32d2469c42931fa3dead4c5078e7d5b44b5d60
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/29/2019
ms.locfileid: "66334934"
---
# <a name="ienumdebugprocesses2"></a>IEnumDebugProcesses2
Diese Schnittstelle Listet die Prozesse, die auf ein Debugport ausgeführt wird.

## <a name="syntax"></a>Syntax

```
IEnumDebugProcesses : IUnknown
```

## <a name="notes-for-implementers"></a>Hinweise für Implementierer
 Ein benutzerdefinierten Port Lieferanten implementiert diese Schnittstelle, um eine Liste der Prozesse, die an einen Port angeben.

## <a name="notes-for-callers"></a>Hinweise für Aufrufer
 Visual Studio-Aufrufe [EnumProcesses](../../../extensibility/debugger/reference/idebugport2-enumprocesses.md) dieser Schnittstelle abgerufen.

## <a name="methods-in-vtable-order"></a>Methoden in Vtable-Reihenfolge
 Die folgende Tabelle zeigt die Methoden der `IEnumDebugProcesses2`.

|Methode|Beschreibung|
|------------|-----------------|
|[Nächste](../../../extensibility/debugger/reference/ienumdebugprocesses2-next.md)|Ruft eine angegebene Anzahl von Prozessen in einer Enumerationsfolge ab.|
|[Skip](../../../extensibility/debugger/reference/ienumdebugprocesses2-skip.md)|Überspringt eine angegebene Anzahl von Prozessen in einer Enumerationsfolge.|
|[Reset](../../../extensibility/debugger/reference/ienumdebugprocesses2-reset.md)|Setzt eine Enumerationsfolge auf den Anfang zurück.|
|[Clone](../../../extensibility/debugger/reference/ienumdebugprocesses2-clone.md)|Erstellt einen Enumerator, der den gleichen Enumerationszustand wie der aktuelle Enumerator enthält.|
|[GetCount](../../../extensibility/debugger/reference/ienumdebugprocesses2-getcount.md)|Ruft die Anzahl von Prozessen in einen Enumerator ab.|

## <a name="remarks"></a>Hinweise
 Visual Studio verwendet diese Schnittstelle zum Ausfüllen der **Prozesse** Fenster.

## <a name="requirements"></a>Anforderungen
 Header: msdbg.h

 Namespace: Microsoft.VisualStudio.Debugger.Interop

 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Siehe auch
- [Wichtige Schnittstellen](../../../extensibility/debugger/reference/core-interfaces.md)
- [EnumProcesses](../../../extensibility/debugger/reference/idebugport2-enumprocesses.md)