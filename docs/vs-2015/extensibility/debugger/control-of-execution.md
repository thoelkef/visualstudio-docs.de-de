---
title: Steuern der Ausführung | Microsoft-Dokumentation
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- debugging [Debugging SDK], control of execution
ms.assetid: 97071846-007e-450f-95a6-f072d0f5e61e
caps.latest.revision: 10
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 31584a0f59369def8a1a89ad2544b94ef9633366
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/12/2018
ms.locfileid: "49302379"
---
# <a name="control-of-execution"></a>Steuern der Ausführung
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Die Debug-Engine (DE) wird in der Regel eines der folgenden Ereignisse als das letzte Startup-Ereignis gesendet:  
  
-   Das punktereignis Eintrag, wenn Anfügen an einen neu gestarteten Programms  
  
-   Dem Load ausgelöste Ereignis, wenn ein Programm angefügt, die bereits ausgeführt wird  
  
 Diese beiden Ereignisse werden beendet, dies bedeutet, dass eine Antwort vom Benutzer über die IDE die DE wartet. Weitere Informationen finden Sie unter [Betriebsmodi](../../extensibility/debugger/operational-modes.md).  
  
## <a name="stopping-event"></a>Ereignis beenden  
 Wenn die Stopping-Ereignis an die Debug-Sitzung gesendet wird:  
  
1.  Das Programm und einen Thread, der den aktuellen Anweisungszeiger enthalten, können der Schnittstelle der abgerufen werden.  
  
2.  Die IDE stellt fest, die aktuelle Quellcodedatei und die Position, d. h. er zeigt im Editor hervorgehoben.  
  
3.  Die Debugsitzung zu diesem ersten Stopping-Ereignis in der Regel durch Aufrufen des Programms reagiert **Weiter** Methode.  
  
4.  Das Programm wird dann ausgeführt, bis eine beenden-Bedingung, wie z. B. das Erreichen eines Haltepunkts, in dem Fall die DE ein Haltepunktereignis sendet, wenn auf die Debugsitzung erreicht wird. Das Haltepunktereignis ist eine Beenden-Ereignis aus, und die DE erneut wartet auf eine Antwort des Benutzers.  
  
5.  Wenn der Benutzer wählt, mehr als Einzelschritt oder aus einer Funktion, die IDE die Debugsitzung zum Aufrufen des Programms fordert `Step` -Methode, und übergeben sie die Einheit der Schritt (-Anweisung, Anweisung oder Zeile) und die Art der Schritt – d. h. angibt, ob mehr als in Schritt , oder aus der Funktion. Wenn der Schritt abgeschlossen ist, sendet die DE ein vollständiges Schritt-Ereignis an die Debugsitzung, handelt es sich eine Beenden-Ereignis.  
  
     - oder -   
  
     Wenn der Benutzer wählt fortgesetzt werden von den aktuellen Anweisungszeiger, fordert die IDE die Debugsitzung zum Aufrufen des Programms **Execute** Methode. Das Programm wird die Ausführung fortgesetzt, bis die nächste beenden-Bedingung erreicht.  
  
     - oder -   
  
     Wenn die Debug-Sitzung eine bestimmte Stopping-Ereignis ignorieren soll, ruft die Debug-Sitzung des Programms **Weiter** Methode. Wenn das Programm ausführen in Einzelschritten wurde in, überspringen oder aus einer Funktion, wenn sie die beenden-Bedingung aufgetreten, weiterhin klicken Sie dann den Schritt.  
  
 Programmgesteuert, wenn die DE eine beenden-Bedingung auftritt, sendet er beendet Ereignisse wie [IDebugLoadCompleteEvent2](../../extensibility/debugger/reference/idebugloadcompleteevent2.md) oder [IDebugEntryPointEvent2](../../extensibility/debugger/reference/idebugentrypointevent2.md) für die Sitzung-Debug-Manager (SDM) mithilfe von ein [IDebugEventCallback2](../../extensibility/debugger/reference/idebugeventcallback2.md) Schnittstelle. Der DE übergibt die [IDebugProgram2](../../extensibility/debugger/reference/idebugprogram2.md) und [IDebugThread2](../../extensibility/debugger/reference/idebugthread2.md) Schnittstellen, die die Anwendung und der Thread, der mit den aktuellen Anweisungszeiger darstellen. Die SDM-Aufrufe [IDebugThread2::EnumFrameInfo](../../extensibility/debugger/reference/idebugthread2-enumframeinfo.md) zum Abrufen der Top Stapelrahmen und Aufrufe [IDebugStackFrame2::GetDocumentContext](../../extensibility/debugger/reference/idebugstackframe2-getdocumentcontext.md) zum Abrufen der aktuellen Anweisung zugeordneten Dokumentkontext Zeiger. Diese Dokumentenkontext ist in der Regel eine Source Code Name, Zeile und Spalte Dateinummer. Die IDE verwendet diese, um Quellcode hervorzuheben, der den aktuellen Anweisungszeiger enthält.  
  
 Das SDM reagiert in der Regel auf diese ersten Stopping-Ereignis durch Aufruf [IDebugProgram2::Continue](../../extensibility/debugger/reference/idebugprogram2-continue.md). Das Programm dann ausgeführt wird, bis es eine beenden-Bedingung trifft, wie z. B. das Erreichen eines Haltepunkts, in dem Fall der DE sendet eine [IDebugBreakpointEvent2 Schnittstelle](../../extensibility/debugger/reference/idebugbreakpointevent2.md) , das SDM. Das Haltepunktereignis ist eine Beenden-Ereignis aus, und die DE erneut wartet auf eine Antwort des Benutzers.  
  
 Wenn der Benutzer wählt, mehr als Einzelschritt oder aus einer Funktion, die IDE werden, das SDM aufgefordert Aufrufen [IDebugProgram2::Step](../../extensibility/debugger/reference/idebugprogram2-step.md), und übergeben sie die [STEPUNIT](../../extensibility/debugger/reference/stepunit.md) (-Anweisung, Anweisung oder Zeile) und die [ STEPKIND](../../extensibility/debugger/reference/stepkind.md), d. h., ob in, überspringen oder aus der Funktion schrittweise. Wenn der Schritt abgeschlossen ist, sendet der DE eine [IDebugStepCompleteEvent2](../../extensibility/debugger/reference/idebugstepcompleteevent2.md) Schnittstelle, das SDM, handelt es sich eine Beenden-Ereignis.  
  
 Wenn der Benutzer wählt fortgesetzt werden von den aktuellen Anweisungszeiger, fragt die IDE das SDM Aufrufen [IDebugProgram2::Execute](../../extensibility/debugger/reference/idebugprogram2-execute.md). Das Programm wird die Ausführung fortgesetzt, bis die nächste beenden-Bedingung erreicht.  
  
 Wenn das debugpaket einer bestimmten Stopping-Ereignis ignorieren soll, ruft das debugpaket das SDM, die aufruft [IDebugProgram2::Continue](../../extensibility/debugger/reference/idebugprogram2-continue.md). Wenn das Programm ausführen in Einzelschritten wurde in, überspringen oder aus einer Funktion, wenn sie die beenden-Bedingung aufgetreten, weiterhin klicken Sie dann den Schritt. Dies bedeutet, dass das Programm einen schrittweisen Status verwaltet, damit es weiß, wie der Vorgang fortgesetzt wird.  
  
 Ruft die das SDM stellt `Step`, **Execute**, und **Weiter** sind asynchron, das bedeutet, dass das SDM erwartet, den Aufruf dass von schnell zurückgegeben. Wenn die DE dem SDM Stopping-Ereignis auf dem gleichen Thread vor dem sendet `Step`, **ausführen**, oder **Weiter** zurückgibt, das SDM reagiert.  
  
## <a name="see-also"></a>Siehe auch  
 [Debuggingaufgaben](../../extensibility/debugger/debugging-tasks.md)

