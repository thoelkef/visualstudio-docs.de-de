---
title: "Steuerung der Ausf&#252;hrung | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Debuggen [Debuggen SDK], Steuerung der Ausführung"
ms.assetid: 97071846-007e-450f-95a6-f072d0f5e61e
caps.latest.revision: 9
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 9
---
# Steuerung der Ausf&#252;hrung
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Das Debugmodul \(DE\) sendet es sich in der Regel um eines der folgenden Ereignisse als letztes Ereignis starten:  
  
-   Mit dem Einstiegspunkt wird, um auf einen neu gestarteten Programm anhängen  
  
-   Das vollständige Ereignis beim Laden der mit einem Programm anfügen, der bereits ausgeführt wird  
  
 Beide diesen Ereignissen beenden und die Ereignisse bedeuten, dass DE auf eine Antwort vom Benutzer mithilfe der IDE wartet.  Weitere Informationen finden Sie unter [Betriebsweisen](../../extensibility/debugger/operational-modes.md).  
  
## Beenden von Ereignissen  
 Wenn ein aufhörendes Ereignis an die Debugsitzung gesendet wird:  
  
1.  Das Programm, und der Thread, in denen der aktuelle Anweisungszeiger enthalten, können von der Ereignisschnittstelle abgerufen werden.  
  
2.  Die IDE bestimmt die aktuelle Quelle Codedatei und der Position, an der sie im Editor markiert werden.  
  
3.  Die Debugsitzung reagiert in der Regel auf das erste aufhörende Ereignis, indem sie die **Weiter**\-Methode des Programms aufruft.  
  
4.  Das Programm wird ausgeführt, bis eine Bedingung aufhörende Informieren eines Haltepunkts auftritt, z. B. In diesem Fall wird ein Haltepunkt DE die Debugsitzung sendet.  Der Haltepunkt ist ein Klickereignis aufhörendes Ereignis, und wartet DE erneut auf eine Benutzerantwort.  
  
5.  Wenn der Benutzer wählt, um in oder aus über eine Funktion in Einzelschritten auszuführen, fordert übergibt die IDE die Debugsitzung auf, die `Step`\-Methode des Programms aufrufen und das Gerät des Schritts \(Anweisung, Anweisung oder Zeile\) und die Art der Schritt\-dass ist, ob in bzw. aus, um die Funktion erfolgt.  Wenn der Schritt abgeschlossen ist, sendet DE vollständiges Ereignis des Schritts auf die Debugsitzung, die ein aufhörendes Ereignis ist.  
  
     \- oder \-  
  
     Wenn der Benutzer wählt, um die Ausführung fortzusetzen, fordert vom aktuellen Anweisungszeiger die IDE die Debugsitzung auf, die **Ausführen**\-Methode des Programms aufzurufen.  Das Programm setzt die Ausführung fort, bis er die folgende aufhörende Bedingung findet.  
  
     \- oder \-  
  
     Wenn die Debugsitzung ein bestimmtes aufhörendes Ereignis ignorieren soll, ruft die Debugsitzung die **Weiter**\-Methode des Programms an.  Wenn das Programm an, über oder in einer Funktion aufgetreten, als es die aufhörende Bedingung gefunden hat, setzt er den Schritt fort.  
  
 Programmgesteuert, wenn eine Bedingung aufhörende DE auftritt, sendet es aufhörenden solche Ereignisse, die [IDebugLoadCompleteEvent2](../../extensibility/debugger/reference/idebugloadcompleteevent2.md) oder [IDebugEntryPointEvent2](../../extensibility/debugger/reference/idebugentrypointevent2.md) Debuggen auf den Manager der Sitzung \(SDM\) mittels einer [IDebugEventCallback2](../../extensibility/debugger/reference/idebugeventcallback2.md)\-Schnittstelle.  DE [IDebugProgram2](../../extensibility/debugger/reference/idebugprogram2.md) und führt die [IDebugThread2](../../extensibility/debugger/reference/idebugthread2.md)\-Schnittstellen, die das Programm und den Thread darstellt, die der aktuelle Anweisungszeiger enthalten.  Das SDM ruft [IDebugThread2::EnumFrameInfo](../../extensibility/debugger/reference/idebugthread2-enumframeinfo.md) auf, um den obersten Stapelrahmen abzurufen und ruft [IDebugStackFrame2::GetDocumentContext](../../extensibility/debugger/reference/idebugstackframe2-getdocumentcontext.md) auf, um den Dokumentenkontext abzurufen, der das aktuelle Anweisungszeiger zugeordnet ist.  Dieser Dokumentenkontext ist in der Regel ein Dateiname Quellcode, Zeilen\- und Spaltennummer. \-  Die IDE verwendet diese, um den Quellcode hervorheben, indem der aktuelle Anweisungszeiger enthält.  
  
 Das SDM reagiert in der Regel auf das erste aufhörende Ereignis, indem [IDebugProgram2::Fahren Sie fort](../../extensibility/debugger/reference/idebugprogram2-continue.md)aufruft.  Das Programm wird ausgeführt, bis eine Bedingung aufhörende Informieren eines Haltepunkts auftritt, z. B. In diesem Fall sendet. SDM dem [Schnittstelle IDebugBreakpointEvent2](../../extensibility/debugger/reference/idebugbreakpointevent2.md) DE  Der Haltepunkt ist ein Klickereignis aufhörendes Ereignis, und wartet DE erneut auf eine Benutzerantwort.  
  
 Wenn der Benutzer wählt, um in oder aus über eine Funktion in Einzelschritten auszuführen, fordert übergibt die IDE das SDM auf, [IDebugProgram2::Schritt](../../extensibility/debugger/reference/idebugprogram2-step.md)aufzurufen und es [STEPUNIT](../../extensibility/debugger/reference/stepunit.md)\-Anweisung \(oder Zeile\) und [STEPKIND](../../extensibility/debugger/reference/stepkind.md), d. h. ob die Funktion in oder aus.  Wenn der Schritt abgeschlossen ist, sendet eine DE [IDebugStepCompleteEvent2](../../extensibility/debugger/reference/idebugstepcompleteevent2.md)\-Schnittstelle zum aufhörendes SDM, das ein Ereignis ist.  
  
 Wenn der Benutzer wählt, um die Ausführung fortzusetzen, fordert vom aktuellen Anweisungszeiger die IDE das SDM, [IDebugProgram2::Ausführen](../../extensibility/debugger/reference/idebugprogram2-execute.md)aufzurufen.  Das Programm setzt die Ausführung fort, bis er die folgende aufhörende Bedingung findet.  
  
 Wenn das Debuggen ein bestimmtes Paket aufhörendes Ereignis ignorieren ist, ruft das Debuggen des Pakets SDM an, das [IDebugProgram2::Fahren Sie fort](../../extensibility/debugger/reference/idebugprogram2-continue.md)aufruft.  Wenn das Programm an, über oder in einer Funktion aufgetreten, als es die aufhörende Bedingung gefunden hat, setzt er den Schritt fort.  Dies bedeutet, dass das Programm einen tretenden Zustand beibehält, dass er fortgesetzt werden kann.  
  
 Die Aufrufe, die das SDM `Step`macht, **Ausführen**, und **Weiter** asynchron sind. Dies bedeutet, dass das SDM den Aufruf erwartet, schnell zu wechseln.  Wenn ein SDM das DE aufhörendes Ereignis für sendet, derselbe Thread vor `Step`, **Ausführen**, oder **Weiter** wird beendet, hängt das SDM.  
  
## Siehe auch  
 [Debugging\-Aufgaben](../../extensibility/debugger/debugging-tasks.md)