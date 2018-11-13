---
title: Debuggen von Multithreadanwendungen in Visual Studio | Microsoft-Dokumentation
ms.custom: ''
ms.date: 11/06/2018
ms.technology: vs-ide-debug
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
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 599880f3c8e04b742ab943304ac910f8c0bcbe78
ms.sourcegitcommit: bc43970c000f07c9cc2051f1264a9742943a9755
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/09/2018
ms.locfileid: "51349529"
---
# <a name="debug-multithreaded-applications-in-visual-studio"></a>Debuggen von Multithreadanwendungen in Visual Studio
Ein Thread ist eine Sequenz von Anweisungen, die auf die das Betriebssystem Prozessorzeit gewährt. Jeder Prozess, der im Betriebssystem ausgeführt wird, umfasst mindestens einen Thread. Prozesse, die über mehr als einen Thread verfügen, werden als Multithreadprozesse bezeichnet.  
  
Computer mit mehreren Prozessoren, Mehrkernprozessoren oder Hyperthreadingprozessen können mehrere gleichzeitige Threads ausführen. Parallelverarbeitung mit vielen Threads kann die Leistung der Anwendung erheblich verbessern, aber es kann auch Debuggen erschweren, da Sie viele Threads nachverfolgen.  
  
Multithreading kann neue potenzielle Fehlertypen eingeführt. Z. B. zwei oder mehr Threads müssen dieselbe Ressource zugreifen, aber jeweils nur ein Thread sicher auf die Ressource zugreifen kann. Eine Form des gegenseitigen Ausschlusses ist erforderlich, um sicherzustellen, dass zu einem beliebigen Zeitpunkt nur ein Thread die Ressource zugreift. Wenn wechselseitigen Ausschluss nicht richtig implementiert wird, können sie erstellen eine *Deadlock* Bedingung, in denen kein Thread ausgeführt wird. Deadlocks sind häufig ein schwieriges Problem Debuggen.

## <a name="tools-for-debugging-multithreaded-apps"></a>Tools zum Debuggen von Multithreadanwendungen

Visual Studio bietet verschiedene Tools für Verwendung beim Debuggen von Multithreadanwendungen.

- Für Threads, die wichtigsten Tools zum Debuggen von Threads sind die **Threads** , Threadmarker in Quellcodefenstern der **parallele Stapel** Fenster die **parallele Überwachung** Fenster, und die **Debugspeicherort** Symbolleiste. Informationen zu den **Threads** Fenster und **Debugspeicherort** Symbolleiste finden Sie unter [Exemplarische Vorgehensweise: Debuggen mithilfe des Fensters Threads](../debugger/how-to-use-the-threads-window.md). Informationen zum Verwenden der **parallele Stapel** und **parallele Überwachung** Windows finden Sie unter [erste Schritte zum Debuggen einer Multithreadanwendung](../debugger/get-started-debugging-multithreaded-apps.md). Beide Themen zeigen, wie Threadmarker verwendet wird.
  
- Für Code, verwendet der [Task Parallel Library (TPL)](/dotnet/standard/parallel-programming/task-parallel-library-tpl) oder [Concurrency Runtime](/cpp/parallel/concrt/concurrency-runtime/), sind die wichtigsten Tools zum Debuggen der **parallele Stapel** Fenster, das **Parallele Überwachung** Fenster, und die **Aufgaben** Fenster, in dem auch JavaScript unterstützt. Informationen zum Einstieg finden Sie unter [Exemplarische Vorgehensweise: Debuggen einer parallelen Anwendung](../debugger/walkthrough-debugging-a-parallel-application.md) und [Exemplarische Vorgehensweise: Debuggen einer C++ AMP-Anwendung](/cpp/parallel/amp/walkthrough-debugging-a-cpp-amp-application). 

- Zum Debuggen von Threads auf der GPU, die das primäre Tool ist das **GPU-Threads** Fenster. Finden Sie unter [Vorgehensweise: Verwenden von GPU-Threadfenster](../debugger/how-to-use-the-gpu-threads-window.md).  

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

 [Exemplarische Vorgehensweise: Debuggen mithilfe des Fensters Threads](../debugger/how-to-use-the-threads-window.md).  
 Exemplarische Vorgehensweise, die zeigt, wie Sie mit der **Threads** Fenster und die **Debugspeicherort** Symbolleiste. 

 [Exemplarische Vorgehensweise: Debuggen einer parallelen Anwendung](../debugger/walkthrough-debugging-a-parallel-application.md)  
 Exemplarische Vorgehensweise, die zeigt, wie Sie mit der **parallele Stapel** und **Aufgaben** Windows.  
  
 [Gewusst wie: Wechseln zu einem anderen Thread während des Debuggings](../debugger/how-to-switch-to-another-thread-while-debugging.md)  
 Mehrere Möglichkeiten, um den Debugkontext zu einem anderen Thread zu wechseln.  
  
 [Gewusst wie: Kennzeichnen von Threads und Aufheben der Kennzeichnung](../debugger/how-to-flag-and-unflag-threads.md)  
 Markieren oder Kennzeichnen von Threads, die beim Debuggen besondere Aufmerksamkeit erhalten sollen.    
  
 [Gewusst wie: Debuggen auf einem Hochleistungscluster](../debugger/how-to-debug-on-a-high-performance-cluster.md)  
 Techniken zum Debuggen einer Anwendung, die auf einem Hochleistungscluster ausgeführt wird.  

 [Tipps zum Debuggen von Threads in nativem Code](../debugger/tips-for-debugging-threads-in-native-code.md)  
 Einfache Techniken, die beim Debuggen systemeigener Threads hilfreich sein können. 

 [Gewusst wie: Festlegen eines Threadnamens in nativem Code](../debugger/how-to-set-a-thread-name-in-native-code.md)  
 Benennen Sie Ihr Thread in der angezeigten der **Threads** Fenster.  
  
 [Gewusst wie: Festlegen eines Threadnamens in verwaltetem Code](../debugger/how-to-set-a-thread-name-in-managed-code.md)  
 Benennen Sie Ihr Thread in der angezeigten der **Threads** Fenster. 
  
## <a name="see-also"></a>Siehe auch  

[Verwenden von Haltepunkten](../debugger/using-breakpoints.md)  
[Threading](/dotnet/standard/threading/index)  
[Multithreading in Komponenten](https://msdn.microsoft.com/Library/2fc31e68-fb71-4544-b654-0ce720478779)  
[Multithreadingunterstützung für älteren Code (Visual C++)](/cpp/parallel/multithreading-support-for-older-code-visual-cpp)  
 [Debuggen von Threads und Prozessen](../debugger/debug-threads-and-processes.md)   
 [Remotedebuggen](../debugger/remote-debugging.md)