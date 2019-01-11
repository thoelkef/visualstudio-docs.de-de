---
title: Verwenden das Fenster "Aufgaben" | Microsoft-Dokumentation
ms.date: 03/18/2018
ms.topic: conceptual
f1_keywords:
- vs.debug.paralleltasks
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- debugger, parallel tasks window
ms.assetid: bd5e0612-a0dc-41cf-a7af-1e87d0d5c35f
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: dfb95e3bc1a2a1aaf94db229d951773e97d4ef2d
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MTE95
ms.contentlocale: de-DE
ms.lasthandoff: 01/02/2019
ms.locfileid: "53942839"
---
# <a name="using-the-tasks-window"></a>Verwenden des Fensters "Aufgaben"

Das Fenster **Aufgaben** ähnelt dem Fenster **Threads**. In diesem Fenster werden jedoch Informationen zu jedem <xref:System.Threading.Tasks.Task?displayProperty=fullName>-, [task_handle](/cpp/parallel/concrt/reference/task-group-class)- oder [WinJS.Promise](/previous-versions/windows/apps/br211867(v=win.10))-Objekt anstatt für die einzelnen Threads angezeigt. Wie Threads stellen auch Aufgaben asynchrone Vorgänge dar, die gleichzeitig ausgeführt werden können. Es dürfen jedoch mehrere Aufgaben im selben Thread ausgeführt werden.

In verwaltetem Code können Sie das Fenster **Aufgaben** verwenden, wenn Sie mit<xref:System.Threading.Tasks.Task?displayProperty=fullName> -Objekten oder mit den **await**- und **async**-Schlüsselwörtern arbeiten (**Await** und **Async** in Visual Basic). Weitere Informationen zu Aufgaben in verwaltetem Code finden Sie unter [zur parallelen Programmierung](/dotnet/standard/parallel-programming/index).

In nativem Code können Sie das Fenster **Aufgaben** verwenden, wenn Sie mit [Aufgabengruppen](/cpp/parallel/concrt/task-parallelism-concurrency-runtime), [parallelen Algorithmen](/cpp/parallel/concrt/parallel-algorithms), [asynchronen Agents](/cpp/parallel/concrt/asynchronous-agents) und [einfachen Aufgaben](/cpp/parallel/concrt/task-scheduler-concurrency-runtime) arbeiten. Weitere Informationen zu Aufgaben in nativem Code finden Sie unter [Concurrency Runtime](/cpp/parallel/concrt/concurrency-runtime).

In JavaScript können Sie das Fenster "Aufgaben" Wenn Sie mit der Zusage arbeiten `.then` Code. Finden Sie unter [asynchrone Programmierung in JavaScript (UWP-apps)](/previous-versions/windows/apps/hh700330(v=win.10)) für Weitere Informationen.

Sie können das Fenster **Aufgaben** immer dann verwenden, wenn die Ausführung im Debugger unterbrochen wird. Sie können darauf zugreifen, indem Sie im Menü **Debuggen** auf **Fenster** und anschließend auf **Aufgaben** klicken. In der folgenden Abbildung wird das Fenster **Aufgaben** im Standardmodus dargestellt.

![Fenster "Aufgaben"](../debugger/media/parallel_tasks_window.png "Parallel_Tasks_Window")

> [!NOTE]
> In verwaltetem Code eine <xref:System.Threading.Tasks.Task> -Objekt mit dem Status der [TaskStatus.Created](<xref:System.Threading.Tasks.TaskStatus.Created>), [TaskStatus.WaitingForActivation](<xref:System.Threading.Tasks.TaskStatus.WaitingForActivation>), oder [TaskStatus.WaitingToRun](<xref:System.Threading.Tasks.TaskStatus.WaitingToRun>) möglicherweise nicht angezeigt der **Aufgaben** Wartungszeitfensters, in verwalteten Threads in einem Standby- oder Verknüpfungszustand Zustand befinden.

## <a name="tasks-column-information"></a>Informationen in der Spalte „Aufgaben“

In den Spalten im Fenster **Aufgaben** sind die folgenden Informationen angegeben.

|Spaltenname|Beschreibung|
|-----------------|-----------------|
|**Flags**|Zeigt an, welche Aufgaben gekennzeichnet sind. Zudem können Sie Aufgaben kennzeichnen bzw. deren Kennzeichnung aufheben.|
|**Symbole**|Ein gelber Pfeil gibt die aktuelle Aufgabe an. Die aktuelle Aufgabe ist die oberste Aufgabe im aktuellen Thread.<br /><br /> Ein weißer Pfeil gibt die unterbrechende Aufgabe an, d. h., die Aufgabe, die beim Aufrufen des Debuggers aktuell war.<br /><br /> Das Pausensymbol gibt eine Aufgabe an, die vom Benutzer eingefroren wurde. Sie können eine Aufgabe einfrieren und deaktivieren, indem Sie in der Liste mit der rechten Maustaste darauf klicken.|
|**ID**|Eine vom System bereitgestellte Nummer für die Aufgabe. In nativem Code ist diese Nummer die Adresse der Aufgabe.|
|**Status**|Der aktuelle Status (geplant, aktiv, blockiert, blockiert, wartet auf oder abgeschlossen) der Aufgabe. Eine geplante Aufgabe wurde noch nicht ausgeführt und verfügt daher noch über keine Aufrufliste, keinen zugewiesenen Thread oder weitere Informationen.<br /><br /> Eine aktive Aufgabe hat vor dem Unterbrechen im Debugger Code ausgeführt.<br /><br /> Eine wartet auf oder auf blockierte Aufgabe ist blockiert, da er auf ein Ereignis signalisiert werden, eine Sperre aufgehoben wird oder auf den Abschluss einer anderen Aufgabe wartet.<br /><br /> Eine blockierte Aufgabe ist eine wartende Aufgabe, deren Thread an einem anderen Thread blockiert ist.<br /><br /> Zeigen Sie auf die **Status** Zelle für eine Aufgabe blockiert oder wartet auf, um weitere Informationen zum Block anzuzeigen. **Warnung:**  Im Fenster **Aufgaben** werden Deadlocks nur für eine blockierte Aufgabe gemeldet, bei der eine Synchronisierungsprimitive verwendet wird, die von Wait Chain Traversal (WCT) unterstützt wird. Z. B. für einen Deadlock <xref:System.Threading.Tasks.Task> -Objekt, das WCT verwendet wird, meldet der Debugger **erwartet-deadlocked**. Für eine Aufgabe mit Deadlock, die von der Concurrency Runtime verwaltet wird, die nicht WCT verwendet, meldet der Debugger **Warten**. Weitere Informationen zu WCT finden Sie unter [Wait Chain Traversal](/windows/desktop/Debug/wait-chain-traversal).|
|**Startzeit**|Die Uhrzeit, zu der die Aufgabe aktiviert wurde.|
|**Dauer**|Die Anzahl von Sekunden, die die Aufgabe aktiv war.|
|**Abschlusszeit**|Die Uhrzeit, zu der die Aufgabe abgeschlossen wurde.|
|**Position**|Die aktuelle Position in der Aufrufliste der Aufgabe. Zeigen Sie auf diese Zelle, um die gesamte Aufrufliste für die Aufgabe anzuzeigen. Für geplante Aufgaben ist in dieser Spalte kein Wert vorhanden.|
|**Aufgabe**|Die ursprüngliche Methode und Argumente, die beim Erstellen an die Aufgabe übergeben wurden.|
|**AsyncState**|Für verwalteten Code ist dies der Aufgabenstatus. Standardmäßig ist diese Spalte ausgeblendet. Um diese Spalte anzuzeigen, öffnen Sie das Kontextmenü für einen der Spaltenheader. Wählen Sie **Spalten**, **AsyncState** aus.|
|**Parent**|Die ID der Aufgabe, von der diese Aufgabe erstellt wurde. Wenn diese Spalte leer ist, verfügt die Aufgabe über kein übergeordnetes Element. Dies gilt nur für verwaltete Programme.|
|**Threadzuweisung**|Die ID und der Name des Threads, in dem die Aufgabe ausgeführt wird.|
|**AppDomain**|Für verwalteten Code die Anwendungsdomäne, in der die Aufgabe ausgeführt wird.|
|**task_group**|Für nativen Code die Adresse des [task_group](/cpp/parallel/concrt/reference/task-group-class)-Objekts, von dem die Aufgabe geplant wurde. Für asynchrone Agents und einfache Aufgaben wird diese Spalte auf 0 festgelegt.|
|**Process**|Die ID des Prozesses, in dem die Aufgabe ausgeführt wird.|

 Sie können der Ansicht Spalten hinzufügen, indem Sie mit der rechten Maustaste auf eine Spaltenüberschrift klicken und die gewünschten Spalten auswählen. (Entfernen Sie Spalten, indem Sie die jeweilige Auswahl aufheben.) Sie können auch die Anordnung der Spalten ändern, indem Sie sie nach links oder rechts ziehen. Das Kontextmenü für Spalten wird in der folgenden Abbildung veranschaulicht.

 ![Ansicht "Kontextmenü" im Fenster "Aufgaben"](../debugger/media/parallel_tasks_contextmenu.png "Parallel_Tasks_ContextMenu")

## <a name="sorting-tasks"></a>Sortieren von Aufgaben
 Wenn Sie Aufgaben nach Spaltenkriterien sortieren möchten, klicken Sie auf den Spaltenheader. Beispielsweise, indem Sie auf die **ID** Spaltenüberschrift klicken, können Sie die Aufgaben nach Aufgaben-ID sortieren: Und so weiter. Klicken Sie erneut auf den Spaltenheader, um die Sortierreihenfolge umzukehren. Die aktuelle Sortierspalte und die Sortierreihenfolge werden durch einen Pfeil in der Spalte angegeben.

## <a name="grouping-tasks"></a>Gruppieren von Aufgaben
 Sie können Aufgaben nach jeder Spalte in der Listenansicht gruppieren. Wenn Sie beispielsweise mit der rechten Maustaste auf den Spaltenheader **Status** klicken und anschließend auf **Gruppieren nach** > **[*Status*]** klicken, können Sie alle Aufgaben gruppieren, die denselben Status aufweisen. Beispielsweise können Sie schnell erkennen, Tasks erwartet, sodass Sie untersuchen können, welchen Gründen diese blockiert werden. Sie können auch Gruppen reduzieren, die während der Debugsitzung nicht von Interesse sind. Auf die gleiche Weise können Sie nach den anderen Spalten gruppieren. Eine Gruppe kann gekennzeichnet bzw. die Kennzeichnung einer Gruppe kann aufgehoben werden, indem Sie auf die Schaltfläche neben dem Gruppenheader klicken. In der folgenden Abbildung wird das Fenster **Aufgaben** im gruppierten Modus dargestellt.

 ![Gruppierter Modus im Fenster "Aufgaben"](../debugger/media/parallel_tasks_groupedmode.png "Parallel_Tasks_GroupedMode")

## <a name="parent-child-view"></a>Ansicht über- und untergeordneter Elemente
 (Diese Ansicht ist nur für verwalteten Code verfügbar.) Mit der rechten Maustaste die **Status** Spaltenüberschrift, und klicken Sie dann auf **Group by-** > **übergeordneten**, können Sie die Liste der Aufgaben in eine hierarchische Ansicht, in denen ändern jede untergeordnete Aufgabe ist es sich um einen Unterknoten darstellt, der angezeigt werden kann oder die unter dem übergeordneten Element ausgeblendet werden kann.

## <a name="flagging-tasks"></a>Kennzeichnen von Aufgaben
 Sie können den Thread, der die Aufgabe, die auf dem eine Aufgabe ausgeführt wird, wählen Sie die Aufgabe Liste, und klicken dann kennzeichnen **zugewiesenen Thread kennzeichnen** aus dem Kontextmenü oder durch Klicken auf das Flagsymbol in der ersten Spalte. Wenn Sie mehrere Aufgaben kennzeichnen, können Sie nach der Flagspalte sortieren, um alle gekennzeichneten Aufgaben an oberster Stelle anzuzeigen, sodass Sie sich auf die betreffenden Aufgaben konzentrieren können. Sie können auch das Fenster **Parallele Stapel** verwenden, um ausschließlich gekennzeichnete Aufgaben anzuzeigen. Damit können Sie Aufgaben herausfiltern, die für das Debugging nicht von Interesse sind. Flags werden nicht zwischen Debugsitzungen beibehalten.

## <a name="freezing-and-thawing-tasks"></a>Einfrieren und Reaktivieren von Aufgaben
 Sie können den Thread einfrieren, in dem eine Aufgabe ausgeführt wird. Klicken Sie dazu mit der rechten Maustaste auf das Aufgabenlistenelement, und klicken Sie anschließend auf **Zugewiesenen Thread einfrieren**. (Wenn eine Aufgabe bereits eingefroren ist, heißt der Befehl **Zugewiesenen Thread entsperren**.) Wenn Sie einen Thread einfrieren, wird dieser Thread nicht ausgeführt, wenn Sie Code nach dem aktuellen Haltepunkt schrittweise durchlaufen. Die **Einfrieren aller Threads, aber diese eine** Befehl bleibt hängen alle Threads mit Ausnahme der, der das Aufgabenlistenelement ausführt.

 In der folgenden Abbildung werden die anderen Menüelemente für die einzelnen Aufgaben angezeigt.

 ![Kontextmenü "Thread" im Fenster "Aufgaben"](../debugger/media/parallel_tasks_contextmenu2.png "Parallel_Tasks_ContextMenu2")

## <a name="switching-the-active-task-or-frame"></a>Wechseln das aktive Aufgabe oder den Zielframe

Die **zu Aufgabe wechseln** Befehl wird der aktuellen Aufgabe die aktive Aufgabe. Die **zu Rahmen wechseln** Befehl wird der ausgewählte Stack Rahmen für den aktiven Stapelrahmen. Der Debuggerkontext wechselt in den aktuellen Vorgang oder den ausgewählten Stapelrahmen.

## <a name="see-also"></a>Siehe auch

- [Erster Einblick in den Debugger](../debugger/debugger-feature-tour.md)
- [Debuggen von verwaltetem Code](../debugger/debugging-managed-code.md)
- [Parallele Programmierung](/dotnet/standard/parallel-programming/index)
- [Concurrency Runtime](/cpp/parallel/concrt/concurrency-runtime)
- [Verwenden des Fensters "Parallele Stapel"](../debugger/using-the-parallel-stacks-window.md)
- [Exemplarische Vorgehensweise: Debuggen einer Parallelanwendung](../debugger/walkthrough-debugging-a-parallel-application.md)