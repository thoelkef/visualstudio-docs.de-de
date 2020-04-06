---
title: IEnumDebugPrograms2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IEnumDebugPrograms2
helpviewer_keywords:
- IEnumDebugPrograms2
ms.assetid: 7fbb8fb7-db64-4546-a364-dc668430c8af
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 1717397d9ff073642c7b6bc25ad85babe76d684c
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/06/2020
ms.locfileid: "80715571"
---
# <a name="ienumdebugprograms2"></a>IEnumDebugPrograms2
Diese Schnittstelle zählt die Programme auf, die in der aktuellen Debugsitzung ausgeführt werden.

## <a name="syntax"></a>Syntax

```
IEnumDebugPrograms2 : IUnknown
```

## <a name="notes-for-implementers"></a>Hinweise für Implementierer
 Das Debugmodul (DE) implementiert diese Schnittstelle, um eine Liste der Programme bereitzustellen, die von der DE gedebuggen werden.

## <a name="notes-for-callers"></a>Hinweise für Anrufer
 Visual Studio ruft [EnumPrograms](../../../extensibility/debugger/reference/idebugprocess2-enumprograms.md) auf, um diese Schnittstelle abzuerhalten. [EnumPrograms](../../../extensibility/debugger/reference/idebugengine2-enumprograms.md) wird von Visual Studio nicht verwendet.

## <a name="methods-in-vtable-order"></a>Methoden in Vtable-Reihenfolge
 Die folgende Tabelle zeigt `IEnumDebugPrograms2`die Methoden von .

|Methode|BESCHREIBUNG|
|------------|-----------------|
|[Weiter](../../../extensibility/debugger/reference/ienumdebugprograms2-next.md)|Ruft eine angegebene Anzahl von Programmen in einer Enumerationssequenz ab.|
|[Überspringen](../../../extensibility/debugger/reference/ienumdebugprograms2-skip.md)|Überspringt eine angegebene Anzahl von Programmen in einer Enumerationssequenz.|
|[Zurücksetzen](../../../extensibility/debugger/reference/ienumdebugprograms2-reset.md)|Setzt eine Enumerationsfolge auf den Anfang zurück.|
|[Klon](../../../extensibility/debugger/reference/ienumdebugprograms2-clone.md)|Erstellt einen Enumerator, der denselben Enumerationsstatus wie der aktuelle Enumerator enthält.|
|[GetCount](../../../extensibility/debugger/reference/ienumdebugprograms2-getcount.md)|Ruft die Anzahl der Programme in einem Enumerator ab.|

## <a name="remarks"></a>Bemerkungen
 Visual Studio verwendet diese Schnittstelle, um:

- Füllen Sie das **Fenster Modules** (durch Aufrufen von [EnumPrograms](../../../extensibility/debugger/reference/idebugprocess2-enumprograms.md) und anschließendes Aufrufen von [EnumModules](../../../extensibility/debugger/reference/idebugprogram2-enummodules.md) für jedes Programm).

- Füllen Sie die Liste An Prozess `IDebugProcess2::EnumPrograms` **anfügen** (durch Aufrufen und Aufrufen von [QueryInterface](/cpp/atl/queryinterface) auf jeder [IDebugProgram2-Schnittstelle,](../../../extensibility/debugger/reference/idebugprogram2.md) um eine [IDebugEngineProgram2-Schnittstelle](../../../extensibility/debugger/reference/idebugengineprogram2.md) zu erhalten).

- Generieren Sie eine Liste von DEs, die jedes Programm im Prozess debuggen können (mit [GetEngineInfo](../../../extensibility/debugger/reference/idebugprogram2-getengineinfo.md)).

- Wenden Sie Edit- und Continue-Updates (ENC)-Aktualisierungen auf jedes Programm an (durch Aufrufen von IDebugProcess2::EnumPrograms und dann Aufrufen von [GetENCUpdate](../../../extensibility/debugger/reference/idebugprogram2-getencupdate.md)).

## <a name="requirements"></a>Requirements (Anforderungen)
 Kopfzeile: msdbg.h

 Namespace: Microsoft.VisualStudio.Debugger.Interop

 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Weitere Informationen
- [Wichtige Schnittstellen](../../../extensibility/debugger/reference/core-interfaces.md)
- [EnumPrograms](../../../extensibility/debugger/reference/idebugengine2-enumprograms.md)
- [EnumPrograms](../../../extensibility/debugger/reference/idebugprocess2-enumprograms.md)
