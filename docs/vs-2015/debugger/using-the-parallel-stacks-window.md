---
title: Verwenden die parallele Stapel-Fenster | Microsoft-Dokumentation
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
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
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 353d9a39a299c0803bb4f27843fcae43375105cf
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/12/2018
ms.locfileid: "49182169"
---
# <a name="using-the-parallel-stacks-window"></a>Verwenden des Fensters "Parallele Stapel"
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Die **parallele Stapel** Fenster eignet sich, beim Debuggen von Multithreadanwendungen. Die **Ansicht "Threads"** Aufruflisteninformationen für alle Threads in Ihrer Anwendung. Im Fenster können Sie zwischen Threads und Stapelrahmen in diesen Threads navigieren. In verwaltetem Code der **Aufgabenansicht** Aufruflisten von <xref:System.Threading.Tasks.Task?displayProperty=fullName> Objekte. In nativem Code der **Aufgabenansicht** Aufruflisten von [Aufgabengruppen](http://msdn.microsoft.com/library/42f05ac3-2098-494a-ba84-737fcdcad077), [parallele Algorithmen](http://msdn.microsoft.com/library/045dca7b-4d73-4558-a44c-383b88a28473), [asynchrone Agents](http://msdn.microsoft.com/library/6cf6ccc6-87f1-4e14-af15-ea8ba58fef1a), und [einfache Aufgaben](http://msdn.microsoft.com/library/9aba278c-e0c9-4ede-b7c6-fedf7a365d90).  
  
## <a name="threads-view"></a>Threadansicht  
 In der folgenden Abbildung wird ein Thread dargestellt, der vom Hauptthread zu A und zu B und anschließend zu externem Code gewechselt ist. Zwei andere Threads starteten in externem Code und wechselten zu A. Einer der Threads fuhr jedoch mit B und anschließend mit externem Code fort, während der andere Thread mit C und dann mit einer AnonymousMethod fortfuhr.  
  
 ![Threadansicht im Fenster "Parallele Stapel"](../debugger/media/parallel-stacksthread.png "Parallel_StacksThread")  
  
 In der Abbildung wird der Aufrufpfad des aktuellen Threads blau hervorgehoben, und der aktive Stapelrahmen wird durch den gelben Pfeil angegeben. Sie können den aktuellen Stapelrahmen ändern, indem Sie eine andere Methode im Auswählen der **parallele Stapel** Fenster. Dies kann auch zu einem Wechsel des aktuellen Threads führen, je nachdem, ob die ausgewählte Methode bereits zum aktuellen Threads oder zu einem anderen Thread gehört. Die folgende Tabelle beschreibt die wichtigsten Funktionen des die **parallele Stapel** wie in der Abbildung gezeigt.  
  
|Legendenbuchstabe|Elementname|Beschreibung|  
|--------------------|------------------|-----------------|  
|A|Aufruflistensegment oder -knoten|Enthält eine Reihe von Methodenkontexten für einen oder mehrere Threads. Wenn mit dem Knoten keine Pfeillinien verbunden sind, stellt er den gesamten Aufrufpfad für den Thread bzw. die Threads dar.|  
|B|Blaue Hervorhebung|Gibt den Aufrufpfad des aktuellen Threads an.|  
|C|Pfeillinien|Diese verbinden Knoten, um den gesamten Aufrufpfad für den Thread bzw. die Threads darzustellen.|  
|D|QuickInfo zum Knotenheader|Zeigt die ID sowie den benutzerdefinierten Namen der einzelnen Threads an, deren Aufrufpfad diesen Knoten enthält.|  
|E|Methodenkontext|Stellt einen oder mehrere Stapelrahmen in derselben Methode dar.|  
|F|QuickInfo zum Methodenkontext|In der Threadansicht werden alle Threads in einer Tabelle ähnelt der **Threads** Fenster. In der Aufgabenansicht werden alle Aufgaben in einer Tabelle ähnlich wie auf die **Parallele Aufgaben** Fenster.|  
  
 Darüber hinaus das Fenster "Parallele Stapel" zeigt eine **Vogelperspektive** Symbol im Hauptbereich, wenn das Diagramm zu groß, um ins Fenster passt. Sie können auf das Symbol klicken, um das ganze Diagramm im Fenster zu sehen.  
  
## <a name="method-context-icons"></a>Methodenkontextsymbole  
 In der folgenden Tabelle werden die Symbole beschrieben, die Informationen zu aktiven Stapelrahmen und zum aktuellen Stapelrahmen liefern:  
  
|||  
|-|-|  
|Symbol|Beschreibung|  
|![Parallele Stapel-gelber Pfeil](../debugger/media/icon-parallelyellowarrow.gif "Icon_ParallelYellowArrow")|Gibt an, dass der Methodenkontext den aktiven Stapelrahmen des aktuellen Threads enthält.|  
|![Parallele Stapel-Threads-Symbol](../debugger/media/icon-parallelthreads.gif "Icon_ParallelThreads")|Gibt an, dass der Methodenkontext den aktiven Stapelrahmen eines nicht-aktuellen Threads enthält.|  
|![Parallele Stapel-Grüner Pfeil](../debugger/media/icon-parallelgreenarrow.gif "Icon_ParallelGreenArrow")|Gibt an, dass der Methodenkontext den aktuellen Stapelrahmen enthält. Dieser Methodenname ist in allen Knoten fett formatiert, in denen er angezeigt wird.|  
  
## <a name="toolbar-controls"></a>Symbolleisten-Steuerelemente  
 In der folgenden Abbildung und der Tabelle werden die verfügbaren Steuerelemente auf der Symbolleiste Parallele Stapel beschrieben.  
  
 ![Symbolleiste im Fenster "Parallele Stapel"](../debugger/media/parallel-stackstoolbar.png "Parallel_StacksToolbar")  
  
|Legendenbuchstabe|Steuerelement|Beschreibung|  
|--------------------|-------------|-----------------|  
|A|Kombinationsfeld Threads/Aufgaben|Schaltet die Ansicht zwischen Aufruflisten von Threads und Aufruflisten von Aufgaben um. Weitere Informationen finden Sie unter Aufgabenansicht und Threadansicht.|  
|B|Nur gekennzeichnete Elemente anzeigen|Zeigt nur Aufruflisten für die Threads, die in anderen Debug-Fenster,, z. B. gekennzeichnet sind die **GPU-Threads** Fenster und die **parallele Überwachung** Fenster.|  
|C|Methodenansicht ein- bzw. ausschalten|Wechselt zwischen Stapelansicht und Methodenansicht. Weitere Informationen finden Sie unter Methodenansicht.|  
|D|Automatischen Bildlauf zu aktuellem Stapelrahmen durchführen|Führt einen automatischen Bildlauf durch das Diagramm aus, sodass der aktuelle Stapelrahmen angezeigt wird. Diese Funktion ist hilfreich beim Ändern des aktuellen Stapelrahmens aus anderen Fenstern oder beim Erreichen eines neuen Haltepunkts in großen Diagrammen.|  
|E|Zoomsteuerung ein- bzw. ausschalten|Blendet die Zoomsteuerung ein oder aus. Sie können auch vergrößern, indem Sie STRG-Taste drücken, und aktivieren das Mausrad, unabhängig von der Sichtbarkeit der zoomsteuerung, oder mithilfe von **STRG + UMSCHALT + '+'** zum Verkleinern die Tasten und **STRG + UMSCHALT +'-'** verkleinern. Drücken Sie **STRG + F8** wird vergrößert, um den Bildschirm zu passen.|  
  
### <a name="context-menu-items"></a>Elemente des Kontextmenüs  
 In der folgenden Abbildung und der Tabelle werden die verfügbaren Kontextmenüelemente beschrieben. Das Kontextmenü wird aufgerufen, wenn Sie in der Threadansicht oder in der Aufgabenansicht mit der rechten Maustaste auf einen Methodenkontext klicken. Die letzten sechs Elemente sind direkt aus dem Fenster Aufrufliste übernommen, und sie weisen kein neues Verhalten auf.  
  
 ![Kontextmenü im Fenster "Parallele Stapel"](../debugger/media/parallel-contmenu.png "Parallel_ContMenu")  
  
|Menübefehl|Beschreibung|  
|---------------|-----------------|  
|Flag|Kennzeichnet das ausgewählte Element.|  
|Kennzeichnung aufheben|Hebt die Kennzeichnung des ausgewählten Elements auf.|  
|Einfrieren|Friert das ausgewählte Element ein.|  
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
 Wenn Ihre Anwendung verwendet <xref:System.Threading.Tasks.Task?displayProperty=fullName> -Objekten (verwalteter Code) oder `task_handle` Objekte (nativer Code) ausdrückt, können Sie im Kombinationsfeld, in der Symbolleiste des Fensters Parallele Stapel, wechseln zu *Aufgabenansicht*. In der Aufgabenansicht werden Aufruflisten von Aufgaben anstatt von Threads angezeigt. Die Aufgabenansicht unterscheidet sich von der Threadansicht wie folgt:  
  
-   Aufruflisten von Threads, die keine Aufgaben ausführen, werden nicht angezeigt.  
  
-   Aufruflisten von Threads, die Aufgaben ausführen, sind oben und unten abgeschnitten, um die Frames anzuzeigen, die für die Aufgabe die größte Relevanz besitzen.  
  
-   Wenn sich mehrere Aufgaben in einem Thread befinden, werden die Aufruflisten dieser Aufgaben auf separate Knoten aufgeteilt.  
  
 In der folgenden Abbildung wird rechts die Aufgabenansicht von Parallele Stapel angezeigt, und auf der linken Seite ist die entsprechende Threadansicht dargestellt.  
  
 ![Aufgabenansicht im Fenster "Parallele Stapel"](../debugger/media/parallel-tasksview.png "Parallel_TasksView")  
  
 Um die gesamte Aufrufliste anzuzeigen, wechseln Sie einfach zur Threadansicht zurück durch einen Rechtsklick auf einen Stapelrahmen, und klicken Sie dann auf **zu Thread wechseln**.  
  
 Wie bereits in der obigen Tabelle erläutert, können Sie weitere Informationen aufrufen, indem Sie mit dem Mauszeiger auf einen Methodenkontext zeigen. In der folgenden Abbildung werden die Informationen in der QuickInfo für die Threadansicht und die Aufgabenansicht dargestellt.  
  
 ![QuickInfos im Fenster "Parallele Stapel"](../debugger/media/parallel-stack-tooltips.png "Parallel_Stack_Tooltips")  
  
## <a name="method-view"></a>Methodenansicht  
 Sowohl in der Threadansicht als auch in der Aufgabenansicht können Sie das Diagramm zur aktuellen Methode pivotieren, indem Sie auf der Symbolleiste auf das Symbol Methodenansicht klicken. In der Methodenansicht sind auf einen Blick alle Methoden für sämtliche Threads angezeigt, die entweder Aufrufer oder Aufgerufene der aktuellen Methode sind. Die folgende Abbildung zeigt eine Threadansicht. Zudem wird veranschaulicht, wie dieselben Informationen in der Methodenansicht dargestellt werden.  
  
 ![Methodenansicht im Fenster "Parallele Stapel"](../debugger/media/parallel-methodview.png "Parallel_MethodView")  
  
 Durch das Wechseln in einen neuen Stapelrahmen legen Sie diese Methode als aktuelle Methode fest, und im Fenster werden alle Aufrufer und Aufgerufenen für die neue Methode angezeigt. Dabei werden möglicherweise einige Threads in der Ansicht eingeblendet oder ausgeblendet, je nachdem, ob die betreffende Methode in ihren Aufruflisten enthalten ist. Wenn Sie in die Stapelansicht zurückwechseln möchten, klicken Sie erneut auf die Symbolleistenschaltfläche Methodenansicht.  
  
## <a name="see-also"></a>Siehe auch  
 [Exemplarische Vorgehensweise: Debuggen einer parallelen Anwendung](../debugger/walkthrough-debugging-a-parallel-application.md)   
 [Debugger – Grundlagen](../debugger/debugger-basics.md)   
 [Debuggen von verwaltetem Code](../debugger/debugging-managed-code.md)   
 [Parallele Programmierung](http://msdn.microsoft.com/library/4d83c690-ad2d-489e-a2e0-b85b898a672d)   
 [Verwenden das Fenster "Aufgaben"](../debugger/using-the-tasks-window.md)   
 [Exemplarische Vorgehensweise: Debuggen einer parallelen Anwendung](../debugger/walkthrough-debugging-a-parallel-application.md)   
 [Aufgabenklasse](../extensibility/debugger/task-class-internal-members.md)



