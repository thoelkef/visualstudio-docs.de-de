---
title: Debuggen von Multithreadanwendungen
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.debug.gputthreads
dev_langs:
- FSharp
- VB
- CSharp
- C++
helpviewer_keywords:
- threading [Visual Studio], debugging
- debugging [Visual Studio], high-performance computing
- debugging [Visual Studio], multithreaded
- multithreaded debugging
- high-performance debugging
ms.assetid: 9d175bc2-1d95-4c47-9bc3-9755af968a9c
caps.latest.revision: 28
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 8cb43c9a32f3dfd0a6383d466f7cd283acf0ab3a
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "65691278"
---
# <a name="debug-multithreaded-applications-in-visual-studio"></a>Debuggen von Multithreadanwendungen in Visual Studio
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Ein Thread ist eine Folge von Anweisungen, für die das Betriebssystem Prozessorzeit reserviert. Jeder Prozess, der im Betriebssystem ausgeführt wird, umfasst mindestens einen Thread. Prozesse, die über mehr als einen Thread verfügen, werden als Multithreadprozesse bezeichnet.

 Auf Computern mit mehreren Prozessoren, Mehrkernprozessoren oder Hyperthreadingprozessen können mehrere Threads gleichzeitig ausgeführt werden. Die parallele Verarbeitung mehrerer Threads kann sich äußerst positiv auf die Programmleistung auswirken, andererseits aber auch das Debuggen erschweren, da in diesem Fall mehrere Threads verfolgt werden müssen.

 Außerdem werden durch das Multithreading neue potenzielle Fehlertypen eingeführt. Beispielsweise müssen zwei oder mehr Threads häufig auf dieselbe Ressource zugreifen, während jeweils nur ein Thread sicher auf die Ressource zugreifen kann. Um sicherzustellen, dass immer nur ein Thread auf die Ressource zugreifen kann, ist eine Form des gegenseitigen Ausschlusses erforderlich. Wenn der gegenseitige Ausschluss nicht ordnungsgemäß ausgeführt wird, kann er eine Deadlockbedingung erstellen, in *der kein Thread* ausgeführt werden kann. Deadlocks können beim Debuggen ein besonders schwerwiegendes Problem verursachen.

 Visual Studio bietet ein **Thread** Fenster, ein GPU-Thread Fenster, eine parallele Überwachungsfenster und andere Features, die multithreaddebugging vereinfachen. Es wird empfohlen, sich mithilfe der exemplarischen Vorgehensweise mit den Threading-Funktionen vertraut zu machen. Siehe Exemplarische Vorgehensweise [: Debuggen einer Multithread-Anwendung](../debugger/walkthrough-debugging-a-multithreaded-application.md) und Exemplarische Vorgehensweise [: Debuggen einer C++ amp](https://msdn.microsoft.com/library/40e92ecc-f6ba-411c-960c-b3047b854fb5)

 Visual Studio stellt auch leistungsstarke Halte- und Ablaufverfolgungspunkte bereit, die beim Debuggen von Multithreadanwendungen sehr hilfreich sein können. Um Haltepunkte in einzelnen Threads zu platzieren, können Sie Haltepunktfilter verwenden. Siehe [Verwenden von Breakpoints](../debugger/using-breakpoints.md)

 Das Debuggen einer Multithreadanwendung mit einer Benutzeroberfläche kann besonders schwierig sein. In diesem Fall könnten Sie erwägen, die Anwendung auf einem zweiten Computer auszuführen und das Remotedebuggen zu verwenden. Weitere Informationen finden Sie unter [Remote Debuggen](../debugger/remote-debugging.md).

## <a name="in-this-section"></a>In diesem Abschnitt
 [Debuggen von Threads und Prozessen](../debugger/debug-threads-and-processes.md) Erläutert die Grundlagen des Debuggens von Threads und Prozessen.

 [Debuggen mehrerer Prozesse](../debugger/debug-multiple-processes.md) Erläutert das Debuggen mehrerer Prozesse.

 Gewusst [wie: Verwenden des Fensters "Threads](../debugger/how-to-use-the-threads-window.md) " Nützliche Verfahren zum Debuggen von Threads mit dem Fenster **Threads** .

 Gewusst [wie: Wechseln zu einem anderen Thread während des Debuggens](../debugger/how-to-switch-to-another-thread-while-debugging.md) Drei Möglichkeiten, den debuggingkontext zu einem anderen Thread zu wechseln.

 Gewusst [wie: markieren und Aufheben der Flag von Threads](../debugger/how-to-flag-and-unflag-threads.md) Markieren oder markieren Sie Threads, die beim Debuggen besonders beachtet werden sollen.

 Gewusst [wie: Festlegen eines Thread namens in nativem Code](../debugger/how-to-set-a-thread-name-in-native-code.md) Benennen Sie Ihren Thread, den Sie im Fenster **Threads** anzeigen.

 Gewusst [wie: Festlegen eines Thread namens in verwaltetem Code](../debugger/how-to-set-a-thread-name-in-managed-code.md) Benennen Sie Ihren Thread, den Sie im Fenster **Threads** anzeigen.

 Exemplarische Vorgehensweise [: Debuggen einer Multithread-Anwendung](../debugger/walkthrough-debugging-a-multithreaded-application.md).
Eine Einführung in die Features für das Threaddebuggen, wobei der Schwerpunkt auf den Gewusst wie-Features von [!INCLUDE[vs_orcas_long](../includes/vs-orcas-long-md.md)] liegt.

 Gewusst [wie: Debuggen in einem Hochleistungs Cluster](../debugger/how-to-debug-on-a-high-performance-cluster.md) Techniken zum Debuggen einer Anwendung, die in einem Hochleistungs Cluster ausgeführt wird.

 [Tipps zum Debuggen von Threads in nativem Code](../debugger/tips-for-debugging-threads-in-native-code.md) Einfache Techniken, die für das Debuggen nativer Threads nützlich sein können.

 [Verwenden des Fensters "Aufgaben](../debugger/using-the-tasks-window.md) " Zeigt eine Liste aller verwalteten oder nativen Aufgaben Objekte einschließlich ihres Status und anderer nützlicher Informationen an.

 [Verwenden des Fensters "parallele Stapel](../debugger/using-the-parallel-stacks-window.md) " Zeigt Aufruf Listen mehrerer Threads (oder Aufgaben) in einer einzelnen Ansicht an und fügt auch Stapel Segmente zusammen, die in den Threads (oder Aufgaben) häufig vorkommen.

 Exemplarische Vorgehensweise [: Debuggen einer parallelen Anwendung](../debugger/walkthrough-debugging-a-parallel-application.md) Exemplarische Vorgehensweise, die zeigt, wie die Fenster parallele Aufgaben und parallele Stapel verwendet werden.

 Gewusst [wie: Verwenden des parallelen Überwachungs Fensters](../debugger/how-to-use-the-parallel-watch-window.md) Überprüfen Sie die Werte und Ausdrücke über mehrere Threads hinweg.

 Gewusst [wie: Verwenden des Fensters "GPU-Threads](../debugger/how-to-use-the-gpu-threads-window.md) " Untersuchen und arbeiten Sie Threads, die während des Debuggens auf der GPU ausgeführt werden.

## <a name="related-sections"></a>Verwandte Abschnitte

[Verwenden von Haltepunkten](../debugger/using-breakpoints.md)
- Verwenden Sie Haltepunktfilter, wenn ein Haltepunkt in einem einzelnen Thread platziert werden soll.

- Ablaufverfolgungspunkte ermöglichen es Ihnen, die Ausführung des Programms ohne Unterbrechung zu verfolgen. Dies kann beim Untersuchen von Problemen wie Deadlocks hilfreich sein.

  [Threading](https://msdn.microsoft.com/library/7b46a7d9-c6f1-46d1-a947-ae97471bba87) Threading Konzepte in der [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] Programmierung, einschließlich Beispielcode.

  [Multithreading in Komponenten](https://msdn.microsoft.com/library/2fc31e68-fb71-4544-b654-0ce720478779) Verwendung von Multithreading in- [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] Komponenten.

  [Multithreading-Unterstützung für älteren Code (Visual C++)](https://msdn.microsoft.com/library/24425b1f-5031-4c6b-aac7-017115a40e7c) Threading Konzepte und Beispielcode für C++-Programmierer, die MFC verwenden.

## <a name="see-also"></a>Weitere Informationen
 [Debuggen von Threads und verarbeiten](../debugger/debug-threads-and-processes.md) von [Remote Debugging](../debugger/remote-debugging.md)
