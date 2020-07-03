---
title: Debugaufgaben | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: overview
helpviewer_keywords:
- debugging [Debugging SDK], tasks
ms.assetid: 5d60e9e8-305e-4a48-829f-b9440fc8af7b
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 070068853d962bdf9b209edb9410d33d46ccf853
ms.sourcegitcommit: 05487d286ed891a04196aacd965870e2ceaadb68
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/02/2020
ms.locfileid: "85903559"
---
# <a name="debug-tasks"></a>Aufgaben Debuggen
Zum Debuggen eines Programms muss es gestartet werden, und es muss eine Debug-Engine (de) angefügt werden. andernfalls muss die de an ein zuvor gestartetes Programm angefügt werden. Nach dem Anfügen muss der de bestimmte Start Ereignisse generieren. Als Antwort versucht das Debug-Paket, die Breakpoints zu binden, die in der IDE festgelegt sind. Wenn das Programm auf einen gebundenen Haltepunkt trifft, wird es angehalten, und es wird auf eine Benutzereingabe gewartet.

## <a name="in-this-section"></a>In diesem Abschnitt
 [Sicherheitsprobleme](../../extensibility/debugger/security-issues.md) Erläutert die Sicherheits Schritte, die zum Debuggen eines Programms erforderlich sind.

 [Programm starten](../../extensibility/debugger/launching-a-program.md) Enthält Schritt-für-Schritt-Anleitungen zum Angeben einer de, die das Betriebssystem aufruft, um das Programm zu starten.

 [Direkt an ein Programm anfügen](../../extensibility/debugger/attaching-directly-to-a-program.md) Beschreibt den Prozess, der zum Debuggen eines Programms in einem Prozess verwendet wird, der bereits ausgeführt wird.

 [Start Ereignisse nach einem Start senden](../../extensibility/debugger/sending-startup-events-after-a-launch.md) Listet die Ereignisse auf, die nach dem Anfügen von de an das Programm stattfinden, bis sich das Programm an seinem Haupteinstiegspunkt befindet und zum Debuggen bereit ist.

 [Kontrolle der Ausführung](../../extensibility/debugger/control-of-execution.md) Erläutert, wie der de in der Regel abhängig von den jeweiligen Umständen ein Einstiegspunkt Ereignis, ein Ereignis zum Laden eines Ladevorgangs oder ein anhalteereignis sendet.

 [Binden](../../extensibility/debugger/binding-breakpoints.md) von Haltepunkten Beschreibt, wie die IDE die Anforderung formuliert und die Debugsitzung anfordert, den Breakpoint zu erstellen, wenn der Benutzer einen Haltepunkt festlegt.

 [Auswerten von Ausdrücken](../../extensibility/debugger/evaluating-expressions.md) Erläutert, wie Ausdrücke erstellt werden und was geschieht, wenn ein Ausdruck ausgewertet wird.

 [Visualisieren und Anzeigen von Daten](../../extensibility/debugger/visualizing-and-viewing-data.md) Erläutert, wie typvisualisierungen und benutzerdefinierte Viewer von der Ausdrucks Auswertung unterstützt werden.

## <a name="related-sections"></a>Verwandte Abschnitte
 [Debugger-Konzepte](../../extensibility/debugger/debugger-concepts.md) Beschreibt die wichtigsten Konzepte der debuggingarchitektur.

 [Debugger-Komponenten](../../extensibility/debugger/debugger-components.md) Bietet eine Übersicht über die Visual Studio-debuggingkomponenten, die de, EE und Symbol Handler (SH) enthalten.

 [Debugger-Kontexte](../../extensibility/debugger/debugger-contexts.md) Erläutert die gleichzeitige Funktionsweise von de innerhalb von Code-, Dokumentations-und Ausdrucks Auswertungs Kontexten. Beschreibt für jeden der drei Kontexte den Speicherort, die Position oder die Auswertung, die für ihn relevant sind.

## <a name="see-also"></a>Siehe auch
 [Erste Schritte](../../extensibility/debugger/getting-started-with-debugger-extensibility.md)
