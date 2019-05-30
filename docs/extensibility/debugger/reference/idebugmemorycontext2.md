---
title: IDebugMemoryContext2 | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugMemoryContext2
helpviewer_keywords:
- IDebugMemoryContext2 interface
ms.assetid: 3a544c8b-11dc-46bb-8549-261e4ac5bbc4
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: bb1abe29a915d8ca2aaba1135d2e57946250bc3f
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/29/2019
ms.locfileid: "66346972"
---
# <a name="idebugmemorycontext2"></a>IDebugMemoryContext2
Diese Schnittstelle stellt eine Position im Adressraum des Computers, die zu debuggende Programm wird ausgeführt.

## <a name="syntax"></a>Syntax

```
IDebugMemoryContext2 : IUnknown
```

## <a name="notes-for-implementers"></a>Hinweise für Implementierer
 Die Debug-Engine (DE) implementiert diese Schnittstelle, um eine Adresse im Speicher darstellen.

## <a name="notes-for-callers"></a>Hinweise für Aufrufer
 Ein Aufruf von [GetMemoryContext](../../../extensibility/debugger/reference/idebugproperty2-getmemorycontext.md) oder [GetMemoryContext](../../../extensibility/debugger/reference/idebugreference2-getmemorycontext.md) dieser Schnittstelle zurück. Außerdem Aufrufe von [hinzufügen](../../../extensibility/debugger/reference/idebugmemorycontext2-add.md) und [Subtract](../../../extensibility/debugger/reference/idebugmemorycontext2-subtract.md) neue Kopien dieser Schnittstelle zurück, nachdem die entsprechenden arithmetische Operation angewendet wurde.

## <a name="methods-in-vtable-order"></a>Methoden in Vtable-Reihenfolge
 Die folgende Tabelle zeigt die Methoden der `IDebugMemoryContext2`.

|Methode|Beschreibung|
|------------|-----------------|
|[GetName](../../../extensibility/debugger/reference/idebugmemorycontext2-getname.md)|Ruft den Benutzer angezeigten Namen für diesen Kontext ab.|
|[GetInfo](../../../extensibility/debugger/reference/idebugmemorycontext2-getinfo.md)|Ruft die Informationen, die diesem Kontext zu beschreiben.|
|[Add](../../../extensibility/debugger/reference/idebugmemorycontext2-add.md)|Fügt einen angegebenen Wert auf dem aktuellen Kontext-Adresse, die ein neuer Kontext erstellt.|
|[Subtrahieren](../../../extensibility/debugger/reference/idebugmemorycontext2-subtract.md)|Subtrahiert einen angegebenen Wert aus dem aktuellen Kontext-Adresse, ein neuer Kontext erstellt.|
|[Compare](../../../extensibility/debugger/reference/idebugmemorycontext2-compare.md)|Vergleicht zwei Kontexten wie angegeben Vergleichsflags.|

## <a name="remarks"></a>Hinweise
 Visual Studio **Arbeitsspeicher** Fenster Aufrufe [GetMemoryContext](../../../extensibility/debugger/reference/idebugproperty2-getmemorycontext.md) zum Abrufen der `IDebugMemoryContext2` -Schnittstelle, den ausgewerteten Ausdruck für die Speicheradresse enthält. Dieser Kontext wird dann an übergeben [ReadAt](../../../extensibility/debugger/reference/idebugmemorybytes2-readat.md) und [WriteAt](../../../extensibility/debugger/reference/idebugmemorybytes2-writeat.md) an die Adresse für das Lesen und schreiben.

## <a name="requirements"></a>Anforderungen
 Header: msdbg.h

 Namespace: Microsoft.VisualStudio.Debugger.Interop

 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Siehe auch
- [Wichtige Schnittstellen](../../../extensibility/debugger/reference/core-interfaces.md)
- [GetMemoryContext](../../../extensibility/debugger/reference/idebugproperty2-getmemorycontext.md)
- [GetMemoryContext](../../../extensibility/debugger/reference/idebugreference2-getmemorycontext.md)
- [ReadAt](../../../extensibility/debugger/reference/idebugmemorybytes2-readat.md)
- [WriteAt](../../../extensibility/debugger/reference/idebugmemorybytes2-writeat.md)