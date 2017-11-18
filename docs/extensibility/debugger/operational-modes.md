---
title: Betriebsmodi | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: debug engines, modes
ms.assetid: f69972d0-809d-40df-9da3-04738791391c
caps.latest.revision: "13"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 205837bc5bfdf9476839ea1e54a53dc57dbf9a72
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/31/2017
---
# <a name="operational-modes"></a>Betriebsmodi
Es gibt drei Modi, die in denen IDE, wie folgt ausgeführt werden kann:  
  
-   [Entwurfsmodus](#vsconoperationalmodesanchor1)  
  
-   [Ausführmodus](#vsconoperationalmodesanchor2)  
  
-   [Unterbrechungsmodus](#vsconoperationalmodesanchor3)  
  
 Wie Ihre benutzerdefinierten Debugmodul (DE) zwischen diesen Modi übergeht, wird eine Entscheidung hinsichtlich der Implementierung, die Sie mit den Mechanismen Übergang vertraut sein muss. Die DE kann oder dieser Modi kann nicht direkt implementieren. Diese Modi sind eigentlich Paket Debugmodi, auf den wechseln basierend auf Handlung des Benutzers oder Ereignisse aus dem DE. Der Übergang vom ausführungs-in den Unterbrechungsmodus wird z. B. durch eine Stopping-Ereignis aus dem DE ausgelöst hat. Der Übergang von Break entweder oder Schritt Modus ausgeführt wird durch den Benutzer, die Vorgänge, z. B. Schritt oder Execute ausgelöst hat. Weitere Informationen zu DE Übergänge, finden Sie unter [Steuern der Ausführung von](../../extensibility/debugger/control-of-execution.md).  
  
##  <a name="vsconoperationalmodesanchor1"></a>Entwurfsmodus  
 Im Entwurfsmodus ist das nonrunning Zustand von Visual Studio debuggen, während dieses, den Zeitraums Debugfunktionen in Ihrer Anwendung festlegen können.  
  
 Nur wenige Debuggen Features verwendet werden, während der Entwurfsmodus zu wechseln. Entwickler können Haltepunkte setzen noch Überwachungsfenster Ausdrücke erstellen. Die DE ist nie geladen oder aufgerufen, während die IDE im Entwurfsmodus befindet. Interaktion mit der DE findet während der Ausführung und Seitenumbruch-Modi.  
  
##  <a name="vsconoperationalmodesanchor2"></a>Ausführmodus  
 Ausführungsmodus tritt auf, wenn ein Programm in einer Debugsitzung in der IDE ausgeführt wird. Die Anwendung ausgeführt, bis die Beendigung, bis ein Haltepunkt erreicht wird, oder eine Ausnahme ausgelöst wird. Wenn die Anwendung zu beenden, die DE Übergänge in den Entwurfsmodus versetzt ausgeführt wird. Wenn ein Haltepunkt erreicht wird, oder eine Ausnahme ausgelöst wird, geht die DE um in den Unterbrechungsmodus.  
  
##  <a name="vsconoperationalmodesanchor3"></a>Unterbrechungsmodus  
 Unterbrechungsmodus tritt auf, wenn die Ausführung des Programms Debuggen angehalten wird. Unterbrechungsmodus bietet dem Entwickler eine Momentaufnahme der Anwendung zum Zeitpunkt der Unterbrechung an und ermöglicht dem Entwickler, den Status der Anwendung analysieren und zu ändern, wie die Anwendung ausgeführt wird. Der Entwickler kann anzeigen und Bearbeiten von Code, zu überprüfen oder Ändern von Daten, die Anwendung neu starten, Ausführung beenden oder Fortsetzen der Ausführung desselben Zeitpunkts.  
  
 Unterbrechungsmodus eingegeben, wenn die DE eine synchrone Stopping-Ereignis sendet. Synchrone beenden-Ereignissen, die Ereignisse wird beendet, so genannte benachrichtigen den Sitzungs-Manager (SDM) und die IDE, die von die gedebuggten Anwendung beendet wurde, Ausführen von Code. Die [IDebugBreakpointEvent2](../../extensibility/debugger/reference/idebugbreakpointevent2.md) und [IDebugExceptionEvent2](../../extensibility/debugger/reference/idebugexceptionevent2.md) Schnittstellen sind Beispiele für Ereignisse wird beendet.  
  
 Beenden des Ereignisse werden durch einen Aufruf einer der folgenden Methoden Fortsetzung, die Übergang von der Debugger im Unterbrechungsmodus befinden, ausführen oder Schritt Modus:  
  
-   [Führen Sie](../../extensibility/debugger/reference/idebugprocess3-execute.md)  
  
-   [Step](../../extensibility/debugger/reference/idebugprocess3-step.md)  
  
-   [Continue](../../extensibility/debugger/reference/idebugprocess3-continue.md)  
  
###  <a name="vsconoperationalmodesanchor4"></a>Schritt-Modus  
 Schritt-Modus tritt auf, wenn das Programm in die nächste Zeile des Codes, oder ausführen, überspringen oder aus einer Funktion Schritte aus. Ein Schritt ausgeführt wird, durch Aufrufen der Methode [Schritt](../../extensibility/debugger/reference/idebugprocess3-step.md). Diese Methode erfordert `DWORD`s, die angeben, die [STEPUNIT](../../extensibility/debugger/reference/stepunit.md) und [STEPKIND](../../extensibility/debugger/reference/stepkind.md) Enumerationen als Eingabeparameter.  
  
 Wenn das Programm erfolgreich Schritte aus, um die nächste Zeile des Codes oder in eine Funktion oder erfolgt die Ausführung bis zum Cursor oder auf einen Haltepunkt festlegen, geht die DE automatisch zurück, um den Unterbrechungsmodus.  
  
## <a name="see-also"></a>Siehe auch  
 [Steuern der Ausführung](../../extensibility/debugger/control-of-execution.md)