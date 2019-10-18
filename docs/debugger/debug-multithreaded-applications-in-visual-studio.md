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
ms.openlocfilehash: 668e95c340348eeb1fa509622aa44d99b65b6efc
ms.sourcegitcommit: 485ffaedb1ade71490f11cf05962add1718945cc
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/16/2019
ms.locfileid: "72431804"
---
# <a name="debug-multithreaded-applications-in-visual-studio"></a>Debuggen von Multithreadanwendungen in Visual Studio
Ein Thread ist eine Abfolge von Anweisungen, denen das Betriebssystem Prozessorzeit zuweist. Jeder Prozess, der im Betriebssystem ausgeführt wird, umfasst mindestens einen Thread. Prozesse, die über mehr als einen Thread verfügen, werden als Multithreadprozesse bezeichnet.

Auf Computern mit mehreren Prozessoren, Multi-Core-Prozessoren oder Hyperthreading-Prozessen können mehrere gleichzeitige Threads ausgeführt werden. Die parallele Verarbeitung mit vielen Threads kann die Programmleistung erheblich verbessern, aber auch das Debuggen erschwert werden, da viele Threads nachverfolgt werden.

Durch das Multithreading können neue Arten potenzieller Fehler eingeführt werden. Beispielsweise müssen zwei oder mehr Threads möglicherweise auf dieselbe Ressource zugreifen, aber jeweils nur ein Thread kann sicher auf die Ressource zugreifen. Eine Form des gegenseitigen Ausschlusses ist erforderlich, um sicherzustellen, dass zu einem beliebigen Zeitpunkt nur ein Thread auf die Ressource zugreift. Wenn der gegenseitige Ausschluss nicht ordnungsgemäß implementiert ist, kann er eine Deadlockbedingung erstellen, in *der kein Thread* ausgeführt wird. Deadlocks sind häufig ein schwer zu debuggenden Problem.

## <a name="tools-for-debugging-multithreaded-apps"></a>Tools zum Debuggen von Multithread-apps

Visual Studio stellt verschiedene Tools für das Debuggen von Multithread-apps bereit.

- Bei Threads handelt es sich bei den primären Tools zum Debuggen von Threads um das Fenster **Threads** , Thread Markierungen in Quell Fenstern, das Fenster **parallele Stapel** , das Fenster **parallele Überwachung** und die Symbolleiste **Debugspeicherort** . Weitere Informationen zum Fenster **Threads** und zum **Debugspeicherort** finden Sie unter Exemplarische Vorgehensweise [: Debuggen mithilfe des Fensters "Threads](../debugger/how-to-use-the-threads-window.md)". Informationen dazu, wie Sie **parallele Stapel** und **parallele Überwachungs** Fenster verwenden, finden Sie unter Einstieg in das [Debuggen einer Multithreadanwendung](../debugger/get-started-debugging-multithreaded-apps.md). Beide Themen zeigen, wie Thread Marker verwendet werden.

- Für Code, in dem die [Task Parallel Library (TPL)](/dotnet/standard/parallel-programming/task-parallel-library-tpl) oder die [Concurrency Runtime](/cpp/parallel/concrt/concurrency-runtime/)verwendet wird, sind die wichtigsten Tools für das Debuggen das Fenster **parallele Stapel** , das Fenster **parallele Überwachung** und das Fenster **Tasks** , das auch Ja. Weitere Informationen finden Sie unter Exemplarische Vorgehensweise [: Debuggen einer parallelen Anwendung](../debugger/walkthrough-debugging-a-parallel-application.md) und Exemplarische Vorgehensweise [: Debuggen einer C++ amp-Anwendung](/cpp/parallel/amp/walkthrough-debugging-a-cpp-amp-application)

- Beim Debuggen von Threads auf der GPU ist das primäre Tool das **GPU-Thread** Fenster. Siehe Gewusst [wie: Verwenden des Fensters "GPU-Threads](../debugger/how-to-use-the-gpu-threads-window.md)".

- Für Prozesse sind die primären Tools das Dialogfeld **an den Prozess anhängen** , das Fenster **Prozesse** und die Symbolleiste **Debugspeicherort** .

Visual Studio bietet auch leistungsstarke Haltepunkte und Ablauf Verfolgungs Punkte, die beim Debuggen von Multithreadanwendungen nützlich sein können. Verwenden Sie Haltepunkt Bedingungen und Filter, um Haltepunkte in einzelnen Threads zu platzieren. Ablauf Verfolgungs Punkte ermöglichen es Ihnen, die Ausführung des Programms ohne Unterbrechung zu verfolgen, um Probleme wie Deadlocks zu untersuchen. Weitere Informationen finden Sie unterhalte [Punkt Aktionen und](../debugger/using-breakpoints.md#BKMK_Print_to_the_Output_window_with_tracepoints)Ablauf Verfolgungs Punkte.

Das Debuggen einer Multithreadanwendung mit einer Benutzeroberfläche kann besonders schwierig sein. Sie sollten die Anwendung auf einem zweiten Computer ausführen und Remote Debugging verwenden. Weitere Informationen finden Sie unter [Remote Debuggen](../debugger/remote-debugging.md).

## <a name="articles-about-debugging-multithreaded-apps"></a>Artikel zum Debuggen von Multithread-apps

 [Starten des Debuggens einer Multithread-Anwendung](../debugger/get-started-debugging-multithreaded-apps.md)

Eine Tour durch Thread-Debuggingfunktionen, die Features im Fenster **parallele Stapel** und im Fenster **parallele Überwachung** hervorheben.

 [Tools zum Debuggen von Threads und Prozessen](../debugger/debug-threads-and-processes.md)

Listet die Funktionen der Tools zum Debuggen von Threads und Prozessen auf.

 [Debuggen mehrerer Prozesse](../debugger/debug-multiple-processes.md)

Erläutert das Debuggen mehrerer Prozesse.

 [Walkthrough: Debug using the Threads window (Exemplarische Vorgehensweise: Debuggen mithilfe des Fensters „Threads“)](../debugger/how-to-use-the-threads-window.md)

Exemplarische Vorgehensweise, die zeigt, wie das Fenster **Threads** und die Symbolleiste **Debugspeicherort** verwendet werden.

 [Exemplarische Vorgehensweise: Debuggen einer parallelen Anwendung](../debugger/walkthrough-debugging-a-parallel-application.md)

Exemplarische Vorgehensweise, die zeigt, wie die Fenster **parallele Stapel** und **Aufgaben** verwendet werden.

 [Gewusst wie: Wechseln zu einem anderen Thread während des Debuggings](../debugger/how-to-switch-to-another-thread-while-debugging.md)

Es gibt mehrere Möglichkeiten, den debuggingkontext auf einen anderen Thread zu

 [Gewusst wie: Kennzeichnen von Threads und Aufheben der Kennzeichnung](../debugger/how-to-flag-and-unflag-threads.md)

Markieren oder Kennzeichnen von Threads, die beim Debuggen besondere Aufmerksamkeit erhalten sollen.

 [How to: Debug on a high-performance cluster (Vorgehensweise: Debuggen eines Hochleistungsclusters)](../debugger/how-to-debug-on-a-high-performance-cluster.md)

Techniken zum Debuggen einer Anwendung, die auf einem Hochleistungscluster ausgeführt wird.

 [Tipps zum Debuggen von Threads in nativem Code](../debugger/tips-for-debugging-threads-in-native-code.md)

Einfache Techniken, die beim Debuggen systemeigener Threads hilfreich sein können.

 [Gewusst wie: Festlegen eines Threadnamens in nativem Code](../debugger/how-to-set-a-thread-name-in-native-code.md)

Geben Sie Ihrem Thread einen Namen, der im Fenster **Threads** angezeigt wird.

 [Gewusst wie: Festlegen eines Threadnamens in verwaltetem Code](../debugger/how-to-set-a-thread-name-in-managed-code.md)

Geben Sie Ihrem Thread einen Namen, der im Fenster **Threads** angezeigt wird.

## <a name="see-also"></a>Siehe auch

- [Verwenden von Haltepunkten](../debugger/using-breakpoints.md)
- [Threading](/dotnet/standard/threading/index)
- [Multithreading in components (Multithreading in Komponenten)](https://msdn.microsoft.com/Library/2fc31e68-fb71-4544-b654-0ce720478779)
- [Multithreading-Unterstützung für älteren Code](/cpp/parallel/multithreading-support-for-older-code-visual-cpp)
- [Debug threads and processes (Debuggen von Threads und Prozessen)](../debugger/debug-threads-and-processes.md)
- [Remotedebuggen](../debugger/remote-debugging.md)