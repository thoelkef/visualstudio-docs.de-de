---
title: "Steuerung der Ausführung | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: debugging [Debugging SDK], control of execution
ms.assetid: 97071846-007e-450f-95a6-f072d0f5e61e
caps.latest.revision: "9"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 79d888e9b50d18b4a9d46a8914381db27f09698d
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/31/2017
---
# <a name="control-of-execution"></a>Steuerung der Ausführung
Die Debugging-Modul (DE) sendet eines der folgenden Ereignisse in der Regel als letzte Startup-Ereignis:  
  
-   Das punktereignis Eintrag, wenn Anfügen an ein Programm neu gestartet  
  
-   Die Last ausgelöste Ereignis, wenn ein Programm zuordnen, die bereits ausgeführt wird  
  
 Diese beiden Ereignisse sind Beendigungen von Ereignissen, was bedeutet, dass die DE auf eine Antwort des Benutzers mithilfe der IDE wartet. Weitere Informationen finden Sie unter [Betriebsmodi](../../extensibility/debugger/operational-modes.md).  
  
## <a name="stopping-event"></a>Beenden-Ereignis  
 Wenn eine Stopping-Ereignis an die Debugsitzung gesendet wird:  
  
1.  Das Programm und der Thread, der den aktuellen Anweisungszeiger enthalten, können von Ereignisschnittstelle abgerufen werden.  
  
2.  Die IDE stellt fest, die aktuelle Quellcodedatei und die Position zeigt im Editor hervorgehoben.  
  
3.  Die Debugsitzung zu diesem ersten Stopping-Ereignis in der Regel durch Aufrufen des Programms reagiert **Fortfahren** Methode.  
  
4.  Das Programm wird dann ausgeführt, bis er erkennt, dass eine beenden-Bedingung, z. B. Erreichens einen Haltepunkt, in dem Fall DE die Debugsitzung ein Haltepunktereignis sendet. Das Haltepunktereignis ist eine Stopping-Ereignis und die DE wartet eine Benutzerantwort erneut.  
  
5.  Wenn der Benutzer entscheidet, die über einen Einzelschritt in, oder aus einer Funktion, die IDE, der Debugsitzung, rufen Sie des Programms `Step` -Methode, und übergeben sie die Einheit der Schritt (Instruction, Anweisung oder Zeile) und die Art der Schritt – d. h., ob mehr als einen Einzelschritt in, , oder aus der Funktion. Wenn der Schritt abgeschlossen ist, sendet der DE ein Schritt ausgelöste Ereignis an die Debugsitzung, also eine Stopping-Ereignis.  
  
     - oder -   
  
     Wenn der Benutzer wählt fortgesetzt werden von den aktuellen Anweisungszeiger, fordert die IDE die Debugsitzung, rufen Sie des Programms **Execute** Methode. Das Programm setzt die Ausführung fort, bis die nächste beenden-Bedingung erreicht.  
  
     - oder -   
  
     Wenn die Debugsitzung ist, um einen bestimmten Stopping-Ereignis zu ignorieren, ruft die Debugsitzung des Programms **Fortfahren** Methode. Wenn das Programm ausführen in Einzelschritten wurde ausführen, überspringen oder aus einer Funktion, wenn die beenden-Bedingung gefunden wurden, stellt dann den Schritt.  
  
 Programmgesteuert, wenn die DE eine beenden-Bedingung auftritt, sendet er beenden Ereignisse wie [IDebugLoadCompleteEvent2](../../extensibility/debugger/reference/idebugloadcompleteevent2.md) oder [IDebugEntryPointEvent2](../../extensibility/debugger/reference/idebugentrypointevent2.md) Sitzung Debug-Manager (SDM) mithilfe von ein [IDebugEventCallback2](../../extensibility/debugger/reference/idebugeventcallback2.md) Schnittstelle. Der DE übergibt die [IDebugProgram2](../../extensibility/debugger/reference/idebugprogram2.md) und [IDebugThread2](../../extensibility/debugger/reference/idebugthread2.md) Schnittstellen, die das Programm sowie den Thread an, die den aktuellen Anweisungszeiger enthält darstellen. Ruft die SDM [IDebugThread2::EnumFrameInfo](../../extensibility/debugger/reference/idebugthread2-enumframeinfo.md) zum Abrufen der obersten Stapelrahmen und Aufrufe [IDebugStackFrame2::GetDocumentContext](../../extensibility/debugger/reference/idebugstackframe2-getdocumentcontext.md) zum Abrufen der aktuellen Anweisung zugeordneten Dokument Kontexts Zeiger. Dieses Dokumentenkontext ist in der Regel eine Quelle Code Name, Zeile und Spalte Dateinummer. Die IDE verwendet diese, um den Quellcode hervorheben, der den aktuellen Anweisungszeiger enthält.  
  
 Die SDM zu diesem ersten Stopping-Ereignis in der Regel durch Aufrufen reagiert [IDebugProgram2::Continue](../../extensibility/debugger/reference/idebugprogram2-continue.md). Das Programm dann ausgeführt wird, bis er erkennt, dass eine beenden-Bedingung, z. B. Erreichens einen Haltepunkt, in dem Fall DE sendet eine [IDebugBreakpointEvent2 Schnittstelle](../../extensibility/debugger/reference/idebugbreakpointevent2.md) , das SDM. Das Haltepunktereignis ist eine Stopping-Ereignis und die DE wartet eine Benutzerantwort erneut.  
  
 Wenn der Benutzer entscheidet, die über einen Einzelschritt in, oder aus einer Funktion, die IDE, das SDM Aufrufen [IDebugProgram2::Step](../../extensibility/debugger/reference/idebugprogram2-step.md), und übergeben sie die [STEPUNIT](../../extensibility/debugger/reference/stepunit.md) (Instruction, Anweisung oder Zeile) und die [ STEPKIND](../../extensibility/debugger/reference/stepkind.md), d. h., ob Schritt ausführen, überspringen oder aus der Funktion. Wenn der Schritt abgeschlossen ist, sendet der DE ein [IDebugStepCompleteEvent2](../../extensibility/debugger/reference/idebugstepcompleteevent2.md) Schnittstelle, um die SDM, also eine Stopping-Ereignis.  
  
 Wenn der Benutzer wählt fortgesetzt werden von den aktuellen Anweisungszeiger, fordert die IDE die SDM Aufrufen [IDebugProgram2::Execute](../../extensibility/debugger/reference/idebugprogram2-execute.md). Das Programm setzt die Ausführung fort, bis die nächste beenden-Bedingung erreicht.  
  
 Wenn das debugpaket ist, um einen bestimmten Stopping-Ereignis zu ignorieren, ruft das debugpaket der SDM, der aufgerufen wird, [IDebugProgram2::Continue](../../extensibility/debugger/reference/idebugprogram2-continue.md). Wenn das Programm ausführen in Einzelschritten wurde ausführen, überspringen oder aus einer Funktion, wenn die beenden-Bedingung gefunden wurden, stellt dann den Schritt. Dies bedeutet, dass das Programm einen schrittweisen Zustand aufrechterhalten, damit er weiß, wie Sie den Vorgang fortzusetzen.  
  
 Die Aufrufe der SDM nimmt `Step`, **Execute**, und **Fortfahren** sind asynchron, was bedeutet, dass die SDM erwartet, dass den Aufruf schnell zurückgegeben. Wenn DE die SDM Stopping-Ereignis im selben Thread vor sendet `Step`, **Execute**, oder **Fortfahren** zurückgegeben wird, hängt von der SDM.  
  
## <a name="see-also"></a>Siehe auch  
 [Debuggingaufgaben](../../extensibility/debugger/debugging-tasks.md)