---
title: Betriebsmodi | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- debug engines, modes
ms.assetid: f69972d0-809d-40df-9da3-04738791391c
caps.latest.revision: 14
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: c4009ab6268140117c8fd1294adcc52ac347b799
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "68153718"
---
# <a name="operational-modes"></a>Betriebsmodi
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Es gibt drei Modi, in denen die IDE funktionieren kann, wie im folgenden dargestellt:  
  
- [Entwurfsmodus](#vsconoperationalmodesanchor1)  
  
- [Lauf Modus](#vsconoperationalmodesanchor2)  
  
- [Break-Modus](#vsconoperationalmodesanchor3)  
  
  Die Art und Weise, wie Ihre benutzerdefinierte Debug-Engine (de) zwischen diesen Modi wechselt, ist eine Implementierungs Entscheidung, bei der Sie mit den Übergangsmechanismen vertraut sein müssen. Diese Modi können von de oder nicht direkt implementiert werden. Diese Modi sind wirklich Debug-paketmodi, die auf der Grundlage von Benutzeraktionen oder Ereignissen aus der de wechseln. Beispielsweise wird der Übergang vom Lauf Modus zum Break-Modus durch ein anhalteereignis aus der de ausgelöst. Der Übergang von der Pause zum Ausführungs Modus oder Schritt Modus wird durch den Benutzer ausgelöst, der Vorgänge ausführt, z. b. Schritt oder ausführen. Weitere Informationen zu de-Übergängen finden Sie unter [Steuerung der Ausführung](../../extensibility/debugger/control-of-execution.md).  
  
## <a name="design-mode"></a><a name="vsconoperationalmodesanchor1"></a> Entwurfs Modus  
 Beim Entwurfs Modus handelt es sich um den nicht ausgestellten Status des Visual Studio-Debuggens. in diesem Zeitraum können Sie Debuggingfunktionen in der Anwendung  
  
 Im Entwurfs Modus werden nur einige Debuggingfunktionen verwendet. Ein Entwickler kann festlegen, dass Breakpoints festgelegt oder Überwachungs Ausdrücke erstellt werden. Die de wird niemals geladen oder aufgerufen, während sich die IDE im Entwurfs Modus befindet. Die Interaktion mit der de findet nur während der Lauf-und Umbruch Modi statt.  
  
## <a name="run-mode"></a><a name="vsconoperationalmodesanchor2"></a> Lauf Modus  
 Der Ausführungs Modus tritt auf, wenn ein Programm in einer Debugsitzung in der IDE ausgeführt wird. Die Anwendung wird bis zum Abbruch ausgeführt, bis ein Breakpoint gedrückt wird oder bis eine Ausnahme ausgelöst wird. Wenn die Anwendung bis zum Beenden ausgeführt wird, wechselt die de in den Entwurfs Modus. Wenn ein Breakpoint gedrückt wird oder eine Ausnahme ausgelöst wird, wechselt die de in den Break-Modus.  
  
## <a name="break-mode"></a><a name="vsconoperationalmodesanchor3"></a> Break-Modus  
 Der unterbruchs Modus tritt auf, wenn die Ausführung des debugprogramms angehalten wird. Der Break-Modus bietet dem Entwickler eine Momentaufnahme der Anwendung zum Zeitpunkt der Unterbrechung und ermöglicht es dem Entwickler, den Zustand der Anwendung zu analysieren und zu ändern, wie die Anwendung ausgeführt wird. Der Entwickler kann Code anzeigen und bearbeiten, Daten überprüfen oder ändern, die Anwendung neu starten, die Ausführung beenden oder die Ausführung von demselben Punkt aus fortsetzen.  
  
 Der Break-Modus wird eingegeben, wenn von de ein synchrones anhalteereignis gesendet wird. Beim synchronen Beenden von Ereignissen, auch als Beendigungs Ereignisse bezeichnet, wird der Sitzungs-Debug-Manager (SDM) und die IDE benachrichtigt, dass die zu debuggende Anwendung nicht mehr ausgeführt wird. Die [IDebugBreakpointEvent2](../../extensibility/debugger/reference/idebugbreakpointevent2.md) -und [IDebugExceptionEvent2](../../extensibility/debugger/reference/idebugexceptionevent2.md) -Schnittstellen sind Beispiele für das Beenden von Ereignissen.  
  
 Das Beenden von Ereignissen wird durch einen Rückruf einer der folgenden Methoden fortgesetzt, die den Debugger vom Unterbrechungs Modus zum Ausführen oder Schritt Modus übergehen:  
  
- [Ausführen](../../extensibility/debugger/reference/idebugprocess3-execute.md)  
  
- [Schritt](../../extensibility/debugger/reference/idebugprocess3-step.md)  
  
- [Fortsetzen](../../extensibility/debugger/reference/idebugprocess3-continue.md)  
  
### <a name="step-mode"></a><a name="vsconoperationalmodesanchor4"></a> Schritt Modus  
 Der Schritt Modus tritt auf, wenn das Programm die nächste Codezeile oder eine Funktion in eine Funktion wechselt. Ein Schritt wird ausgeführt, indem der Methoden [Schritt](../../extensibility/debugger/reference/idebugprocess3-step.md)aufgerufen wird. Diese Methode erfordert `DWORD` s, die die [stepunit](../../extensibility/debugger/reference/stepunit.md) -und [stepkind](../../extensibility/debugger/reference/stepkind.md) -Enumerationen als Eingabeparameter angeben.  
  
 Wenn das Programm erfolgreich in die nächste Codezeile oder in eine Funktion wechselt oder bis zum Cursor oder zu einem festgelegten Breakpoint ausgeführt wird, wechselt der de automatisch zurück in den Break-Modus.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Steuern der Ausführung](../../extensibility/debugger/control-of-execution.md)
