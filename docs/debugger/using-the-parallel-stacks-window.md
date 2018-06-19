---
title: Anzeigen von Threads, die das Fenster "Parallele Stapel" mit | Microsoft Docs
ms.custom: ''
ms.date: 04/25/2017
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.debug.parallelstacks
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- debugger, parallel tasks window
ms.assetid: f50efb78-5206-4803-bb42-426ef8133f2f
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: d19e39ef16bddce9910a65c6833e79d9263fba97
ms.sourcegitcommit: 3d10b93eb5b326639f3e5c19b9e6a8d1ba078de1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/18/2018
ms.locfileid: "31478290"
---
# <a name="view-threads-and-tasks-using-the-parallel-stacks-window"></a>Threads anzeigen und Aufgaben mit dem Fenster "Parallele Stapel"
Die **parallele Stapel** Fenster ist hilfreich beim Debuggen von Multithreadanwendungen. Die **Threadansicht** werden Aufruflisteninformationen für alle Threads in der Anwendung. Im Fenster können Sie zwischen Threads und Stapelrahmen in diesen Threads navigieren. In verwaltetem Code die **Aufgabenansicht** Aufruflisten von <xref:System.Threading.Tasks.Task?displayProperty=fullName> Objekte. In systemeigenen Code der die **Aufgabenansicht** Aufruflisten von [Aufgabengruppen](/cpp/parallel/concrt/task-parallelism-concurrency-runtime), [parallele Algorithmen](/cpp/parallel/concrt/parallel-algorithms), [asynchrone Agents](/cpp/parallel/concrt/asynchronous-agents), und [einfache Aufgaben](/cpp/parallel/concrt/task-scheduler-concurrency-runtime).  
  
## <a name="threads-view"></a>Threadansicht  
 In der folgenden Abbildung wird ein Thread dargestellt, der vom Hauptthread zu A und zu B und anschließend zu externem Code gewechselt ist. Zwei andere Threads starteten in externem Code und wechselten zu A. Einer der Threads fuhr jedoch mit B und anschließend mit externem Code fort, während der andere Thread mit C und dann mit einer AnonymousMethod fortfuhr.  
  
 ![Threadansicht im Fenster "Parallele Stapel"](../debugger/media/parallel_stacksthread.png "Parallel_StacksThread")  
  
 In der Abbildung wird der Aufrufpfad des aktuellen Threads blau hervorgehoben, und die aktuelle Position (aktiven Stapelrahmen) des Threads wird durch den gelben Pfeil gekennzeichnet. Sie können den aktuellen Stapelrahmen ändern, indem Sie in eine andere Methode auswählen der **parallele Stapel** Fenster. Dies kann auch zu einem Wechsel des aktuellen Threads führen, je nachdem, ob die ausgewählte Methode bereits zum aktuellen Threads oder zu einem anderen Thread gehört. Die folgende Tabelle beschreibt die wichtigsten Funktionen von der **parallele Stapel** wie in der Abbildung gezeigt.  
  
|Legendenbuchstabe|Elementname|Beschreibung|  
|--------------------|------------------|-----------------|  
|A|Aufruflistensegment oder -knoten|Enthält eine Reihe von Methoden für einen oder mehrere Threads. Wenn mit dem Knoten keine Pfeillinien verbunden sind, stellt er den gesamten Aufrufpfad für den Thread bzw. die Threads dar.|  
|B|Blaue Hervorhebung|Gibt den Aufrufpfad des aktuellen Threads an.|  
|C|Pfeillinien|Diese verbinden Knoten, um den gesamten Aufrufpfad für den Thread bzw. die Threads darzustellen.|  
|D|QuickInfo zum Knotenheader|Zeigt die ID sowie den benutzerdefinierten Namen der einzelnen Threads an, deren Aufrufpfad diesen Knoten enthält.|  
|E|Methode|Stellt einen oder mehrere Stapelrahmen in derselben Methode dar.|  
|F|QuickInfo für die Methode|In der Threadansicht werden alle Threads in einer Tabelle ähnlich wie die **Threads** Fenster. In der Aufgabenansicht werden alle Aufgaben in einer Tabelle ähnlich wie auf die **Aufgaben** Fenster.|  
  
 Darüber hinaus wird gezeigt, das Fenster "Parallele Stapel" eine **Vogelperspektive** Symbol im Hauptbereich, wenn das Diagramm zu groß, um in das Fenster zu passen. Sie können auf das Symbol klicken, um das ganze Diagramm im Fenster zu sehen.  
  
## <a name="stack-frame-icons"></a>Stack-Frame-Symbole  
 In der folgenden Tabelle werden die Symbole beschrieben, die Informationen zu aktiven Stapelrahmen und zum aktuellen Stapelrahmen liefern:  
  
|||  
|-|-|  
|Symbol|Beschreibung|  
|![Parallele Stapel-gelben Pfeil](../debugger/media/icon_parallelyellowarrow.gif "Icon_ParallelYellowArrow")|Gibt an, dass die Methode den aktuellen Speicherort (aktiven Stapelrahmen) des aktuellen Threads enthält.|  
|![Parallele Stapel-Threads-Symbol](../debugger/media/icon_parallelthreads.gif "Icon_ParallelThreads")|Gibt an, dass die Methode den aktuellen Speicherort (aktiven Stapelrahmen) eines nicht-aktuellen Threads enthält.|  
|![Parallele Stapel-grünen Pfeil](../debugger/media/icon_parallelgreenarrow.gif "Icon_ParallelGreenArrow")|Gibt an, dass die Methode den aktuellen Stapelrahmen (der aktuelle Debuggerkontext) enthält. Dieser Methodenname ist in allen Knoten fett formatiert, in denen er angezeigt wird.|  
  
## <a name="toolbar-controls"></a>Symbolleisten-Steuerelemente  
 In der folgenden Abbildung und der Tabelle werden die verfügbaren Steuerelemente auf der Symbolleiste Parallele Stapel beschrieben.  
  
 ![Symbolleiste im Fenster "Parallele Stapel"](../debugger/media/parallel_stackstoolbar.png "Parallel_StacksToolbar")  
  
|Legendenbuchstabe|Steuerelement|Beschreibung|  
|--------------------|-------------|-----------------|  
|A|Kombinationsfeld Threads/Aufgaben|Schaltet die Ansicht zwischen Aufruflisten von Threads und Aufruflisten von Aufgaben um. Weitere Informationen finden Sie unter Aufgabenansicht und Threadansicht.|  
|B|Nur gekennzeichnete Elemente anzeigen|Zeigt Aufruflisten nur für die Threads, die in anderen Debug-Fenster, z. B. gekennzeichnet sind die **GPU-Threads** Fenster und die **parallele Überwachung** Fenster.|  
|C|Methodenansicht ein- bzw. ausschalten|Wechselt zwischen Stapelansicht und Methodenansicht. Weitere Informationen finden Sie unter Methodenansicht.|  
|D|Automatischen Bildlauf zu aktuellem Stapelrahmen durchführen|Führt einen automatischen Bildlauf durch das Diagramm aus, sodass der aktuelle Stapelrahmen angezeigt wird. Diese Funktion ist hilfreich beim Ändern des aktuellen Stapelrahmens aus anderen Fenstern oder beim Erreichen eines neuen Haltepunkts in großen Diagrammen.|  
|E|Zoomsteuerung ein- bzw. ausschalten|Blendet die Zoomsteuerung ein oder aus. Sie können auch vergrößern STRG gedrückt, und aktivieren das Mausrad, unabhängig von der Sichtbarkeit der zoomsteuerung, oder mithilfe von STRG + UMSCHALT + '+', um zu vergrößern und STRG + UMSCHALT + "-" zu verkleinern. Drücken Sie STRG + F8 wird vergrößert, um den Bildschirm zu passen.|  
  
### <a name="context-menu-items"></a>Elemente des Kontextmenüs  
 Die folgende Abbildung und Tabelle beschreiben die Kontextmenü wird aufgerufen, die verfügbar sind, wenn Sie eine Methode in der Threadansicht oder Aufgabenansicht mit der rechten Maustaste. Die letzten sechs Elemente sind direkt aus dem Fenster Aufrufliste übernommen, und sie weisen kein neues Verhalten auf.  
  
 !["Kontextmenü" im Fenster "Parallele Stapel"](../debugger/media/parallel_contmenu.png "Parallel_ContMenu")  
  
|Menübefehl|Beschreibung|  
|---------------|-----------------|  
|Flag|Kennzeichnet das ausgewählte Element.|  
|Kennzeichnung aufheben|Hebt die Kennzeichnung des ausgewählten Elements auf.|  
|Einfrieren|Friert das ausgewählte Element ein.|  
|Reaktivieren|Reaktiviert das ausgewählte Element.|  
|Zu Aufgabe wechseln (Zu Thread wechseln)|Führt dieselbe Funktion wie das Kombinationsfeld auf der Symbolleiste aus, dabei bleibt jedoch derselbe Stapelrahmen hervorgehoben.|  
|Gehe zu Quellcode|Navigiert zu der Position im Quellcode, die dem Stapelrahmen entspricht, auf den der Benutzer mit der rechten Maustaste geklickt hat.|  
|Zu Rahmen wechseln|Identisch mit dem entsprechenden Menübefehl im Fenster Aufrufliste. Bei Parallele Stapel können jedoch mehrere Frames an eine Methode entsprechen. Daher weist das Menüelement Untermenüs auf, von denen jedes einen bestimmten Stapelrahmen darstellt. Wenn sich einer der Stapelrahmen im aktuellen Thread befindet, wird das Menü ausgewählt, das diesem Stapelrahmen entspricht.|  
|Gehe zu Disassembly|Navigiert zu der Position im Disassemblyfenster, die dem Stapelrahmen entspricht, auf den der Benutzer mit der rechten Maustaste geklickt hat.|  
|Externen Code anzeigen|Blendet externen Code ein bzw. aus.|  
|Hexadezimale Anzeige|Schaltet zwischen dezimaler und hexadezimaler Anzeige um.|  
|Symbolladeinformationen|Zeigt das entsprechende Dialogfeld an.|  
|Symboleinstellungen|Zeigt das entsprechende Dialogfeld an.|  
  
## <a name="tasks-view"></a>Aufgabenansicht  
 Wenn die Anwendung Parallelität mit <xref:System.Threading.Tasks.Task?displayProperty=fullName> -Objekten (verwalteter Code) oder `task_handle` -Objekten (nativer Code) ausdrückt, können Sie das Kombinationsfeld auf der Symbolleiste des Fensters Parallele Stapel, wechseln Sie zu *Aufgabenansicht*. In der Aufgabenansicht werden Aufruflisten von Aufgaben anstatt von Threads angezeigt. Die Aufgabenansicht unterscheidet sich von der Threadansicht wie folgt:  
  
-   Aufruflisten von Threads, die keine Aufgaben ausführen, werden nicht angezeigt.  
  
-   Aufruflisten von Threads, die Aufgaben ausführen, sind oben und unten abgeschnitten, um die Frames anzuzeigen, die für die Aufgabe die größte Relevanz besitzen.  
  
-   Wenn sich mehrere Aufgaben in einem Thread befinden, werden die Aufruflisten dieser Aufgaben auf separate Knoten aufgeteilt.  
  
 In der folgenden Abbildung wird rechts die Aufgabenansicht von Parallele Stapel angezeigt, und auf der linken Seite ist die entsprechende Threadansicht dargestellt.  
  
 ![Aufgabenansicht im Fenster "Parallele Stapel"](../debugger/media/parallel_tasksview.png "Parallel_TasksView")  
  
 Um die gesamte Aufrufliste anzuzeigen, wechseln Sie einfach zur Threadansicht zurück, indem Sie mit der rechten Maustaste eines Stapelrahmen entspricht, und klicken Sie dann auf **zu Thread wechseln**.  
  
 Wie in der obigen Tabelle beschrieben, indem Sie mit dem Mauszeiger auf eine Methode können Sie weitere Informationen finden Sie unter. In der folgenden Abbildung werden die Informationen in der QuickInfo für die Threadansicht und die Aufgabenansicht dargestellt.  
  
 ![QuickInfos im Fenster "Parallele Stapel"](../debugger/media/parallel_stack_tooltips.png "Parallel_Stack_Tooltips")  
  
## <a name="method-view"></a>Methodenansicht  
 Sowohl in der Threadansicht als auch in der Aufgabenansicht können Sie das Diagramm zur aktuellen Methode pivotieren, indem Sie auf der Symbolleiste auf das Symbol Methodenansicht klicken. In der Methodenansicht sind auf einen Blick alle Methoden für sämtliche Threads angezeigt, die entweder Aufrufer oder Aufgerufene der aktuellen Methode sind. Die folgende Abbildung zeigt eine Threadansicht. Zudem wird veranschaulicht, wie dieselben Informationen in der Methodenansicht dargestellt werden.  
  
 ![Methodenansicht im Fenster "Parallele Stapel"](../debugger/media/parallel_methodview.png "Parallel_MethodView")  
  
 Durch das Wechseln in einen neuen Stapelrahmen legen Sie diese Methode als aktuelle Methode fest, und im Fenster werden alle Aufrufer und Aufgerufenen für die neue Methode angezeigt. Dabei werden möglicherweise einige Threads in der Ansicht eingeblendet oder ausgeblendet, je nachdem, ob die betreffende Methode in ihren Aufruflisten enthalten ist. Wenn Sie in die Stapelansicht zurückwechseln möchten, klicken Sie erneut auf die Symbolleistenschaltfläche Methodenansicht.  
  
## <a name="see-also"></a>Siehe auch  
 [Erste Schritte zum Debuggen einer Multithread-Tasksequenzausführungsmodul](../debugger/get-started-debugging-multithreaded-apps.md)   
 [Exemplarische Vorgehensweise: Debuggen einer parallelen Anwendung](../debugger/walkthrough-debugging-a-parallel-application.md)   
 [Debugger – Grundlagen](../debugger/debugger-basics.md)   
 [Debuggen von verwaltetem Code](../debugger/debugging-managed-code.md)   
 [Parallele Programmierung](/dotnet/standard/parallel-programming/index)   
 [Verwenden das Fenster "Aufgaben"](../debugger/using-the-tasks-window.md)   
 [Task-Klasse](../extensibility/debugger/task-class-internal-members.md)
