---
title: IEnumDebugModules2 | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IEnumDebugModules2
helpviewer_keywords:
- IEnumDebugModules2
ms.assetid: 4fe28074-a960-41ad-b74d-b57f04c0c0ad
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 548bcd0328f7bdf52e47eb9a4295168ca47a2517
ms.sourcegitcommit: 6196d0b7fdcb08ba6d28a8151ad36b8d1139f2cc
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/07/2019
ms.locfileid: "65226701"
---
# <a name="ienumdebugmodules2"></a>IEnumDebugModules2
Diese Schnittstelle Listet eine Liste der Module an.

## <a name="syntax"></a>Syntax

```
IEnumDebugModules2 : IUnknown
```

## <a name="notes-for-implementers"></a>Hinweise für Implementierer
 Die Debug-Engine (DE) implementiert diese Schnittstelle, um eine Liste der für ein Programm geladenen Module darstellt.

## <a name="notes-for-callers"></a>Hinweise für Aufrufer
 Visual Studio-Aufrufe [EnumModules](../../../extensibility/debugger/reference/idebugprogram2-enummodules.md) dieser Schnittstelle abgerufen.

## <a name="methods-in-vtable-order"></a>Methoden in Vtable-Reihenfolge
 Die folgende Tabelle zeigt die Methoden der `IEnumDebugModules2`.

|Methode|Beschreibung|
|------------|-----------------|
|[Nächste](../../../extensibility/debugger/reference/ienumdebugmodules2-next.md)|Ruft eine angegebene Anzahl von Modulen in einer Enumerationsfolge ab.|
|[Skip](../../../extensibility/debugger/reference/ienumdebugmodules2-skip.md)|Überspringt eine angegebene Anzahl von Modulen in einer Enumerationsfolge.|
|[Reset](../../../extensibility/debugger/reference/ienumdebugmodules2-reset.md)|Setzt eine Enumerationsfolge auf den Anfang zurück.|
|[Clone](../../../extensibility/debugger/reference/ienumdebugmodules2-clone.md)|Erstellt einen Enumerator, der den gleichen Enumerationszustand wie der aktuelle Enumerator enthält.|
|[GetCount](../../../extensibility/debugger/reference/ienumdebugmodules2-getcount.md)|Ruft die Anzahl der Module ab.|

## <a name="remarks"></a>Hinweise
 Visual Studio verwendet diese Schnittstelle in erster Linie zum Aktualisieren der **Module** Fenster.

 Für die Zwecke des Debuggens in Visual Studio, ein Programm ist eine logische Sequenz von Code-Anweisungen, die modulgrenzen, daher überschreiten, können die Notwendigkeit, eine Liste von Modulen für eine einzelne [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md) Schnittstelle. Das erste Modul in der Liste enthält in der Regel den ersten Einstiegspunkt für das zugeordnete Programm.

## <a name="requirements"></a>Anforderungen
 Header: msdbg.h

 Namespace: Microsoft.VisualStudio.Debugger.Interop

 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Siehe auch
- [Wichtige Schnittstellen](../../../extensibility/debugger/reference/core-interfaces.md)
- [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)
- [EnumModules](../../../extensibility/debugger/reference/idebugprogram2-enummodules.md)