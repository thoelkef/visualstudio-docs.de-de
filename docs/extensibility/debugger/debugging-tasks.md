---
title: Debuggen von Aufgaben | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], tasks
ms.assetid: 5d60e9e8-305e-4a48-829f-b9440fc8af7b
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: d41f53ab1392ea3c31908faf65a871fa100fbb3f
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/06/2020
ms.locfileid: "80738953"
---
# <a name="debug-tasks"></a>Debug-Aufgaben
Um ein Programm zu debuggen, muss es gestartet werden, und ein Debugmodul (DE) muss daran angefügt werden, andernfalls muss die DE an ein zuvor gestartetes Programm angefügt werden. Nach dem Anhängen muss die DE bestimmte Startereignisse generieren. Als Reaktion darauf versucht das Debugpaket, die in der IDE festgelegten Haltepunkte zu binden. Wenn das Programm einen gebundenen Haltepunkt erreicht, hält es an und wartet auf Benutzereingaben.

## <a name="in-this-section"></a>In diesem Abschnitt
 [Sicherheitsfragen](../../extensibility/debugger/security-issues.md) Erläutert die Sicherheitsschritte, die zum Debuggen eines Programms erforderlich sind.

 [Starten eines Programms](../../extensibility/debugger/launching-a-program.md) Enthält schritt für Schritt Anweisungen zum Angeben einer DE, die das Betriebssystem aufruft, um das Programm zu starten.

 [Direkt an ein Programm anhängen](../../extensibility/debugger/attaching-directly-to-a-program.md) Beschreibt den Prozess, der zum Debuggen eines Programms in einem Prozess verwendet wird, der bereits ausgeführt wird.

 [Senden von Startereignissen nach einem Start](../../extensibility/debugger/sending-startup-events-after-a-launch.md) Listet die Ereignisse auf, die stattfinden, sobald die DE an das Programm angefügt ist, bis sich das Programm am Haupteinstiegspunkt befindet und zum Debuggen bereit ist.

 [Kontrolle der Ausführung](../../extensibility/debugger/control-of-execution.md) Erläutert, wie die DE in der Regel ein Einstiegspunktereignis, ein Load-Complete-Ereignis oder ein Beenden-Ereignis sendet, je nach den Umständen.

 [Binden von Haltepunkten](../../extensibility/debugger/binding-breakpoints.md) Beschreibt, wie die IDE, wenn der Benutzer einen Haltepunkt festlegt, die Anforderung formuliert und die Debugsitzung zum Erstellen des Haltepunkts auffordert.

 [Ausdrücken auswerten](../../extensibility/debugger/evaluating-expressions.md) Erläutert, wie Ausdrücke erstellt werden und was geschieht, wenn ein Ausdruck ausgewertet wird.

 [Visualisieren und Anzeigen](../../extensibility/debugger/visualizing-and-viewing-data.md) von Daten Erläutert, wie Typvisualisierer und benutzerdefinierte Viewer vom Ausdrucksevaluator (EE) unterstützt werden.

## <a name="related-sections"></a>Verwandte Abschnitte
 [Debuggerkonzepte](../../extensibility/debugger/debugger-concepts.md) Beschreibt die wichtigsten Architekturkonzepte für das Debuggen.

 [Debugger-Komponenten](../../extensibility/debugger/debugger-components.md) Bietet eine Übersicht über die Visual Studio-Debugkomponenten, zu denen der DE-, EE- und Symbolhandler (SH) gehört.

 [Debuggerkontexte](../../extensibility/debugger/debugger-contexts.md) Erläutert, wie die DE gleichzeitig in Code-, Dokumentations- und Ausdrucksauswertungskontexten arbeitet. Beschreibt für jeden der drei Kontexte den Standort, die Position oder die Bewertung, die für ihn relevant sind.

## <a name="see-also"></a>Weitere Informationen
 [Erste Schritte](../../extensibility/debugger/getting-started-with-debugger-extensibility.md)
