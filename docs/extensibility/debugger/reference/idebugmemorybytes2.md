---
title: IDebugMemoryBytes2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugMemoryBytes2
helpviewer_keywords:
- IDebugMemoryBytes2 interface
ms.assetid: d7647575-0e06-4190-88f5-ca40b82209a4
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 56cb234e2295c5c9c08c2a2e9271e1c173524875
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/06/2020
ms.locfileid: "80727507"
---
# <a name="idebugmemorybytes2"></a>IDebugMemoryBytes2
Diese Schnittstelle stellt Datenbytes dar.

## <a name="syntax"></a>Syntax

```
IDebugMemoryBytes2 : IUnknown
```

## <a name="notes-for-implementers"></a>Hinweise für Implementierer
 Das Debugmodul (DE) implementiert diese Schnittstelle, um Bytes im Arbeitsspeicher darzustellen.

## <a name="notes-for-callers"></a>Hinweise für Anrufer
- [GetMemoryBytes](../../../extensibility/debugger/reference/idebugprogram2-getmemorybytes.md) gibt diese Schnittstelle zurück, um Zugriff auf den Systemspeicher zu ermöglichen. [GetMemoryBytes](../../../extensibility/debugger/reference/idebugproperty2-getmemorybytes.md) und [GetMemoryBytes](../../../extensibility/debugger/reference/idebugreference2-getmemorybytes.md) geben diese Schnittstelle zurück, um Zugriff auf die Bytes eines Objekts zu gewähren.

## <a name="methods-in-vtable-order"></a>Methoden in Vtable-Reihenfolge
 Die folgende Tabelle zeigt `IDebugMemoryBytes2`die Methoden von .

|Methode|BESCHREIBUNG|
|------------|-----------------|
|[ReadAt](../../../extensibility/debugger/reference/idebugmemorybytes2-readat.md)|Liest eine Folge von Bytes, beginnend an einem bestimmten Speicherort.|
|[WriteAt](../../../extensibility/debugger/reference/idebugmemorybytes2-writeat.md)|Schreibt `dwCount` Bytes, `pStartContext`beginnend bei .|
|[GetSize](../../../extensibility/debugger/reference/idebugmemorybytes2-getsize.md)|Ruft die Größe des Speichers, der von dieser Schnittstelle dargestellt wird, in Bytes ab.|

## <a name="remarks"></a>Bemerkungen
 Für Eigenschaften stellt eine [IDebugProperty2-Schnittstelle,](../../../extensibility/debugger/reference/idebugproperty2.md) die ein Array darstellt, eine `IDebugMemoryBytes2` Schnittstelle für den Zugriff auf die Werte in diesem Array bereit.

 Visual Studio es **Memory View** ruft [GetMemoryBytes](../../../extensibility/debugger/reference/idebugprogram2-getmemorybytes.md) auf, um eine `IDebugMemoryBytes2` Schnittstelle für den Zugriff auf den Systemspeicher abzurufen. Die Adresse, auf die zugegriffen werden soll, wird abgerufen, indem der als Adresse eingegebene Ausdruck `IDebugProperty2` in der Speicheransicht analysiert und dann der analysierte Ausdruck mithilfe von [EvaluateSync](../../../extensibility/debugger/reference/idebugexpression2-evaluatesync.md) ausgewertet wird, um eine Schnittstelle abrufbar zu machen. Ein Aufruf von [GetMemoryContext](../../../extensibility/debugger/reference/idebugproperty2-getmemorycontext.md) gibt den [IDebugMemoryContext2](../../../extensibility/debugger/reference/idebugmemorycontext2.md) zurück, der die Speicheradresse beschreibt. Dieser Speicherkontext wird dann an [ReadAt](../../../extensibility/debugger/reference/idebugmemorybytes2-readat.md) und [WriteAt](../../../extensibility/debugger/reference/idebugmemorybytes2-writeat.md)übergeben.

## <a name="requirements"></a>Requirements (Anforderungen)
 Kopfzeile: msdbg.h

 Namespace: Microsoft.VisualStudio.Debugger.Interop

 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Weitere Informationen
- [Wichtige Schnittstellen](../../../extensibility/debugger/reference/core-interfaces.md)
- [GetMemoryBytes](../../../extensibility/debugger/reference/idebugprogram2-getmemorybytes.md)
- [GetMemoryBytes](../../../extensibility/debugger/reference/idebugproperty2-getmemorybytes.md)
- [GetMemoryBytes](../../../extensibility/debugger/reference/idebugreference2-getmemorybytes.md)
- [IDebugMemoryContext2](../../../extensibility/debugger/reference/idebugmemorycontext2.md)
