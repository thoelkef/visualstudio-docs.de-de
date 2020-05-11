---
title: IEnumDebugThreads2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IEnumDebugThreads2
helpviewer_keywords:
- IEnumDebugThreads2
ms.assetid: 1854f078-3b49-42c2-b65b-33e3b506fd63
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: bbbe047c08f8e91264163d028c1b40d94cde97fc
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/06/2020
ms.locfileid: "80715087"
---
# <a name="ienumdebugthreads2"></a>IEnumDebugThreads2
Diese Schnittstelle zählt die Threads auf, die in der aktuellen Debugsitzung ausgeführt werden.

## <a name="syntax"></a>Syntax

```
IEnumDebugThreads2 : IUnknown
```

## <a name="notes-for-implementers"></a>Hinweise für Implementierer
 Das Debugmodul (DE) implementiert diese Schnittstelle, um eine Liste von Threads in einem Programm darzustellen.

## <a name="notes-for-callers"></a>Hinweise für Anrufer
 Rufen Sie [EnumThreads](../../../extensibility/debugger/reference/idebugprocess2-enumthreads.md) auf, um diese Schnittstelle abzurufen, die eine Liste aller Threads in allen Programmen darstellt, die in einem Prozess ausgeführt werden. Rufen Sie [EnumThreads](../../../extensibility/debugger/reference/idebugprogram2-enumthreads.md) auf, um diese Schnittstelle abzurufen, die eine Liste der Threads darstellt, die in einem Programm ausgeführt werden.

## <a name="methods-in-vtable-order"></a>Methoden in Vtable-Reihenfolge
 Die folgende Tabelle zeigt `IEnumDebugThreads2`die Methoden von .

|Methode|BESCHREIBUNG|
|------------|-----------------|
|[Weiter](../../../extensibility/debugger/reference/ienumdebugthreads2-next.md)|Ruft eine angegebene Anzahl von Threads in der Enumerationssequenz ab.|
|[Überspringen](../../../extensibility/debugger/reference/ienumdebugthreads2-skip.md)|Überspringt eine angegebene Anzahl von Threads in einer Enumerationssequenz.|
|[Zurücksetzen](../../../extensibility/debugger/reference/ienumdebugthreads2-reset.md)|Setzt eine Enumerationsfolge auf den Anfang zurück.|
|[Klon](../../../extensibility/debugger/reference/ienumdebugthreads2-clone.md)|Erstellt einen Enumerator, der denselben Enumerationsstatus wie der aktuelle enthält.|
|[GetCount](../../../extensibility/debugger/reference/ienumdebugthreads2-getcount.md)|Ruft die Anzahl der Threads in einem Enumerator ab.|

## <a name="remarks"></a>Bemerkungen
 Visual Studio ruft diese Schnittstelle in der Regel ab, um das **Threads-Fenster** zu aktualisieren und den ersten Thread der Liste zu erhalten, um [Execute](../../../extensibility/debugger/reference/idebugprocess3-execute.md), [Continue](../../../extensibility/debugger/reference/idebugprocess3-continue.md)und [Step](../../../extensibility/debugger/reference/idebugprocess3-step.md)aufzurufen.

## <a name="requirements"></a>Requirements (Anforderungen)
 Kopfzeile: msdbg.h

 Namespace: Microsoft.VisualStudio.Debugger.Interop

 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Weitere Informationen
- [Wichtige Schnittstellen](../../../extensibility/debugger/reference/core-interfaces.md)
- [EnumThreads](../../../extensibility/debugger/reference/idebugprocess2-enumthreads.md)
- [EnumThreads](../../../extensibility/debugger/reference/idebugprogram2-enumthreads.md)
- [Schritt](../../../extensibility/debugger/reference/idebugprocess3-step.md)
- [Continue](../../../extensibility/debugger/reference/idebugprocess3-continue.md)
- [Ausführen](../../../extensibility/debugger/reference/idebugprocess3-execute.md)
