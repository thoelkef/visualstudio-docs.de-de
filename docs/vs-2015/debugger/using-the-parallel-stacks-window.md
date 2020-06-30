---
title: Verwenden des Fensters "parallele Stapel" | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.debug.parallelstacks
dev_langs:
- FSharp
- VB
- CSharp
- C++
helpviewer_keywords:
- debugger, parallel tasks window
ms.assetid: f50efb78-5206-4803-bb42-426ef8133f2f
caps.latest.revision: 22
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: e89125c8e1dea25ab02fe64c21b8166e9d65194a
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/30/2020
ms.locfileid: "85542219"
---
# <a name="using-the-parallel-stacks-window"></a>Verwenden des Fensters "Parallele Stapel"
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Das Fenster **parallele Stapel** ist nützlich, wenn Sie Multithreadanwendungen Debuggen. In der Thread Ansicht werden die Informationen zu den **Ansichts** Stapeln für alle Threads in der Anwendung angezeigt. Im Fenster können Sie zwischen Threads und Stapelrahmen in diesen Threads navigieren. In verwaltetem Code werden in der **Aufgaben Ansicht** Aufruf Listen von <xref:System.Threading.Tasks.Task?displayProperty=fullName> Objekten angezeigt. In nativem Code werden in der **Aufgaben Ansicht** Aufruf Listen von Aufgaben [Gruppen](https://msdn.microsoft.com/library/42f05ac3-2098-494a-ba84-737fcdcad077), [parallelen Algorithmen](https://msdn.microsoft.com/library/045dca7b-4d73-4558-a44c-383b88a28473), [asynchronen Agents](https://msdn.microsoft.com/library/6cf6ccc6-87f1-4e14-af15-ea8ba58fef1a)und [Lightweight-Tasks](https://msdn.microsoft.com/library/9aba278c-e0c9-4ede-b7c6-fedf7a365d90)angezeigt.  
  
## <a name="threads-view"></a>Threadansicht  
 In der folgenden Abbildung wird ein Thread dargestellt, der vom Hauptthread zu A und zu B und anschließend zu externem Code gewechselt ist. Zwei andere Threads starteten in externem Code und wechselten zu A. Einer der Threads fuhr jedoch mit B und anschließend mit externem Code fort, während der andere Thread mit C und dann mit einer AnonymousMethod fortfuhr.  
  
 ![Ansicht „Threads“ im Fenster „Parallele Stapel“](../debugger/media/parallel-stacksthread.png "Parallel_StacksThread")  
  
 In der Abbildung wird der Aufrufpfad des aktuellen Threads blau hervorgehoben, und der aktive Stapelrahmen wird durch den gelben Pfeil angegeben. Sie können den aktuellen Stapel Rahmen ändern, indem Sie eine andere Methode im Fenster **parallele Stapel** auswählen. Dies kann auch zu einem Wechsel des aktuellen Threads führen, je nachdem, ob die ausgewählte Methode bereits zum aktuellen Threads oder zu einem anderen Thread gehört. In der folgenden Tabelle werden die Hauptfunktionen des Fensters **parallele Stapel** beschrieben, wie in der Abbildung dargestellt.  
  
|Legendenbuchstabe|Elementname|BESCHREIBUNG|  
|--------------------|------------------|-----------------|  
|Ein|Aufruflistensegment oder -knoten|Enthält eine Reihe von Methodenkontexten für einen oder mehrere Threads. Wenn mit dem Knoten keine Pfeillinien verbunden sind, stellt er den gesamten Aufrufpfad für den Thread bzw. die Threads dar.|  
|B|Blaue Hervorhebung|Gibt den Aufrufpfad des aktuellen Threads an.|  
|C|Pfeillinien|Diese verbinden Knoten, um den gesamten Aufrufpfad für den Thread bzw. die Threads darzustellen.|  
|D|QuickInfo zum Knotenheader|Zeigt die ID sowie den benutzerdefinierten Namen der einzelnen Threads an, deren Aufrufpfad diesen Knoten enthält.|  
|E|Methodenkontext|Stellt einen oder mehrere Stapelrahmen in derselben Methode dar.|  
|F|QuickInfo zum Methodenkontext|In der Thread Ansicht werden alle Threads in einer Tabelle ähnlich wie im Fenster **Threads** angezeigt. In der Aufgaben Ansicht werden alle Aufgaben in einer Tabelle ähnlich wie im Fenster **parallele Aufgaben** angezeigt.|  
  
 Außerdem wird im Fenster parallele Stapel das Symbol für die **Augen Ansicht eines Vogels** im Hauptbereich angezeigt, wenn das Diagramm zu groß ist, um in das Fenster zu passen. Sie können auf das Symbol klicken, um das ganze Diagramm im Fenster zu sehen.  
  
## <a name="method-context-icons"></a>Methodenkontextsymbole  
 In der folgenden Tabelle werden die Symbole beschrieben, die Informationen zu aktiven Stapelrahmen und zum aktuellen Stapelrahmen liefern:  
  
|Symbol|Beschreibung|  
|-|-|
|![Parallele Stapel - Gelber Pfeil](../debugger/media/icon-parallelyellowarrow.gif "Icon_ParallelYellowArrow")|Gibt an, dass der Methodenkontext den aktiven Stapelrahmen des aktuellen Threads enthält.|  
|![Parallele Stapel - Threads-Symbol](../debugger/media/icon-parallelthreads.gif "Icon_ParallelThreads")|Gibt an, dass der Methodenkontext den aktiven Stapelrahmen eines nicht-aktuellen Threads enthält.|  
|![Parallele Stapel - Grüner Pfeil](../debugger/media/icon-parallelgreenarrow.gif "Icon_ParallelGreenArrow")|Gibt an, dass der Methodenkontext den aktuellen Stapelrahmen enthält. Dieser Methodenname ist in allen Knoten fett formatiert, in denen er angezeigt wird.|  
  
## <a name="toolbar-controls"></a>Symbolleisten-Steuerelemente  
 In der folgenden Abbildung und der Tabelle werden die verfügbaren Steuerelemente auf der Symbolleiste Parallele Stapel beschrieben.  
  
 ![Symbolleiste im Fenster "Parallele Stapel"](../debugger/media/parallel-stackstoolbar.png "Parallel_StacksToolbar")  
  
|Legendenbuchstabe|Control|BESCHREIBUNG|  
|--------------------|-------------|-----------------|  
|Ein|Kombinationsfeld Threads/Aufgaben|Schaltet die Ansicht zwischen Aufruflisten von Threads und Aufruflisten von Aufgaben um. Weitere Informationen finden Sie unter Aufgabenansicht und Threadansicht.|  
|B|Nur gekennzeichnete Elemente anzeigen|Zeigt Aufruf Listen nur für die Threads an, die in anderen Debugfenstern gekennzeichnet sind, z. b. im Fenster **GPU-Threads** und im Fenster **parallele Überwachung** .|  
|C|Methodenansicht ein- bzw. ausschalten|Wechselt zwischen Stapelansicht und Methodenansicht. Weitere Informationen finden Sie unter Methodenansicht.|  
|D|Automatischen Bildlauf zu aktuellem Stapelrahmen durchführen|Führt einen automatischen Bildlauf durch das Diagramm aus, sodass der aktuelle Stapelrahmen angezeigt wird. Diese Funktion ist hilfreich beim Ändern des aktuellen Stapelrahmens aus anderen Fenstern oder beim Erreichen eines neuen Haltepunkts in großen Diagrammen.|  
|E|Zoomsteuerung ein- bzw. ausschalten|Blendet die Zoomsteuerung ein oder aus. Sie können auch vergrößern, indem Sie die STRG-Taste gedrückt halten und das Mausrad unabhängig von der Sichtbarkeit des Zoom Steuer Elements drücken, oder indem Sie **STRG + UMSCHALT + "+"** drücken, um die Tastenkombination zu vergrößern und **STRG + UMSCHALT + "-"** zu vergrößern. Durch Drücken von **STRG + F8** wird der Bildschirm angepasst.|  
  
### <a name="context-menu-items"></a>Elemente des Kontextmenüs  
 In der folgenden Abbildung und der Tabelle werden die verfügbaren Kontextmenüelemente beschrieben. Das Kontextmenü wird aufgerufen, wenn Sie in der Threadansicht oder in der Aufgabenansicht mit der rechten Maustaste auf einen Methodenkontext klicken. Die letzten sechs Elemente sind direkt aus dem Fenster Aufrufliste übernommen, und sie weisen kein neues Verhalten auf.  
  
 ![Kontextmenü im Fenster "Parallele Stapel"](../debugger/media/parallel-contmenu.png "Parallel_ContMenu")  
  
|Menübefehl|BESCHREIBUNG|  
|---------------|-----------------|  
|Flag|Kennzeichnet das ausgewählte Element.|  
|Kennzeichnung aufheben|Hebt die Kennzeichnung des ausgewählten Elements auf.|  
|Freeze|Friert das ausgewählte Element ein.|  
|Reaktivieren|Reaktiviert das ausgewählte Element.|  
|Zu Aufgabe wechseln (Zu Thread wechseln)|Führt dieselbe Funktion wie das Kombinationsfeld auf der Symbolleiste aus, dabei bleibt jedoch derselbe Stapelrahmen hervorgehoben.|  
|Gehe zu Quellcode|Navigiert zu der Position im Quellcode, die dem Stapelrahmen entspricht, auf den der Benutzer mit der rechten Maustaste geklickt hat.|  
|Zu Rahmen wechseln|Identisch mit dem entsprechenden Menübefehl im Fenster Aufrufliste. Bei Parallele Stapel dürfen jedoch mehrere Frames einem Methodenkontext entsprechen. Daher weist das Menüelement Untermenüs auf, von denen jedes einen bestimmten Stapelrahmen darstellt. Wenn sich einer der Stapelrahmen im aktuellen Thread befindet, wird das Menü ausgewählt, das diesem Stapelrahmen entspricht.|  
|Gehe zu Disassembly|Navigiert zu der Position im Disassemblyfenster, die dem Stapelrahmen entspricht, auf den der Benutzer mit der rechten Maustaste geklickt hat.|  
|Externen Code anzeigen|Blendet externen Code ein bzw. aus.|  
|Hexadezimale Anzeige|Schaltet zwischen dezimaler und hexadezimaler Anzeige um.|  
|Symbolladeinformationen|Zeigt das entsprechende Dialogfeld an.|  
|Symboleinstellungen|Zeigt das entsprechende Dialogfeld an.|  
  
## <a name="tasks-view"></a>Aufgabenansicht  
 Wenn die Anwendung- <xref:System.Threading.Tasks.Task?displayProperty=fullName> Objekte (verwalteter Code) oder- `task_handle` Objekte (nativer Code) zum Ausdrücken von Parallelität verwendet, können Sie das Kombinations Feld auf der Symbolleiste des Fensters parallele Stapel verwenden, um zur *Aufgaben Ansicht*zu wechseln. In der Aufgabenansicht werden Aufruflisten von Aufgaben anstatt von Threads angezeigt. Die Aufgabenansicht unterscheidet sich von der Threadansicht wie folgt:  
  
- Aufruflisten von Threads, die keine Aufgaben ausführen, werden nicht angezeigt.  
  
- Aufruflisten von Threads, die Aufgaben ausführen, sind oben und unten abgeschnitten, um die Frames anzuzeigen, die für die Aufgabe die größte Relevanz besitzen.  
  
- Wenn sich mehrere Aufgaben in einem Thread befinden, werden die Aufruflisten dieser Aufgaben auf separate Knoten aufgeteilt.  
  
  In der folgenden Abbildung wird rechts die Aufgabenansicht von Parallele Stapel angezeigt, und auf der linken Seite ist die entsprechende Threadansicht dargestellt.  
  
  ![Ansicht „Aufgaben“ im Fenster „Parallele Stapel“](../debugger/media/parallel-tasksview.png "Parallel_TasksView")  
  
  Um die gesamte aufrufsstapel anzuzeigen, wechseln Sie einfach zur Thread Ansicht zurück, indem Sie mit der rechten Maustaste auf einen Stapel Rahmen klicken und dann **auf zu Thread**wechseln klicken.  
  
  Wie bereits in der obigen Tabelle erläutert, können Sie weitere Informationen aufrufen, indem Sie mit dem Mauszeiger auf einen Methodenkontext zeigen. In der folgenden Abbildung werden die Informationen in der QuickInfo für die Threadansicht und die Aufgabenansicht dargestellt.  
  
  ![QuickInfo im Fenster "Parallele Stapel"](../debugger/media/parallel-stack-tooltips.png "Parallel_Stack_Tooltips")  
  
## <a name="method-view"></a>Methodenansicht  
 Sowohl in der Threadansicht als auch in der Aufgabenansicht können Sie das Diagramm zur aktuellen Methode pivotieren, indem Sie auf der Symbolleiste auf das Symbol Methodenansicht klicken. In der Methodenansicht sind auf einen Blick alle Methoden für sämtliche Threads angezeigt, die entweder Aufrufer oder Aufgerufene der aktuellen Methode sind. Die folgende Abbildung zeigt eine Threadansicht. Zudem wird veranschaulicht, wie dieselben Informationen in der Methodenansicht dargestellt werden.  
  
 ![Methodenansicht im Fenster „Parallele Stapel“](../debugger/media/parallel-methodview.png "Parallel_MethodView")  
  
 Durch das Wechseln in einen neuen Stapelrahmen legen Sie diese Methode als aktuelle Methode fest, und im Fenster werden alle Aufrufer und Aufgerufenen für die neue Methode angezeigt. Dabei werden möglicherweise einige Threads in der Ansicht eingeblendet oder ausgeblendet, je nachdem, ob die betreffende Methode in ihren Aufruflisten enthalten ist. Wenn Sie in die Stapelansicht zurückwechseln möchten, klicken Sie erneut auf die Symbolleistenschaltfläche Methodenansicht.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Exemplarische Vorgehensweise: Debuggen einer parallelen Anwendung](../debugger/walkthrough-debugging-a-parallel-application.md)   
 [Debugger-Grundlagen](../debugger/debugger-basics.md)   
 [Debugging von verwaltetem Code](../debugger/debugging-managed-code.md)   
 [Parallele Programmierung](https://msdn.microsoft.com/library/4d83c690-ad2d-489e-a2e0-b85b898a672d)   
 [Verwenden des Fensters "Aufgaben"](../debugger/using-the-tasks-window.md)   
 [Exemplarische Vorgehensweise: Debuggen einer parallelen Anwendung](../debugger/walkthrough-debugging-a-parallel-application.md)   
 [Task-Klasse](../extensibility/debugger/task-class-internal-members.md)
