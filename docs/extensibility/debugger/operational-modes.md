---
title: Betriebsmodi | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debug engines, modes
ms.assetid: f69972d0-809d-40df-9da3-04738791391c
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 027152b2b2fc18b509a687220e5d963ea1b7e721
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/06/2020
ms.locfileid: "80738281"
---
# <a name="operational-modes"></a>Betriebsmodi
Es gibt drei Modi, in denen die IDE wie folgt betrieben werden kann:

- [Designmodus](#vsconoperationalmodesanchor1)

- [Laufmodus](#vsconoperationalmodesanchor2)

- [Break-Modus](#vsconoperationalmodesanchor3)

  Wie Ihr benutzerdefiniertes Debugmodul (DE) zwischen diesen Modi wechselt, ist eine Implementierungsentscheidung, bei der Sie mit den Übergangsmechanismen vertraut sein müssen. Die DE kann diese Modi direkt implementieren oder auch nicht direkt implementieren. Bei diesen Modi handelt es sich wirklich um Debugpaketmodi, die basierend auf Benutzeraktionen oder Ereignissen aus der DE wechseln. Beispielsweise wird der Übergang vom Ausführungsmodus in den Unterbrechungsmodus durch ein Stoppereignis aus dem DE initiiert. Der Übergang vom Unterbrechungsmodus in den Ausführungsmodus oder im Schrittmodus wird vom Benutzer initiiert, der Vorgänge wie Schritt oder Ausführen ausführt. Weitere Informationen zu DE-Übergängen finden Sie unter [Steuerung der Ausführung](../../extensibility/debugger/control-of-execution.md).

## <a name="design-mode"></a><a name="vsconoperationalmodesanchor1"></a>Designmodus
 Der Entwurfsmodus ist der nicht ausgeführte Status des Visual Studio-Debuggens, in dem Sie Debugfeatures in der Anwendung festlegen können.

 Im Entwurfsmodus werden nur wenige Debugfunktionen verwendet. Ein Entwickler kann Breakpoints festlegen oder Überwachungsausdrücke erstellen. Die DE wird nie geladen oder aufgerufen, während sich die IDE im Entwurfsmodus befindet. Die Interaktion mit der DE findet nur während des Lauf- und Pausenmodus statt.

## <a name="run-mode"></a><a name="vsconoperationalmodesanchor2"></a>Laufmodus
 Der Ausführungsmodus wird ausgeführt, wenn ein Programm in einer Debugsitzung in der IDE ausgeführt wird. Die Anwendung wird bis zum Beenden ausgeführt, bis ein Haltepunkt erreicht wird oder bis eine Ausnahme ausgelöst wird. Wenn die Anwendung zum Beenden ausgeführt wird, wechselt die DE in den Entwurfsmodus. Wenn ein Haltepunkt getroffen oder eine Ausnahme ausgelöst wird, wechselt der DE in den Unterbrechungsmodus.

## <a name="break-mode"></a><a name="vsconoperationalmodesanchor3"></a>Break-Modus
 Der Unterbrechungsmodus tritt auf, wenn die Ausführung des Debugprogramms angehalten wird. Der Unterbrechungsmodus bietet dem Entwickler eine Momentaufnahme der Anwendung zum Zeitpunkt der Unterbrechung und ermöglicht es dem Entwickler, den Status der Anwendung zu analysieren und die Ausführung der Anwendung zu ändern. Der Entwickler kann Code anzeigen und bearbeiten, Daten untersuchen oder ändern, die Anwendung neu starten, die Ausführung beenden oder die Ausführung vom selben Punkt aus fortsetzen.

 Der Unterbrechungsmodus wird aktiviert, wenn die DE ein synchrones Stoppereignis sendet. Synchrone Beendigungsereignisse, auch als Stoppereignisse bezeichnet, benachrichtigen den Sitzungsdebug-Manager (SDM) und die IDE, dass die zu debuggende Anwendung den Code nicht mehr ausgeführt hat. Die Schnittstellen [IDebugBreakpointEvent2](../../extensibility/debugger/reference/idebugbreakpointevent2.md) und [IDebugExceptionEvent2](../../extensibility/debugger/reference/idebugexceptionevent2.md) sind Beispiele für das Beenden von Ereignissen.

 Das Beenden von Ereignissen wird durch einen Aufruf einer der folgenden Methoden fortgesetzt, die den Debugger vom Unterbrechungsmodus in den Ausführungs- oder Schrittmodus überführen:

- [Ausführen](../../extensibility/debugger/reference/idebugprocess3-execute.md)

- [Schritt](../../extensibility/debugger/reference/idebugprocess3-step.md)

- [Continue](../../extensibility/debugger/reference/idebugprocess3-continue.md)

### <a name="step-mode"></a><a name="vsconoperationalmodesanchor4"></a>Schrittmodus
 Der Schrittmodus tritt auf, wenn das Programm zur nächsten Codezeile oder in eine Funktion, über oder a-out tritt. Ein Schritt wird ausgeführt, indem die Methode [Step](../../extensibility/debugger/reference/idebugprocess3-step.md)aufgerufen wird. Diese Methode `DWORD`erfordert s, die die [STEPUNIT-](../../extensibility/debugger/reference/stepunit.md) und STEPKIND-Enumerationen als Eingabeparameter angeben. [STEPKIND](../../extensibility/debugger/reference/stepkind.md)

 Wenn das Programm erfolgreich zur nächsten Codezeile oder in eine Funktion tritt oder zum Cursor oder zu einem festgelegten Haltepunkt ausgeführt wird, wechselt die DE automatisch zurück in den Unterbrechungsmodus.

## <a name="see-also"></a>Weitere Informationen
- [Kontrolle der Ausführung](../../extensibility/debugger/control-of-execution.md)
