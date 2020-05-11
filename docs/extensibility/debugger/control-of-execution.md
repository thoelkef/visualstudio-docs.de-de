---
title: Kontrolle der Ausführung | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], control of execution
ms.assetid: 97071846-007e-450f-95a6-f072d0f5e61e
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: e2d338c5470611a5eea0c6279404c4eaddebb2d0
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/06/2020
ms.locfileid: "80739077"
---
# <a name="control-of-execution"></a>Kontrolle der Ausführung
Das Debugmodul (DE) sendet in der Regel eines der folgenden Ereignisse als letztes Startereignis:

- Das Einstiegspunktereignis, wenn es an ein neu gestartetes Programm angefügt wird

- Das Load Complete-Ereignis, wenn es an ein Programm angefügt wird, das bereits ausgeführt wird

  Beide Ereignisse beenden Ereignisse, was bedeutet, dass die DE auf eine Antwort des Benutzers über die IDE wartet. Weitere Informationen finden Sie unter [Betriebsmodi](../../extensibility/debugger/operational-modes.md).

## <a name="stopping-event"></a>Beenden des Ereignisses
 Wenn ein Beenden-Ereignis an die Debugsitzung gesendet wird:

1. Das Programm und der Thread, die den aktuellen Anweisungszeiger enthalten, können über die Ereignisschnittstelle abgerufen werden.

2. Die IDE bestimmt die aktuelle Quellcodedatei und -position, die sie wie im Editor hervorgehoben anzeigt.

3. Die Debugsitzung reagiert in der Regel auf dieses erste Stoppereignis, indem sie die **Continue-Methode** des Programms aufruft.

4. Das Programm wird dann ausgeführt, bis es auf eine Stoppbedingung stößt, z. B. auf einen Haltepunkt. In diesem Fall sendet die DE ein Haltepunktereignis an die Debugsitzung. Das Haltepunktereignis ist ein Stoppereignis, und die DE wartet erneut auf eine Benutzerantwort.

5. Wenn der Benutzer sich dafür entscheidet, in eine Funktion einzutreten, zu oder aus einer `Step` Funktion zu gehen, fordert die IDE die Debugsitzung auf, die Programmmethode aufzurufen. Die IDE übergibt dann die Schritteinheit (Anweisung, Anweisung oder Zeile) und den Typ des Schritts (ob in die Funktion einzutreten, zu überoder. Wenn der Schritt abgeschlossen ist, sendet die DE ein Step Complete-Ereignis an die Debugsitzung, die ein Beenden-Ereignis ist.

    - oder -

    Wenn der Benutzer die Ausführung vom aktuellen Anweisungszeiger aus fortsetzen möchte, fordert die IDE die Debugsitzung auf, die **Execute-Methode** des Programms aufzurufen. Das Programm setzt die Ausführung fort, bis die nächste Stoppbedingung erleidet.

    - oder -

    Wenn die Debugsitzung ein bestimmtes Stoppereignis ignorieren soll, ruft die Debugsitzung die **Continue-Methode** des Programms auf. Wenn das Programm in eine Funktion eintrat, über oder aus einer Funktion ging, als es auf die Stoppbedingung trat, setzt es den Schritt fort.

   Wenn die DE auf eine Stoppbedingung stößt, sendet sie programmatisch solche Stoppereignisse wie [IDebugLoadCompleteEvent2](../../extensibility/debugger/reference/idebugloadcompleteevent2.md) oder [IDebugEntryPointEvent2](../../extensibility/debugger/reference/idebugentrypointevent2.md) über eine [IDebugEventCallback2-Schnittstelle](../../extensibility/debugger/reference/idebugeventcallback2.md) an den Sitzungsdebug-Manager (SDM). Die DE übergibt die [Schnittstellen IDebugProgram2](../../extensibility/debugger/reference/idebugprogram2.md) und [IDebugThread2,](../../extensibility/debugger/reference/idebugthread2.md) die das Programm und den Thread darstellen, der den aktuellen Anweisungszeiger enthält. Das SDM ruft [IDebugThread2::EnumFrameInfo](../../extensibility/debugger/reference/idebugthread2-enumframeinfo.md) auf, um den obersten Stapelframe abzuruft, und ruft [IDebugStackFrame2::GetDocumentContext](../../extensibility/debugger/reference/idebugstackframe2-getdocumentcontext.md) auf, um den Dokumentkontext abzubekommen, der dem aktuellen Anweisungszeiger zugeordnet ist. Dieser Dokumentkontext ist in der Regel ein Quellcodedateiname, Zeilen- und Spaltennummer. Die IDE verwendet diese, um den Quellcode hervorzuheben, der den aktuellen Anweisungszeiger enthält.

   Das SDM reagiert in der Regel auf dieses erste Stoppereignis, indem [es IDebugProgram2::Continue](../../extensibility/debugger/reference/idebugprogram2-continue.md)aufruft. Das Programm wird dann ausgeführt, bis es auf eine Stoppbedingung trifft, z. B. auf einen Haltepunkt, in diesem Fall sendet die DE eine [IDebugBreakpointEvent2-Schnittstelle](../../extensibility/debugger/reference/idebugbreakpointevent2.md) an das SDM. Das Haltepunktereignis ist ein Stoppereignis, und die DE wartet erneut auf eine Benutzerantwort.

   Wenn der Benutzer sich dafür entscheidet, in eine Funktion einzutreten, zu oder aus einer Funktion zu gehen, fordert die IDE das SDM auf, [IDebugProgram2::Step](../../extensibility/debugger/reference/idebugprogram2-step.md)aufzurufen. Die IDE übergibt dann die [STEPUNIT](../../extensibility/debugger/reference/stepunit.md) (Anweisung, Anweisung oder Zeile) und die [STEPKIND](../../extensibility/debugger/reference/stepkind.md), d. h., ob sie in die Funktion einsteigen, überoder aus ihr treten soll. Wenn der Schritt abgeschlossen ist, sendet die DE eine [IDebugStepCompleteEvent2-Schnittstelle](../../extensibility/debugger/reference/idebugstepcompleteevent2.md) an das SDM, das ein Stoppereignis ist.

   Wenn der Benutzer die Ausführung vom aktuellen Anweisungszeiger aus fortsetzen möchte, fordert die IDE das SDM auf, [IDebugProgram2::Execute](../../extensibility/debugger/reference/idebugprogram2-execute.md)aufzurufen. Das Programm setzt die Ausführung fort, bis die nächste Stoppbedingung erleidet.

   Wenn das Debugpaket ein bestimmtes Stoppereignis ignorieren soll, ruft das Debugpaket das SDM auf, das [IDebugProgram2::Continue](../../extensibility/debugger/reference/idebugprogram2-continue.md)aufruft. Wenn das Programm in eine Funktion eintrat, über oder aus einer Funktion ging, als die Stoppbedingung aufgetreten ist, setzt es den Schritt fort. Dies impliziert, dass das Programm einen Schrittzustand beibehält, so dass es weiß, wie es weitergeht.

   Die Aufrufe des SDM an `Step`, **Execute**und **Continue** sind asynchron, was bedeutet, dass das SDM erwartet, dass der Aufruf schnell zurückgegeben wird. Wenn die DE dem SDM ein Stoppereignis `Step`für denselben Thread sendet, bevor , **Ausführen**oder **Weiter** zurückkehrt, hängt das SDM.

## <a name="see-also"></a>Weitere Informationen
- [Debug-Aufgaben](../../extensibility/debugger/debugging-tasks.md)
