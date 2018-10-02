---
title: Debuggen von Multithreadanwendungen in Visual Studio | Microsoft-Dokumentation
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
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
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: ff0030baec409ae54dc5ebb219f5419e583a0efd
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/22/2018
ms.locfileid: "47521768"
---
# <a name="debug-multithreaded-applications-in-visual-studio"></a>Debuggen von Multithreadanwendungen in Visual Studio
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Die neueste Version dieses Themas finden Sie unter [Debuggen von Multithreadanwendungen in Visual Studio](https://docs.microsoft.com/visualstudio/debugger/debug-multithreaded-applications-in-visual-studio).  
  
Ein Thread ist eine Folge von Anweisungen, für die das Betriebssystem Prozessorzeit reserviert. Jeder Prozess, der im Betriebssystem ausgeführt wird, umfasst mindestens einen Thread. Prozesse, die über mehr als einen Thread verfügen, werden als Multithreadprozesse bezeichnet.  
  
 Auf Computern mit mehreren Prozessoren, Mehrkernprozessoren oder Hyperthreadingprozessen können mehrere Threads gleichzeitig ausgeführt werden. Die parallele Verarbeitung mehrerer Threads kann sich äußerst positiv auf die Programmleistung auswirken, andererseits aber auch das Debuggen erschweren, da in diesem Fall mehrere Threads verfolgt werden müssen.  
  
 Außerdem werden durch das Multithreading neue potenzielle Fehlertypen eingeführt. Beispielsweise müssen zwei oder mehr Threads häufig auf dieselbe Ressource zugreifen, während jeweils nur ein Thread sicher auf die Ressource zugreifen kann. Um sicherzustellen, dass immer nur ein Thread auf die Ressource zugreifen kann, ist eine Form des gegenseitigen Ausschlusses erforderlich. Wenn gegenseitiger Ausschluss nicht ordnungsgemäß ausgeführt wird, können sie erstellen eine *Deadlock* Bedingung, der kein Thread ausgeführt werden kann. Deadlocks können beim Debuggen ein besonders schwerwiegendes Problem verursachen.  
  
 Visual Studio bietet eine **Threads** Fenster, ein GPU-Threadfenster, ein Fenster für parallele Überwachung und andere Funktionen, die Multithreaddebuggen erleichtern. Es wird empfohlen, sich mithilfe der exemplarischen Vorgehensweise mit den Threading-Funktionen vertraut zu machen. Finden Sie unter [Exemplarische Vorgehensweise: Debuggen einer Multithreadanwendung](../debugger/walkthrough-debugging-a-multithreaded-application.md) und [Exemplarische Vorgehensweise: Debuggen einer C++ AMP-Anwendung](http://msdn.microsoft.com/library/40e92ecc-f6ba-411c-960c-b3047b854fb5).  
  
 Visual Studio stellt auch leistungsstarke Halte- und Ablaufverfolgungspunkte bereit, die beim Debuggen von Multithreadanwendungen sehr hilfreich sein können. Um Haltepunkte in einzelnen Threads zu platzieren, können Sie Haltepunktfilter verwenden. Finden Sie unter [Verwenden von Haltepunkten](../debugger/using-breakpoints.md)  
  
 Das Debuggen einer Multithreadanwendung mit einer Benutzeroberfläche kann besonders schwierig sein. In diesem Fall könnten Sie erwägen, die Anwendung auf einem zweiten Computer auszuführen und das Remotedebuggen zu verwenden. Weitere Informationen finden Sie unter [Remotedebuggen](../debugger/remote-debugging.md).  
  
## <a name="in-this-section"></a>In diesem Abschnitt  
 [Debuggen von Threads und Prozessen](../debugger/debug-threads-and-processes.md)  
 Erläutert die Grundlagen des Debuggens von Threads und Prozessen.  
  
 [Debuggen mehrerer Prozesse](../debugger/debug-multiple-processes.md)  
 Erläutert das Debuggen mehrerer Prozesse.  
  
 [Gewusst wie: Verwenden des Fensters „Threads“](../debugger/how-to-use-the-threads-window.md)  
 Nützliche Verfahren zum Debuggen von Threads mit der **Threads** Fenster.  
  
 [Gewusst wie: Wechseln zu einem anderen Thread während des Debuggings](../debugger/how-to-switch-to-another-thread-while-debugging.md)  
 Drei Möglichkeiten, um mit dem Debugkontext zu einem anderen Thread zu wechseln.  
  
 [Gewusst wie: Kennzeichnen von Threads und Aufheben der Kennzeichnung](../debugger/how-to-flag-and-unflag-threads.md)  
 Markieren oder Kennzeichnen von Threads, die beim Debuggen besondere Aufmerksamkeit erhalten sollen.  
  
 [Gewusst wie: Festlegen eines Threadnamens in nativem Code](../debugger/how-to-set-a-thread-name-in-native-code.md)  
 Benennen Sie Ihr Thread in der angezeigten der **Threads** Fenster.  
  
 [Gewusst wie: Festlegen eines Threadnamens in verwaltetem Code](../debugger/how-to-set-a-thread-name-in-managed-code.md)  
 Benennen Sie Ihr Thread in der angezeigten der **Threads** Fenster.  
  
 [Exemplarische Vorgehensweise: Debuggen einer Multithreadanwendung](../debugger/walkthrough-debugging-a-multithreaded-application.md).  
 Eine Einführung in die Features für das Threaddebuggen, wobei der Schwerpunkt auf den Gewusst wie-Features von [!INCLUDE[vs_orcas_long](../includes/vs-orcas-long-md.md)] liegt.  
  
 [Gewusst wie: Debuggen eines Hochleistungsclusters](../debugger/how-to-debug-on-a-high-performance-cluster.md)  
 Techniken zum Debuggen einer Anwendung, die auf einem Hochleistungscluster ausgeführt wird.  
  
 [Tipps zum Debuggen von Threads in nativem Code](../debugger/tips-for-debugging-threads-in-native-code.md)  
 Einfache Techniken, die beim Debuggen systemeigener Threads hilfreich sein können.  
  
 [Verwenden des Fensters „Aufgaben“](../debugger/using-the-tasks-window.md)  
 Zeigt eine Liste aller verwalteten oder nativen Aufgabenobjekte einschließlich ihres Status und anderer nützlicher Informationen an.  
  
 [Verwenden des Fensters "Parallele Stapel"](../debugger/using-the-parallel-stacks-window.md)  
 Zeigt Aufruflisten von mehreren Threads (oder Aufgaben) in einer einzelnen Ansicht an. Außerdem werden Stapelsegmente verbunden, die in allen Threads (oder Aufgaben) verwendet werden.  
  
 [Exemplarische Vorgehensweise: Debuggen einer parallelen Anwendung](../debugger/walkthrough-debugging-a-parallel-application.md)  
 Exemplarische Vorgehensweise, in der erläutert wird, wie die Fenster Parallele Aufgaben und Parallele Stapel verwendet werden.  
  
 [Gewusst wie: Verwenden des parallelen Überwachungsfensters](../debugger/how-to-use-the-parallel-watch-window.md)  
 Überprüfen Sie die Werte und Ausdrücke über mehrere Threads hinweg.  
  
 [Gewusst wie: Verwenden des Fensters „GPU-Threads“](../debugger/how-to-use-the-gpu-threads-window.md)  
 Überprüfen und verwenden Sie Threads, die während des Debuggens im Grafikprozessor (Graphics Processing Unit, GPU) ausgeführt werden.  
  
## <a name="related-sections"></a>Verwandte Abschnitte  
 [Verwenden von Haltepunkten](../debugger/using-breakpoints.md)  
 -   Verwenden Sie Haltepunktfilter, wenn ein Haltepunkt in einem einzelnen Thread platziert werden soll.  
  
-   Ablaufverfolgungspunkte ermöglichen es Ihnen, die Ausführung des Programms ohne Unterbrechung zu verfolgen. Dies kann beim Untersuchen von Problemen wie Deadlocks hilfreich sein.  
  
 [Threading](http://msdn.microsoft.com/library/7b46a7d9-c6f1-46d1-a947-ae97471bba87)  
 Threadingbegriffe in der [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)]-Programmierung, einschließlich Beispielcode.  
  
 [Multithreading in Komponenten](http://msdn.microsoft.com/library/2fc31e68-fb71-4544-b654-0ce720478779)  
 Erläutert die Verwendung des Multithreadings in [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)]-Komponenten.  
  
 [Multithreadingunterstützung für älteren Code (Visual C++)](http://msdn.microsoft.com/library/24425b1f-5031-4c6b-aac7-017115a40e7c)  
 Threadingbegriffe und Beispielcode für C++-Programmierer, die MFC verwenden.  
  
## <a name="see-also"></a>Siehe auch  
 [Debuggen von Threads und Prozessen](../debugger/debug-threads-and-processes.md)   
 [Remotedebuggen](../debugger/remote-debugging.md)



