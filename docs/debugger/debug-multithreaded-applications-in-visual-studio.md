---
title: Debuggen von Multithreadanwendungen | Microsoft-Dokumentation
ms.custom: seodec18
ms.date: 11/06/2018
ms.topic: conceptual
f1_keywords:
- vs.debug.gputthreads
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- threading [Visual Studio], debugging
- debugging [Visual Studio], high-performance computing
- debugging [Visual Studio], multithreaded
- multithreaded debugging
- high-performance debugging
ms.assetid: 9d175bc2-1d95-4c47-9bc3-9755af968a9c
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: b3f2fc8b6acd38393cf9fefb1c5581ab4d1a0712
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62852925"
---
# <a name="debug-multithreaded-applications-in-visual-studio"></a>Debuggen von Multithreadanwendungen in Visual Studio
Ein Thread ist eine Sequenz von Anweisungen, die auf die das Betriebssystem Prozessorzeit gewährt. Jeder Prozess, der im Betriebssystem ausgeführt wird, umfasst mindestens einen Thread. Prozesse, die über mehr als einen Thread verfügen, werden als Multithreadprozesse bezeichnet.

Computer mit mehreren Prozessoren, Mehrkernprozessoren oder Hyperthreadingprozessen können mehrere gleichzeitige Threads ausführen. Parallelverarbeitung mit vielen Threads kann die Leistung der Anwendung erheblich verbessern, aber es kann auch Debuggen erschweren, da Sie viele Threads nachverfolgen.

Multithreading kann neue potenzielle Fehlertypen eingeführt. Z. B. zwei oder mehr Threads müssen dieselbe Ressource zugreifen, aber jeweils nur ein Thread sicher auf die Ressource zugreifen kann. Eine Form des gegenseitigen Ausschlusses ist erforderlich, um sicherzustellen, dass zu einem beliebigen Zeitpunkt nur ein Thread die Ressource zugreift. Wenn wechselseitigen Ausschluss nicht richtig implementiert wird, können sie erstellen eine *Deadlock* Bedingung, in denen kein Thread ausgeführt wird. Deadlocks sind häufig ein schwieriges Problem Debuggen.

## <a name="tools-for-debugging-multithreaded-apps"></a>Tools zum Debuggen von Multithreadanwendungen

Visual Studio bietet verschiedene Tools für Verwendung beim Debuggen von Multithreadanwendungen.

- Für Threads, die wichtigsten Tools zum Debuggen von Threads sind die **Threads** , Threadmarker in Quellcodefenstern der **parallele Stapel** Fenster die **parallele Überwachung** Fenster, und die **Debugspeicherort** Symbolleiste. Informationen zu den **Threads** Fenster und **Debugspeicherort** Symbolleiste finden Sie unter [Exemplarische Vorgehensweise: Debuggen mithilfe des Fensters „Threads“](../debugger/how-to-use-the-threads-window.md). Informationen zum Verwenden der **parallele Stapel** und **parallele Überwachung** Windows finden Sie unter [erste Schritte zum Debuggen einer Multithreadanwendung](../debugger/get-started-debugging-multithreaded-apps.md). Beide Themen zeigen, wie Threadmarker verwendet wird.

- Für Code, verwendet der [Task Parallel Library (TPL)](/dotnet/standard/parallel-programming/task-parallel-library-tpl) oder [Concurrency Runtime](/cpp/parallel/concrt/concurrency-runtime/), sind die wichtigsten Tools zum Debuggen der **parallele Stapel** Fenster, das **Parallele Überwachung** Fenster, und die **Aufgaben** Fenster, in dem auch JavaScript unterstützt. Informationen zum Einstieg finden Sie unter [Exemplarische Vorgehensweise: Debuggen einer parallelen Anwendung](../debugger/walkthrough-debugging-a-parallel-application.md) und [Exemplarische Vorgehensweise: Debuggen einer C++ AMP-Anwendung](/cpp/parallel/amp/walkthrough-debugging-a-cpp-amp-application).

- Zum Debuggen von Threads auf der GPU, die das primäre Tool ist das **GPU-Threads** Fenster. Weitere Informationen finden Sie unter [How to: Use the GPU Threads window (Vorgehensweise: Verwenden des Fensters „GPU-Threads“)](../debugger/how-to-use-the-gpu-threads-window.md)

- Für Prozesse, die wichtigsten Tools sind die **an den Prozess anhängen** im Dialogfeld die **Prozesse** Fenster, und die **Debugspeicherort** Symbolleiste.

Visual Studio bietet auch leistungsstarke halte- und Ablaufverfolgungspunkte, die beim Debuggen von Multithreadanwendungen hilfreich sein können. Verwenden von haltepunktbedingungen und-Filter, um Haltepunkte auf einzelne Threads zu platzieren. Ablaufverfolgungspunkte ermöglichen es Ihnen, verfolgen Sie die Ausführung des Programms ohne aufzubrechen, um das Untersuchen von Problemen wie Deadlocks. Weitere Informationen finden Sie unter [Haltepunktaktionen und Ablaufverfolgungspunkte](../debugger/using-breakpoints.md#BKMK_Print_to_the_Output_window_with_tracepoints).

Das Debuggen einer Multithreadanwendung mit einer Benutzeroberfläche kann besonders schwierig sein. Sie sollten erwägen, Ausführen der Anwendung auf einem zweiten Computer und das Remotedebuggen zu verwenden. Weitere Informationen finden Sie unter [Remotedebuggen](../debugger/remote-debugging.md).

## <a name="articles-about-debugging-multithreaded-apps"></a>Artikel über das Debuggen von Multithreadanwendungen

 [Erste Schritte zum Debuggen einer Multithreadanwendung](../debugger/get-started-debugging-multithreaded-apps.md)

Einen Überblick über die Threaddebuggen, Hervorheben von Funktionen in der **parallele Stapel** Fenster und die **parallele Überwachung** Fenster.

 [Tools zum Debuggen von Threads und Prozessen](../debugger/debug-threads-and-processes.md)

Listet die Features der Tools zum Debuggen von Threads und Prozessen.

 [Debuggen mehrerer Prozesse](../debugger/debug-multiple-processes.md)

Erläutert das Debuggen mehrerer Prozesse.

 [Exemplarische Vorgehensweise: Debuggen mithilfe des Fensters „Threads“](../debugger/how-to-use-the-threads-window.md).

Exemplarische Vorgehensweise, die zeigt, wie Sie mit der **Threads** Fenster und die **Debugspeicherort** Symbolleiste.

 [Exemplarische Vorgehensweise: Debuggen einer parallelen Anwendung](../debugger/walkthrough-debugging-a-parallel-application.md)

Exemplarische Vorgehensweise, die zeigt, wie Sie mit der **parallele Stapel** und **Aufgaben** Windows.

 [Vorgehensweise: Switch to another thread while debugging (Vorgehensweise: Wechseln zu einem anderen Thread während des Debuggens)](../debugger/how-to-switch-to-another-thread-while-debugging.md)

Mehrere Möglichkeiten, um den Debugkontext zu einem anderen Thread zu wechseln.

 [Vorgehensweise: Flag and unflag threads (Vorgehensweise: Kennzeichnen von Threads und Aufheben der Kennzeichnung)](../debugger/how-to-flag-and-unflag-threads.md)

Markieren oder Kennzeichnen von Threads, die beim Debuggen besondere Aufmerksamkeit erhalten sollen.

 [Vorgehensweise: Debug on a high-performance cluster (Vorgehensweise: Debuggen auf einem Hochleistungscluster)](../debugger/how-to-debug-on-a-high-performance-cluster.md)

Techniken zum Debuggen einer Anwendung, die auf einem Hochleistungscluster ausgeführt wird.

 [Tipps zum Debuggen von Threads in nativem Code](../debugger/tips-for-debugging-threads-in-native-code.md)

Einfache Techniken, die beim Debuggen systemeigener Threads hilfreich sein können.

 [Vorgehensweise: Set a thread name in native code (Vorgehensweise: Festlegen eines Threadnamens in nativem Code)](../debugger/how-to-set-a-thread-name-in-native-code.md)

Geben Sie Ihrem Thread einen Namen, der im Fenster **Threads** angezeigt wird.

 [Vorgehensweise: Set a thread name in managed code (Vorgehensweise: Festlegen eines Threadnamens in verwaltetem Code)](../debugger/how-to-set-a-thread-name-in-managed-code.md)

Geben Sie Ihrem Thread einen Namen, der im Fenster **Threads** angezeigt wird.

## <a name="see-also"></a>Siehe auch

- [Verwenden von Haltepunkten](../debugger/using-breakpoints.md)
- [Threading](/dotnet/standard/threading/index)
- [Multithreading in components (Multithreading in Komponenten)](https://msdn.microsoft.com/Library/2fc31e68-fb71-4544-b654-0ce720478779)
- [Multithreading support for older code (Visual C++) (Multithreadingunterstützung für älteren Code (Visual C++))](/cpp/parallel/multithreading-support-for-older-code-visual-cpp)
- [Debug threads and processes (Debuggen von Threads und Prozessen)](../debugger/debug-threads-and-processes.md)
- [Remotedebuggen](../debugger/remote-debugging.md)