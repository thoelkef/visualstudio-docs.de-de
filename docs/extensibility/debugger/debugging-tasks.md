---
title: Debuggingaufgaben | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], tasks
ms.assetid: 5d60e9e8-305e-4a48-829f-b9440fc8af7b
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 77cc933c49e15786221fd1cd3eb7e242118527a1
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/16/2018
ms.locfileid: "31101143"
---
# <a name="debugging-tasks"></a>Debugging-Aufgaben
Um ein Programm debuggen, er gestartet werden muss und ein Debugging-Modul (DE) muss an sie angefügt werden, da andernfalls die DE muss angefügt werden, um eine zuvor gestartete Programm. Nachdem angehängt wird, muss die DE bestimmte Startereignisse generieren. Reaktion versucht das debugpaket in der IDE festgelegten Breakpoints Bindung. Wenn das Programm einen gebundenen Haltepunkt trifft, hält an und wartet auf eine Benutzereingabe.  
  
## <a name="in-this-section"></a>In diesem Abschnitt  
 [Sicherheitsprobleme](../../extensibility/debugger/security-issues.md)  
 Erläutert die Schritten, die zum Debuggen eines Programms erforderlich sind.  
  
 [Starten eines Programms](../../extensibility/debugger/launching-a-program.md)  
 Enthält schrittweise Anleitungen zum Angeben einer bereitgestellten Kompatibilitätsrichtlinie das Betriebssystem Ruft, um das Programm zu starten.  
  
 [Direktes Anfügen an ein Programm](../../extensibility/debugger/attaching-directly-to-a-program.md)  
 Beschreibt den Prozess verwendet, um ein Programm in einem Prozess zu debuggen, die bereits ausgeführt wird.  
  
 [Senden von Startereignissen nach einem Start](../../extensibility/debugger/sending-startup-events-after-a-launch.md)  
 Listet die Ereignisse, die erfolgen, sobald die DE an das Programm angefügt wird, bis das Programm befindet sich auf der Haupteinstiegspunkt und bereit für das Debuggen ist.  
  
 [Steuern der Ausführung](../../extensibility/debugger/control-of-execution.md)  
 Erläutert, wie die DE in der Regel ein Einstiegspunkt Ereignis, ein Ereignis Laden abgeschlossen oder eine Stopping-Ereignis, je nach den Umständen sendet.  
  
 [Binden von Haltepunkten](../../extensibility/debugger/binding-breakpoints.md)  
 Beschreibt, wie, wenn der Benutzer einen Breakpoint festzulegen, die IDE formuliert die Anforderung und fordert die Debugsitzung, um den Haltepunkt zu erstellen.  
  
 [Auswerten von Ausdrücken](../../extensibility/debugger/evaluating-expressions.md)  
 Erläutert, wie Ausdrücke erstellt werden und was geschieht, wenn ein Ausdruck ausgewertet wird.  
  
 [Visualisieren und Anzeigen von Daten](../../extensibility/debugger/visualizing-and-viewing-data.md)  
 Erläutert, wie von der ausdrucksauswertung (EE) Typ-Schnellansichten und benutzerdefinierten Viewer unterstützt werden.  
  
## <a name="related-sections"></a>Verwandte Abschnitte  
 [Debuggerkonzepte](../../extensibility/debugger/debugger-concepts.md)  
 Beschreibt die wichtigsten Konzepte für das Debuggen Architektur.  
  
 [Debuggerkomponenten](../../extensibility/debugger/debugger-components.md)  
 Bietet eine Übersicht über Visual Studio debugging-Komponenten, z. B. die DE, EE und Symbol Handler ("SH").  
  
 [Debuggerkontexte](../../extensibility/debugger/debugger-contexts.md)  
 Erläutert, wie die DE gleichzeitig in Code, Dokumentation und ausdruckskontexten für die Auswertung ausgeführt wird. Beschreibt, für jede der drei Kontexten, die Position, Position oder Evaluation für sie relevant.  
  
## <a name="see-also"></a>Siehe auch  
 [Erste Schritte](../../extensibility/debugger/getting-started-with-debugger-extensibility.md)