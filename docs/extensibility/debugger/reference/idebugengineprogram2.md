---
title: IDebugEngineProgram2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugEngineProgram2
helpviewer_keywords:
- IDebugEngineProgram2 interface
ms.assetid: 151003a9-2e4d-4acf-9f4d-365dfa6b9596
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 8e5ccf2327e660a983bcb3032363a92ac8a6f71d
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/06/2020
ms.locfileid: "80730298"
---
# <a name="idebugengineprogram2"></a>IDebugEngineProgram2
Diese Schnittstelle bietet Multithread-Debugunterstützung.

## <a name="syntax"></a>Syntax

```
IDebugEngineProgram2 : IUnknown
```

## <a name="notes-for-implementers"></a>Hinweise für Implementierer
 Ein Debugmodul implementiert diese Schnittstelle, um das gleichzeitige Debuggen mehrerer Threads zu unterstützen. Diese Schnittstelle wird für dasselbe Objekt implementiert, das die [IDebugProgram2-Schnittstelle](../../../extensibility/debugger/reference/idebugprogram2.md) implementiert.

## <a name="notes-for-callers"></a>Hinweise für Anrufer
 Verwenden Sie [QueryInterface,](/cpp/atl/queryinterface) um `IDebugProgram2` diese Schnittstelle von einer Schnittstelle abzufragen.

## <a name="methods-in-vtable-order"></a>Methoden in Vtable-Reihenfolge
 Die folgende Tabelle zeigt `IDebugEngineProgram2`die Methoden von .

|Methode|BESCHREIBUNG|
|------------|-----------------|
|[Beenden](../../../extensibility/debugger/reference/idebugengineprogram2-stop.md)|Beendet alle Threads, die in diesem Programm ausgeführt werden.|
|[WatchForThreadStep](../../../extensibility/debugger/reference/idebugengineprogram2-watchforthreadstep.md)|Uhren für die Ausführung (oder beenden Sie die Beobachtung für die Ausführung), die auf dem angegebenen Thread auftreten.|
|[WatchForExpressionEvaluationOnThread](../../../extensibility/debugger/reference/idebugengineprogram2-watchforexpressionevaluationonthread.md)|Ermöglicht die Auswerteung (oder Nichtzuleinerung) von Ausdrücken für den angegebenen Thread, auch wenn das Programm angehalten wird.|

## <a name="remarks"></a>Bemerkungen
 Visual Studio ruft diese Schnittstelle als Reaktion auf ein [IDebugProgramCreateEvent2-Ereignis](../../../extensibility/debugger/reference/idebugprogramcreateevent2.md) auf und setzt die Zustände "Watch for Thread Step" und "Watch for Expression Evaluation on Thread" des Programms fest. [Stop](../../../extensibility/debugger/reference/idebugengineprogram2-stop.md) wird aufgerufen, wenn das Programm beendet werden soll; Diese Methode gibt dem Programm die Möglichkeit, alle Threads zu beenden.

## <a name="requirements"></a>Requirements (Anforderungen)
 Kopfzeile: msdbg.h

 Namespace: Microsoft.VisualStudio.Debugger.Interop

 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Weitere Informationen
- [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)
