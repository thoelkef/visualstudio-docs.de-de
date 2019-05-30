---
title: Debuggingaufgaben | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], tasks
ms.assetid: 5d60e9e8-305e-4a48-829f-b9440fc8af7b
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 774999dbdcb9eaf4a948364956ed95ab57e24d10
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/29/2019
ms.locfileid: "66345853"
---
# <a name="debug-tasks"></a>Tasks zum Debuggen
Um ein Programm zu debuggen, es muss gestartet werden und eine Debug-Engine (DE) angefügt werden muss, andernfalls die DE muss an eine bereits gestartete Programm angefügt werden. Nach dem Anfügen, muss die DE bestimmte Startup-Ereignisse generieren. Das debugpaket versucht, in der Antwort die Haltepunkte, die in der IDE zu binden. Wenn das Programm einen gebundenen Haltepunkt trifft, hält und Benutzereingaben wartet.

## <a name="in-this-section"></a>In diesem Abschnitt
 [Sicherheitsprobleme](../../extensibility/debugger/security-issues.md) erläutert die Sicherheitsschritte,, die zum Debuggen eines Programms erforderlich sind.

 [Ein Programm starten](../../extensibility/debugger/launching-a-program.md) enthält schrittweise Anweisungen zum Angeben einer bereitgestellten Kompatibilitätsrichtlinie, das Betriebssystem Ruft, um das Programm zu starten.

 [Fügen Sie direkt an ein Programm](../../extensibility/debugger/attaching-directly-to-a-program.md) beschreibt den Prozess verwendet, um ein Programm in einem Prozess zu debuggen, die bereits ausgeführt wird.

 [Senden von Start-Ereignissen nach einem Start](../../extensibility/debugger/sending-startup-events-after-a-launch.md) Listet die Ereignisse, die stattfinden, sobald die DE für das Programm, angefügt ist, bis das Programm auf der Haupteinstiegspunkt und zum Debuggen bereit ist.

 [Steuern der Ausführung](../../extensibility/debugger/control-of-execution.md) wird erläutert, wie die DE in der Regel ein Einstiegspunkt-Ereignis, ein Load-complete-Ereignis oder eine Beenden-Ereignis, je nach den Umständen sendet.

 [Binden von Haltepunkten](../../extensibility/debugger/binding-breakpoints.md) beschreibt, wie, wenn der Benutzer einen Haltepunkt festlegt, die IDE die Anforderung formuliert und werden aufgefordert, die Debugsitzung, um den Haltepunkt zu erstellen.

 [Auswerten von Ausdrücken](../../extensibility/debugger/evaluating-expressions.md) wird erläutert, wie Ausdrücke erstellt werden und was geschieht, wenn ein Ausdruck ausgewertet wird.

 [Visualisieren und Anzeigen von Daten](../../extensibility/debugger/visualizing-and-viewing-data.md) wird erläutert, wie von der ausdrucksauswertung (EE) typschnellansichten und benutzerdefinierten Viewer unterstützt werden.

## <a name="related-sections"></a>Verwandte Abschnitte
 [Debuggerkonzepte](../../extensibility/debugger/debugger-concepts.md) beschreibt die wichtigsten Konzepte für das Debuggen Architektur.

 [Debuggerkomponenten](../../extensibility/debugger/debugger-components.md) bietet eine Übersicht über die Visual Studio-debugging-Komponenten, die die DE, EE und Symbol Handler (SH) enthalten.

 [Debuggerkontexte](../../extensibility/debugger/debugger-contexts.md) wird erläutert, wie die DE gleichzeitig innerhalb von Code, Dokumentationen und Ausdruck Auswertung Kontexten ausgeführt wird. Beschreibt, für jede der drei Kontexten, Speicherort, Position oder Auswertung, die für sie relevant.

## <a name="see-also"></a>Siehe auch
 [Erste Schritte](../../extensibility/debugger/getting-started-with-debugger-extensibility.md)