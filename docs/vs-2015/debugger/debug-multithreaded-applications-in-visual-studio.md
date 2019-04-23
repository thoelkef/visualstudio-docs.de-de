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
ms.openlocfilehash: 8315a797aec5fcedbf33df6ca96f41879b57d971
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/22/2019
ms.locfileid: "60054299"
---
# <a name="debug-multithreaded-applications-in-visual-studio"></a>Debuggen von Multithreadanwendungen in Visual Studio
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Ein Thread ist eine Folge von Anweisungen, für die das Betriebssystem Prozessorzeit reserviert. Jeder Prozess, der im Betriebssystem ausgeführt wird, umfasst mindestens einen Thread. Prozesse, die über mehr als einen Thread verfügen, werden als Multithreadprozesse bezeichnet.

 Auf Computern mit mehreren Prozessoren, Mehrkernprozessoren oder Hyperthreadingprozessen können mehrere Threads gleichzeitig ausgeführt werden. Die parallele Verarbeitung mehrerer Threads kann sich äußerst positiv auf die Programmleistung auswirken, andererseits aber auch das Debuggen erschweren, da in diesem Fall mehrere Threads verfolgt werden müssen.

 Außerdem werden durch das Multithreading neue potenzielle Fehlertypen eingeführt. Beispielsweise müssen zwei oder mehr Threads häufig auf dieselbe Ressource zugreifen, während jeweils nur ein Thread sicher auf die Ressource zugreifen kann. Um sicherzustellen, dass immer nur ein Thread auf die Ressource zugreifen kann, ist eine Form des gegenseitigen Ausschlusses erforderlich. Wenn gegenseitiger Ausschluss nicht ordnungsgemäß ausgeführt wird, können sie erstellen eine *Deadlock* Bedingung, der kein Thread ausgeführt werden kann. Deadlocks können beim Debuggen ein besonders schwerwiegendes Problem verursachen.

 Visual Studio bietet eine **Threads** Fenster, ein GPU-Threadfenster, ein Fenster für parallele Überwachung und andere Funktionen, die Multithreaddebuggen erleichtern. Es wird empfohlen, sich mithilfe der exemplarischen Vorgehensweise mit den Threading-Funktionen vertraut zu machen. Weitere Informationen finden Sie unter [Exemplarische Vorgehensweise: Debuggen einer Multithreadanwendung](../debugger/walkthrough-debugging-a-multithreaded-application.md) und [Exemplarische Vorgehensweise: Debuggen einer C++ AMP-Anwendung](http://msdn.microsoft.com/library/40e92ecc-f6ba-411c-960c-b3047b854fb5).

 Visual Studio stellt auch leistungsstarke Halte- und Ablaufverfolgungspunkte bereit, die beim Debuggen von Multithreadanwendungen sehr hilfreich sein können. Um Haltepunkte in einzelnen Threads zu platzieren, können Sie Haltepunktfilter verwenden. Finden Sie unter [Verwenden von Haltepunkten](../debugger/using-breakpoints.md)

 Das Debuggen einer Multithreadanwendung mit einer Benutzeroberfläche kann besonders schwierig sein. In diesem Fall könnten Sie erwägen, die Anwendung auf einem zweiten Computer auszuführen und das Remotedebuggen zu verwenden. Weitere Informationen finden Sie unter [Remotedebuggen](../debugger/remote-debugging.md).

## <a name="in-this-section"></a>In diesem Abschnitt
 [Debuggen von Threads und Prozessen](../debugger/debug-threads-and-processes.md) erläutert die Grundlagen des Debuggens von Threads und Prozessen.

 [Debuggen mehrerer Prozesse](../debugger/debug-multiple-processes.md) wird erläutert, wie mehrere Prozesse debuggen.

 [Vorgehensweise: Verwenden des Fensters Threads](../debugger/how-to-use-the-threads-window.md) nützliche Verfahren zum Debuggen von Threads mit der **Threads** Fenster.

 [Vorgehensweise: Wechseln Sie zu einem anderen Thread beim Debuggen](../debugger/how-to-switch-to-another-thread-while-debugging.md) drei Möglichkeiten, um den Debugkontext zu einem anderen Thread zu wechseln.

 [Vorgehensweise: Flag und Aufheben der Kennzeichnung von Threads](../debugger/how-to-flag-and-unflag-threads.md) markieren oder Kennzeichnen von Threads, die beim Debuggen besondere Aufmerksamkeit werden sollen.

 [Vorgehensweise: Festlegen eines Threadnamens in nativem Code](../debugger/how-to-set-a-thread-name-in-native-code.md) Benennen des Threads, die Sie, in Anzeigen der **Threads** Fenster.

 [Vorgehensweise: Festlegen eines Threadnamens in verwaltetem Code](../debugger/how-to-set-a-thread-name-in-managed-code.md) Benennen des Threads, die Sie, in Anzeigen der **Threads** Fenster.

 [Exemplarische Vorgehensweise: Debuggen einer Multithreadanwendung](../debugger/walkthrough-debugging-a-multithreaded-application.md).
Eine Einführung in die Features für das Threaddebuggen, wobei der Schwerpunkt auf den Gewusst wie-Features von [!INCLUDE[vs_orcas_long](../includes/vs-orcas-long-md.md)] liegt.

 [Vorgehensweise: Debuggen auf einem High-Performance-Cluster](../debugger/how-to-debug-on-a-high-performance-cluster.md) Techniken zum Debuggen einer Anwendung, die auf einem Hochleistungscluster ausgeführt wird.

 [Tipps zum Debuggen von Threads in nativem Code](../debugger/tips-for-debugging-threads-in-native-code.md) einfache Techniken, die für das Debuggen systemeigener Threads hilfreich sein können.

 [Verwenden das Fenster "Aufgaben"](../debugger/using-the-tasks-window.md) zeigt eine Liste aller der verwalteten oder nativen Aufgabenobjekte einschließlich ihres Status und andere nützliche Informationen.

 [Verwenden das Fenster "Parallele Stapel"](../debugger/using-the-parallel-stacks-window.md) zeigt Aufruf Aufruflisten von mehreren Threads (oder Aufgaben) in einer einzigen Ansicht und außerdem werden stapelsegmente, die für die Threads (oder Aufgaben) gelten.

 [Exemplarische Vorgehensweise: Debuggen einer Parallelanwendung](../debugger/walkthrough-debugging-a-parallel-application.md) Exemplarische Vorgehensweise, die wie die Fenster Parallele Aufgaben und parallele Stapel verwendet wird.

 [Vorgehensweise: Verwenden des parallelen Überwachungsfensters](../debugger/how-to-use-the-parallel-watch-window.md) Werte und Ausdrücke über mehrere Threads hinweg zu überprüfen.

 [Vorgehensweise: Verwenden Sie das GPU-Threadfenster](../debugger/how-to-use-the-gpu-threads-window.md) überprüfen und Verwenden von Threads, die während des Debuggens auf dem GPU ausgeführt werden.

## <a name="related-sections"></a>Verwandte Abschnitte

[Verwenden von Haltepunkten](../debugger/using-breakpoints.md)
- Verwenden Sie Haltepunktfilter, wenn ein Haltepunkt in einem einzelnen Thread platziert werden soll.

- Ablaufverfolgungspunkte ermöglichen es Ihnen, die Ausführung des Programms ohne Unterbrechung zu verfolgen. Dies kann beim Untersuchen von Problemen wie Deadlocks hilfreich sein.

  [Threading](http://msdn.microsoft.com/library/7b46a7d9-c6f1-46d1-a947-ae97471bba87) Threadingbegriffe in [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] Programmierung, einschließlich Beispielcode.

  [Multithreading in Komponenten](http://msdn.microsoft.com/library/2fc31e68-fb71-4544-b654-0ce720478779) mit multithreading in [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] Komponenten.

  [Multithreadingunterstützung für älteren Code (Visual C++)](http://msdn.microsoft.com/library/24425b1f-5031-4c6b-aac7-017115a40e7c) Threadingbegriffe und Beispielcode für C++-Programmierer, die unter Verwendung von MFC.

## <a name="see-also"></a>Siehe auch
 [Debuggen von Threads und Prozessen](../debugger/debug-threads-and-processes.md) [Remotedebuggen](../debugger/remote-debugging.md)
