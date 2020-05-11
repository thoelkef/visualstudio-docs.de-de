---
title: IDebugMemoryContext2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugMemoryContext2
helpviewer_keywords:
- IDebugMemoryContext2 interface
ms.assetid: 3a544c8b-11dc-46bb-8549-261e4ac5bbc4
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 7d20a1180e1162e7de3aee1c5d69facf8c193910
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/06/2020
ms.locfileid: "80727425"
---
# <a name="idebugmemorycontext2"></a>IDebugMemoryContext2
Diese Schnittstelle stellt eine Position im Adressraum des Computers dar, auf dem das zu debuggende Programm ausgeführt wird.

## <a name="syntax"></a>Syntax

```
IDebugMemoryContext2 : IUnknown
```

## <a name="notes-for-implementers"></a>Hinweise für Implementierer
 Das Debugmodul (DE) implementiert diese Schnittstelle, um eine Adresse im Arbeitsspeicher darzustellen.

## <a name="notes-for-callers"></a>Hinweise für Anrufer
 Ein Aufruf von [GetMemoryContext](../../../extensibility/debugger/reference/idebugproperty2-getmemorycontext.md) oder [GetMemoryContext](../../../extensibility/debugger/reference/idebugreference2-getmemorycontext.md) gibt diese Schnittstelle zurück. Außerdem geben Aufrufe von [Add](../../../extensibility/debugger/reference/idebugmemorycontext2-add.md) and [Subtract](../../../extensibility/debugger/reference/idebugmemorycontext2-subtract.md) neue Kopien dieser Schnittstelle zurück, nachdem die entsprechende arithmetische Operation angewendet wurde.

## <a name="methods-in-vtable-order"></a>Methoden in Vtable-Reihenfolge
 Die folgende Tabelle zeigt `IDebugMemoryContext2`die Methoden von .

|Methode|BESCHREIBUNG|
|------------|-----------------|
|[GetName](../../../extensibility/debugger/reference/idebugmemorycontext2-getname.md)|Ruft den vom Benutzer angezeigten Namen für diesen Kontext ab.|
|[GetInfo](../../../extensibility/debugger/reference/idebugmemorycontext2-getinfo.md)|Ruft Informationen ab, die diesen Kontext beschreiben.|
|[Hinzufügen](../../../extensibility/debugger/reference/idebugmemorycontext2-add.md)|Fügt der Adresse des aktuellen Kontexts einen angegebenen Wert hinzu, um einen neuen Kontext zu erstellen.|
|[Subtrahieren](../../../extensibility/debugger/reference/idebugmemorycontext2-subtract.md)|Subtrahiert einen angegebenen Wert von der Adresse des aktuellen Kontexts, um einen neuen Kontext zu erstellen.|
|[Vergleichen](../../../extensibility/debugger/reference/idebugmemorycontext2-compare.md)|Vergleicht zwei Kontexte in der Weise, die durch Vergleichsflags angegeben wird.|

## <a name="remarks"></a>Bemerkungen
 Das **Memory-Fenster** von Visual Studio ruft `IDebugMemoryContext2` [GetMemoryContext](../../../extensibility/debugger/reference/idebugproperty2-getmemorycontext.md) auf, um die Schnittstelle abzuerhalten, die den ausgewerteten Ausdruck enthält, der für die Speicheradresse verwendet wird. Dieser Kontext wird dann an [ReadAt](../../../extensibility/debugger/reference/idebugmemorybytes2-readat.md) und [WriteAt](../../../extensibility/debugger/reference/idebugmemorybytes2-writeat.md) übergeben, um die Adresse anzugeben, die gelesen oder geschrieben werden soll.

## <a name="requirements"></a>Requirements (Anforderungen)
 Kopfzeile: msdbg.h

 Namespace: Microsoft.VisualStudio.Debugger.Interop

 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Weitere Informationen
- [Wichtige Schnittstellen](../../../extensibility/debugger/reference/core-interfaces.md)
- [GetMemoryContext](../../../extensibility/debugger/reference/idebugproperty2-getmemorycontext.md)
- [GetMemoryContext](../../../extensibility/debugger/reference/idebugreference2-getmemorycontext.md)
- [ReadAt](../../../extensibility/debugger/reference/idebugmemorybytes2-readat.md)
- [WriteAt](../../../extensibility/debugger/reference/idebugmemorybytes2-writeat.md)
