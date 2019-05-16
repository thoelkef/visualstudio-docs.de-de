---
title: Verwenden das Fenster "Aufgaben" | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.debug.paralleltasks
dev_langs:
- FSharp
- VB
- CSharp
- C++
helpviewer_keywords:
- debugger, parallel tasks window
ms.assetid: bd5e0612-a0dc-41cf-a7af-1e87d0d5c35f
caps.latest.revision: 23
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 267a04e0d717bde311423aae7f35fba07ca6f39b
ms.sourcegitcommit: 08fc78516f1107b83f46e2401888df4868bb1e40
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/15/2019
ms.locfileid: "65684034"
---
# <a name="using-the-tasks-window"></a>Verwenden des Fensters "Aufgaben"
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Das Fenster **Aufgaben** ähnelt dem Fenster **Threads**. In diesem Fenster werden jedoch Informationen zu jedem <xref:System.Threading.Tasks.Task?displayProperty=fullName>-, [task_handle](https://msdn.microsoft.com/library/b4af5b28-227d-4488-8194-0a0d039173b7)- oder [WinJS.Promise](https://msdn.microsoft.com/library/windows/apps/br211867.aspx)-Objekt anstatt für die einzelnen Threads angezeigt. Wie Threads stellen auch Aufgaben asynchrone Vorgänge dar, die gleichzeitig ausgeführt werden können. Es dürfen jedoch mehrere Aufgaben im selben Thread ausgeführt werden. Finden Sie unter [asynchrone Programmierung in JavaScript (Windows Store-apps)](https://msdn.microsoft.com/library/windows/apps/hh700330.aspx) für Weitere Informationen.  
  
 In verwaltetem Code können Sie das Fenster **Aufgaben** verwenden, wenn Sie mit<xref:System.Threading.Tasks.Task?displayProperty=fullName> -Objekten oder mit den **await**- und **async**-Schlüsselwörtern arbeiten (**Await** und **Async** in Visual Basic). Weitere Informationen zu Aufgaben in verwaltetem Code finden Sie unter [zur parallelen Programmierung](https://msdn.microsoft.com/library/4d83c690-ad2d-489e-a2e0-b85b898a672d).  
  
 In nativem Code können Sie das Fenster **Aufgaben** verwenden, wenn Sie mit [Aufgabengruppen](https://msdn.microsoft.com/library/42f05ac3-2098-494a-ba84-737fcdcad077), [parallelen Algorithmen](https://msdn.microsoft.com/library/045dca7b-4d73-4558-a44c-383b88a28473), [asynchronen Agents](https://msdn.microsoft.com/library/6cf6ccc6-87f1-4e14-af15-ea8ba58fef1a) und [einfachen Aufgaben](https://msdn.microsoft.com/library/9aba278c-e0c9-4ede-b7c6-fedf7a365d90) arbeiten. Weitere Informationen zu Aufgaben in nativem Code finden Sie unter [Concurrency Runtime](https://msdn.microsoft.com/library/874bc58f-8dce-483e-a3a1-4dcc9e52ed2c).  
  
 In JavaScript können Sie das Fenster "Aufgaben" verwenden, wenn Sie mit dem "promise .then"-Code arbeiten.  
  
 Sie können das Fenster **Aufgaben** immer dann verwenden, wenn die Ausführung im Debugger unterbrochen wird. Sie können darauf zugreifen, indem Sie im Menü **Debuggen** auf **Fenster** und anschließend auf **Aufgaben** klicken. In der folgenden Abbildung wird das Fenster **Aufgaben** im Standardmodus dargestellt.  
  
 ![Fenster "Parallele Aufgaben"](../debugger/media/parallel-tasks-window.png "Parallel_Tasks_Window")  
  
> [!NOTE]
> In verwaltetem Code wird ein <xref:System.Threading.Tasks.Task>-Objekt mit dem Status <xref:System.Threading.Tasks.TaskStatus>, <xref:System.Threading.Tasks.TaskStatus> oder <xref:System.Threading.Tasks.TaskStatus> möglicherweise nicht im Aufgabenfenster angezeigt, wenn sich verwaltete Threads in einem Standby- oder Verknüpfungszustand befinden.  
  
## <a name="tasks-column-information"></a>Informationen in der Spalte „Aufgaben“  
 In den Spalten im Fenster **Aufgaben** sind die folgenden Informationen angegeben.  
  
|Spaltenname|Beschreibung|  
|-----------------|-----------------|  
|**Flags**|Zeigt an, welche Aufgaben gekennzeichnet sind. Zudem können Sie Aufgaben kennzeichnen bzw. deren Kennzeichnung aufheben.|  
|**Symbole**|Ein gelber Pfeil gibt die aktuelle Aufgabe an. Die aktuelle Aufgabe ist die oberste Aufgabe im aktuellen Thread.<br /><br /> Ein weißer Pfeil gibt die unterbrechende Aufgabe an, d. h., die Aufgabe, die beim Aufrufen des Debuggers aktuell war.<br /><br /> Das Pausensymbol gibt eine Aufgabe an, die vom Benutzer eingefroren wurde. Sie können eine Aufgabe einfrieren und deaktivieren, indem Sie in der Liste mit der rechten Maustaste darauf klicken.|  
|**ID**|Eine vom System bereitgestellte Nummer für die Aufgabe. In nativem Code ist diese Nummer die Adresse der Aufgabe.|  
|**Status**|Der aktuelle Zustand der Aufgabe (geplant, aktiv, blockiert, wartend oder abgeschlossen). Eine geplante Aufgabe wurde noch nicht ausgeführt und verfügt daher noch über keine Aufrufliste, keinen zugewiesenen Thread oder weitere Informationen.<br /><br /> Eine aktive Aufgabe hat vor dem Unterbrechen im Debugger Code ausgeführt.<br /><br /> Eine wartende Aufgabe ist blockiert, da sie auf das Signalisieren eines Ereignisses, das Aufheben einer Sperre oder das Abschließen einer anderen Aufgabe wartet.<br /><br /> Eine blockierte Aufgabe ist eine wartende Aufgabe, deren Thread an einem anderen Thread blockiert ist.<br /><br /> Zeigen Sie auf die **Status** Zelle für eine blockierte oder wartende Aufgabe, um weitere Informationen zum Block anzuzeigen. **Warnung:**  Im Fenster **Aufgaben** werden Deadlocks nur für eine blockierte Aufgabe gemeldet, bei der eine Synchronisierungsprimitive verwendet wird, die von Wait Chain Traversal (WCT) unterstützt wird. Z. B. für einen Deadlock <xref:System.Threading.Tasks.Task> -Objekt, das WCT verwendet wird, meldet der Debugger **Waiting-deadlocked**. Für eine Aufgabe mit Deadlock, die von der Concurrency Runtime verwaltet wird, die nicht WCT verwendet, meldet der Debugger **Warten**. Weitere Informationen zu WCT finden Sie unter [Wait Chain Traversal](https://msdn.microsoft.com/library/ms681622\(VS.85\).aspx).|  
|**Startzeit**|Die Uhrzeit, zu der die Aufgabe aktiviert wurde.|  
|**Dauer**|Die Anzahl von Sekunden, die die Aufgabe aktiv war.|  
|**Abschlusszeit**|Die Uhrzeit, zu der die Aufgabe abgeschlossen wurde.|  
|**Position**|Die aktuelle Position in der Aufrufliste der Aufgabe. Zeigen Sie auf diese Zelle, um die gesamte Aufrufliste für die Aufgabe anzuzeigen. Für geplante Aufgaben ist in dieser Spalte kein Wert vorhanden.|  
|**Aufgabe**|Die ursprüngliche Methode und Argumente, die beim Erstellen an die Aufgabe übergeben wurden.|  
|**Parent**|Die ID der Aufgabe, von der diese Aufgabe erstellt wurde. Wenn diese Spalte leer ist, verfügt die Aufgabe über kein übergeordnetes Element. Dies gilt nur für verwaltete Programme.|  
|**Threadzuweisung**|Die ID und der Name des Threads, in dem die Aufgabe ausgeführt wird.|  
|**Rückgabestatus**|Der Status der Aufgabe zum Zeitpunkt des Abschlusses. Werden Werte des Rückgabestatus **Erfolg**, **Cancelled**, und **Fehler**.|  
|**AppDomain**|Für verwalteten Code die Anwendungsdomäne, in der die Aufgabe ausgeführt wird.|  
|**task_group**|Für nativen Code die Adresse des [task_group](https://msdn.microsoft.com/library/b4af5b28-227d-4488-8194-0a0d039173b7)-Objekts, von dem die Aufgabe geplant wurde. Für asynchrone Agents und einfache Aufgaben wird diese Spalte auf 0 festgelegt.|  
|Prozess|Die ID des Prozesses, in dem die Aufgabe ausgeführt wird.|  
|Asynchroner Zustand|Für verwalteten Code ist dies der Aufgabenstatus. Standardmäßig ist diese Spalte ausgeblendet. Um diese Spalte anzuzeigen, öffnen Sie das Kontextmenü für einen der Spaltenheader. Wählen Sie **Spalten**, **AsyncState** aus.|  
  
 Sie können der Ansicht Spalten hinzufügen, indem Sie mit der rechten Maustaste auf eine Spaltenüberschrift klicken und die gewünschten Spalten auswählen. (Entfernen Sie Spalten, indem Sie die jeweilige Auswahl aufheben.) Sie können auch die Anordnung der Spalten ändern, indem Sie sie nach links oder rechts ziehen. Das Kontextmenü für Spalten wird in der folgenden Abbildung veranschaulicht.  
  
 ![Ansicht "Kontextmenü" im Fenster "Parallele Aufgaben"](../debugger/media/parallel-tasks-contextmenu.png "Parallel_Tasks_ContextMenu")  
  
## <a name="sorting-tasks"></a>Sortieren von Aufgaben  
 Wenn Sie Aufgaben nach Spaltenkriterien sortieren möchten, klicken Sie auf den Spaltenheader. Beispielsweise, indem Sie auf die **ID** Spaltenüberschrift klicken, können Sie die Aufgaben nach Aufgaben-ID sortieren: 1,2,3,4,5 und So weiter. Klicken Sie erneut auf den Spaltenheader, um die Sortierreihenfolge umzukehren. Die aktuelle Sortierspalte und die Sortierreihenfolge werden durch einen Pfeil in der Spalte angegeben.  
  
## <a name="grouping-tasks"></a>Gruppieren von Aufgaben  
 Sie können Aufgaben nach jeder Spalte in der Listenansicht gruppieren. Z. B. durch einen Rechtsklick auf die **Status** Spaltenüberschrift, und klicken Sie dann auf **Gruppieren nach Status**, Sie können alle Aufgaben, die den gleichen Status gruppieren. So können Sie z. B. schnell wartende Aufgaben anzeigen lassen, damit Sie untersuchen können, aus welchen Gründen diese blockiert sind. Sie können auch Gruppen reduzieren, die während der Debugsitzung nicht von Interesse sind. Auf die gleiche Weise können Sie nach den anderen Spalten gruppieren. Eine Gruppe kann gekennzeichnet bzw. die Kennzeichnung einer Gruppe kann aufgehoben werden, indem Sie auf die Schaltfläche neben dem Gruppenheader klicken. In der folgenden Abbildung wird das Fenster **Aufgaben** im gruppierten Modus dargestellt.  
  
 ![Gruppierter Modus im Fenster "Parallele Aufgaben"](../debugger/media/parallel-tasks-groupedmode.png "Parallel_Tasks_GroupedMode")  
  
## <a name="parent-child-view"></a>Ansicht über- und untergeordneter Elemente  
 (Diese Ansicht ist nur für verwalteten Code verfügbar.) Durch einen Rechtsklick auf eine Spaltenüberschrift, und klicken Sie dann auf **übergeordneten untergeordneten Ansicht**, Sie können die Liste der Vorgänge ändern, in eine hierarchische Ansicht, in der jede untergeordnete Aufgabe einen Unterknoten darstellt, der angezeigt werden kann oder die unter dem übergeordneten Element ausgeblendet ist. In der folgenden Abbildung werden die Aufgaben in der Ansicht übergeordneter und untergeordneter Elemente angezeigt.  
  
 ![Übergeordnete&#45;untergeordnete Ansicht im Fenster "Parallele Aufgaben"](../debugger/media/parallel-tasks-parentchildview.png "Parallel_Tasks_ParentChildView")  
  
## <a name="flagging-tasks"></a>Kennzeichnen von Aufgaben  
 Sie können den Thread, der die Aufgabe, die auf dem eine Aufgabe ausgeführt wird, wählen Sie die Aufgabe Liste, und klicken dann kennzeichnen **Flag** aus dem Kontextmenü oder durch Klicken auf das Flagsymbol in der ersten Spalte. Wenn Sie mehrere Aufgaben kennzeichnen, können Sie nach der Flagspalte sortieren, um alle gekennzeichneten Aufgaben an oberster Stelle anzuzeigen, sodass Sie sich auf die betreffenden Aufgaben konzentrieren können. Sie können auch das Fenster **Parallele Stapel** verwenden, um ausschließlich gekennzeichnete Aufgaben anzuzeigen. Damit können Sie Aufgaben herausfiltern, die für das Debugging nicht von Interesse sind. Flags werden nicht zwischen Debugsitzungen beibehalten.  
  
## <a name="freezing-and-thawing-tasks"></a>Einfrieren und Reaktivieren von Aufgaben  
 Sie können den Thread einfrieren, in dem eine Aufgabe ausgeführt wird. Klicken Sie dazu mit der rechten Maustaste auf das Aufgabenlistenelement, und klicken Sie anschließend auf **Zugewiesenen Thread einfrieren**. (Wenn eine Aufgabe bereits eingefroren ist, heißt der Befehl **Zugewiesenen Thread entsperren**.) Wenn Sie einen Thread einfrieren, wird dieser Thread nicht ausgeführt, wenn Sie Code nach dem aktuellen Haltepunkt schrittweise durchlaufen. Die **Einfrieren aller Threads, aber diese** Befehl bleibt hängen alle Threads mit Ausnahme der, der das Aufgabenlistenelement ausführt.  
  
 In der folgenden Abbildung werden die anderen Menüelemente für die einzelnen Aufgaben angezeigt.  
  
 ![Kontextmenü "Thread" im Fenster "Parallele Aufgaben"](../debugger/media/parallel-tasks-contextmenu2.png "Parallel_Tasks_ContextMenu2")  
  
## <a name="see-also"></a>Siehe auch  
 [Debugger – Grundlagen](../debugger/debugger-basics.md)   
 [Debuggen von verwaltetem Code](../debugger/debugging-managed-code.md)   
 [Parallele Programmierung](https://msdn.microsoft.com/library/4d83c690-ad2d-489e-a2e0-b85b898a672d)   
 [Concurrency Runtime](https://msdn.microsoft.com/library/874bc58f-8dce-483e-a3a1-4dcc9e52ed2c)   
 [View threads and tasks in the Parallel Stacks window (Anzeigen von Threads und Aufgaben im Fenster „Parallele Stapel“)](../debugger/using-the-parallel-stacks-window.md)   
 [Exemplarische Vorgehensweise: Debuggen einer Parallelanwendung](../debugger/walkthrough-debugging-a-parallel-application.md)
