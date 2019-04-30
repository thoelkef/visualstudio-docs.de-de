---
title: IDebugEngineProgram2 | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugEngineProgram2
helpviewer_keywords:
- IDebugEngineProgram2 interface
ms.assetid: 151003a9-2e4d-4acf-9f4d-365dfa6b9596
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: dcf84711b6f87d055bb37f47c259306fb55e0f77
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62875172"
---
# <a name="idebugengineprogram2"></a>IDebugEngineProgram2
Diese Schnittstelle stellt Multithread-debugging-Unterstützung bereit.

## <a name="syntax"></a>Syntax

```
IDebugEngineProgram2 : IUnknown
```

## <a name="notes-for-implementers"></a>Hinweise für Implementierer
 Ein Debugmodul implementiert diese Schnittstelle, um das gleichzeitige Debuggen von mehreren Threads unterstützen. Diese Schnittstelle wird implementiert, für das gleiche Objekt, das implementiert die [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md) Schnittstelle.

## <a name="notes-for-callers"></a>Hinweise für Aufrufer
 Verwendung [QueryInterface](/cpp/atl/queryinterface) dieser Schnittstelle vom Abrufen einer `IDebugProgram2` Schnittstelle.

## <a name="methods-in-vtable-order"></a>Methoden in Vtable-Reihenfolge
 Die folgende Tabelle zeigt die Methoden der `IDebugEngineProgram2`.

|Methode|Beschreibung|
|------------|-----------------|
|[Stop](../../../extensibility/debugger/reference/idebugengineprogram2-stop.md)|Beendet alle Threads, die in diesem Programm ausgeführt wird.|
|[WatchForThreadStep](../../../extensibility/debugger/reference/idebugengineprogram2-watchforthreadstep.md)|Wird überwacht, ob die Ausführung (oder beenden, die für die Ausführung überwachen) an den angegebenen Thread ausgeführt.|
|[WatchForExpressionEvaluationOnThread](../../../extensibility/debugger/reference/idebugengineprogram2-watchforexpressionevaluationonthread.md)|Auswertung von Ausdrücken für den angegebenen Thread ausgeführt wird, auch wenn das Programm beendet wird hiermit (oder verweigert).|

## <a name="remarks"></a>Hinweise
 Visual Studio ruft diese Schnittstelle als Reaktion auf eine [IDebugProgramCreateEvent2](../../../extensibility/debugger/reference/idebugprogramcreateevent2.md) Ereignis und die "Sehen Sie sich für die Thread-Step" und "Sehen Sie sich für Ausdruck Auswertung auf Thread" Status des Programms festlegen. [Beenden Sie](../../../extensibility/debugger/reference/idebugengineprogram2-stop.md) wird aufgerufen, wenn das Programm beendet werden, diese Methode gibt dem Programm die Möglichkeit, die alle Threads zu beenden.

## <a name="requirements"></a>Anforderungen
 Header: msdbg.h

 Namespace: Microsoft.VisualStudio.Debugger.Interop

 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Siehe auch
- [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)