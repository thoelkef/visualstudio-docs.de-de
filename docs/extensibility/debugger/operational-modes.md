---
title: "Betriebsmodi | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Debugmodule, Modi"
ms.assetid: f69972d0-809d-40df-9da3-04738791391c
caps.latest.revision: 13
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 13
---
# Betriebsmodi
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Es gibt drei Modi, in denen die IDE funktionieren kann wie folgt:  
  
-   [Entwurfsmodus](#vsconoperationalmodesanchor1)  
  
-   [Ausführmodus](#vsconoperationalmodesanchor2)  
  
-   [Unterbrechungsmodus](#vsconoperationalmodesanchor3)  
  
 Wie die benutzerdefinierten Übergänge des Moduls \(Debuggen\) zwischen den Modi DE entscheidung eine Implementierung erforderlich ist, mit den Mechanismen Übergangs vertraut sein.  DE implementiert möglicherweise direkt dieser Modi.  Diese Modi sind tatsächlich ändert Paket debuggen, die auf eine Benutzeraktion oder Ereignisse von DE wechseln.  Beispielsweise wird der Umstellung von Ausführmodus auf Unterbrechungsmodus durch ein aufhörendes DE Ereignis ausgelöst.  Der Übergang von Unterbrechen oder Ausführmodus an den Modus Schritt wird vom Benutzer ausgelöst, der Vorgänge wie Schritt ausgeführt wird oder ausgeführt wird.  Weitere Informationen über DE transitions finden Sie unter [Steuerung der Ausführung](../../extensibility/debugger/control-of-execution.md).  
  
##  <a name="vsconoperationalmodesanchor1"></a> Entwurfsmodus  
 Entwurfsmodus ist der inaktive Status von Visual Studio\-Debuggings, währenddessen Sie Debugfeatures in der Anwendung festlegen können.  
  
 Nur einige Debugfunktionen werden während des Entwurfsmodus verwendet.  Ein Entwickler könnte beschließt Überwachung oder Haltepunkte festzulegen, um Ausdrücke zu erstellen.  DE wird niemals geladen oder aufgerufen, während die IDE im Entwurfsmodus befindet.  Interaktion mit DE findet nur während der Ausführung und der Unterbrechungsmodi statt.  
  
##  <a name="vsconoperationalmodesanchor2"></a> Ausführmodus  
 Ausführmodus tritt auf, wenn ein Programm in einer Debugsitzung in der IDE ausgeführt wird.  Die Anwendung wird mit Beendigung ausgeführt, bis ein Haltepunkt erreicht wird oder wenn eine Ausnahme ausgelöst wird.  Wenn die Anwendung zur Beendigung ausgeführt wird, DE transitions in Design Mode.  Wenn ein Haltepunkt erreicht ist oder eine Ausnahme ausgelöst wird, DE transitions in den Unterbrechungsmodus befinden.  
  
##  <a name="vsconoperationalmodesanchor3"></a> Unterbrechungsmodus  
 Unterbrechungsmodus tritt auf, wenn die Ausführung des Debugprogramms angehalten wird.  Unterbrechungsmodus ermöglicht dem Entwickler eine Momentaufnahme der Anwendung zum Zeitpunkt der Unterbrechung an und ermöglicht es dem Entwickler, um den Zustand der Anwendung zu analysieren und zu ändern, wie die Anwendung ausgeführt wird.  Der Entwickler kann Code bearbeiten, und zeigen Sie die Daten überprüfen oder zu ändern, die Anwendung neu zu starten, um die Ausführung zu beenden oder Ausführung desselben Typs zeigen den Vorgang fortzusetzen.  
  
 Unterbrechungsmodus eingegeben wird, wenn ein synchrones DE aufhörendes Ereignis sendet.  Die synchrone aufhörenden Ereignisse, auch als Beenden von Ereignissen benachrichtigt, den Debug\- Manager der Sitzung \(SDM\) und die IDE, dem die Anwendung, die gedebuggt wird, beendet wurde, Code auszuführen.  Die [IDebugBreakpointEvent2](../../extensibility/debugger/reference/idebugbreakpointevent2.md) und [IDebugExceptionEvent2](../../extensibility/debugger/reference/idebugexceptionevent2.md)\-Schnittstellen sind Beispiele für Beendens von Ereignissen.  
  
 Beenden Ereignisse werden durch einen Aufruf an eine der folgenden Methoden, um die Fortsetzung der Debugger im Unterbrechungsmodus gewechselt wird die ausgeführt werden soll: Modus oder im Schritt  
  
-   [Ausführen](../../extensibility/debugger/reference/idebugprocess3-execute.md)  
  
-   [Schritt](../../extensibility/debugger/reference/idebugprocess3-step.md)  
  
-   [Weiter](../../extensibility/debugger/reference/idebugprocess3-continue.md)  
  
###  <a name="vsconoperationalmodesanchor4"></a> Schritt\-Modus  
 Der Modus tritt ein, sobald das Programm schrittweise durchläuft die nächste Codezeile aus, oder über eine Funktion oder ein.  Ein Schritt wird ausgeführt, indem die Methode [Schritt](../../extensibility/debugger/reference/idebugprocess3-step.md)aufruft.  Diese Methode erfordert `DWORD`s, das die [STEPUNIT](../../extensibility/debugger/reference/stepunit.md) und [STEPKIND](../../extensibility/debugger/reference/stepkind.md)\-Enumerationen als Eingabeparameter angeben.  
  
 Wenn das Programm die Schritte erfolgreich auf die nächste Codezeile oder eine Funktion oder er dem Cursor oder einem festgelegten Haltepunkt ausgeführt werden, die DEs automatisch wieder in den Unterbrechungsmodus wechselt.  
  
## Siehe auch  
 [Steuerung der Ausführung](../../extensibility/debugger/control-of-execution.md)