---
title: IEnumDebugProcesses2 | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IEnumDebugProcesses2
helpviewer_keywords:
- IEnumDebugProcesses2
ms.assetid: 06a1368f-10f0-44eb-af61-e388c2327111
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 8b9fe0e96ade081e8da11b5e1c06c5b45279b10b
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "80715757"
---
# <a name="ienumdebugprocesses2"></a>IEnumDebugProcesses2
Diese Schnittstelle listet die Prozesse auf, die auf einem Debugport ausgeführt werden.

## <a name="syntax"></a>Syntax

```
IEnumDebugProcesses : IUnknown
```

## <a name="notes-for-implementers"></a>Hinweise für Implementierer
 Ein benutzerdefinierter Port Lieferant implementiert diese Schnittstelle, um eine Liste der Prozesse bereitzustellen, die auf einem Port ausgeführt werden.

## <a name="notes-for-callers"></a>Hinweise für Aufrufer
 Visual Studio ruft [EnumProcesses](../../../extensibility/debugger/reference/idebugport2-enumprocesses.md) auf, um diese Schnittstelle zu erhalten.

## <a name="methods-in-vtable-order"></a>Methoden in Vtable-Reihenfolge
 In der folgenden Tabelle sind die Methoden von aufgeführt `IEnumDebugProcesses2` .

|Methode|BESCHREIBUNG|
|------------|-----------------|
|[Nächste](../../../extensibility/debugger/reference/ienumdebugprocesses2-next.md)|Ruft eine angegebene Anzahl von Prozessen in einer Enumerationsfolge ab.|
|[Skip](../../../extensibility/debugger/reference/ienumdebugprocesses2-skip.md)|Überspringt eine angegebene Anzahl von Prozessen in einer enumerationssequenz.|
|[Zurücksetzen](../../../extensibility/debugger/reference/ienumdebugprocesses2-reset.md)|Setzt eine Enumerationsfolge auf den Anfang zurück.|
|[Klonen](../../../extensibility/debugger/reference/ienumdebugprocesses2-clone.md)|Erstellt einen Enumerator, der den gleichen Enumerationszustand wie der aktuelle Enumerator enthält.|
|[GetCount](../../../extensibility/debugger/reference/ienumdebugprocesses2-getcount.md)|Ruft die Anzahl der Prozesse in einem Enumerator ab.|

## <a name="remarks"></a>Bemerkungen
 Visual Studio verwendet diese Schnittstelle, um das Fenster **Prozesse** aufzufüllen.

## <a name="requirements"></a>Anforderungen
 Header: msdbg. h

 Namespace: Microsoft. VisualStudio. Debugger. Interop

 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Weitere Informationen
- [Wichtige Schnittstellen](../../../extensibility/debugger/reference/core-interfaces.md)
- [EnumProcesses](../../../extensibility/debugger/reference/idebugport2-enumprocesses.md)
