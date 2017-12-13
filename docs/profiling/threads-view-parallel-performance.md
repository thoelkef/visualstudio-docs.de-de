---
title: Threadansicht (Parallele Leistung) | Microsoft-Dokumentation
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: vs.performance.view.threadblocking
helpviewer_keywords: Concurrency Visualizer, Threads View (Parallel Performance)
ms.assetid: 2e441103-a266-407b-88c3-fb58716257a3
caps.latest.revision: "21"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: bdad50eff09e96c5d9c0513be1f571a901278871
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 10/31/2017
---
# <a name="threads-view-parallel-performance"></a>Threadansicht (Parallele Leistung)
Die Threadansicht ist die detaillierteste und funktionsreichste Ansicht in der Parallelitätsschnellansicht. Mithilfe dieser Ansicht können Sie ermitteln, ob die Threads ausgeführt werden oder aufgrund von Synchronisierung, E/A oder aus anderen Gründen blockiert werden.  
  
 Während der Profilanalyse untersucht die Parallelitätsschnellansicht alle Kontextwechselereignisse des Betriebssystems für jeden Anwendungsthread. Kontextwechsel können aus vielen Gründen auftreten, darunter folgende:  
  
-   Ein Thread wird auf einer Synchronisierungsprimitive blockiert.  
  
-   Das Quantum eines Threads läuft ab.  
  
-   Durch einen Thread erfolgt eine blockierende E/A-Anforderung.  
  
 In der Threadansicht wird jedem Kontextwechsel eine Kategorie zugewiesen, wenn ein Thread die Ausführung beendet hat. Die Kategorien werden in der Legende im unteren linken Teil der Ansicht angezeigt. Die Parallelitätsschnellansicht kategorisiert Kontextwechselereignisse, indem sie die Aufrufliste des Threads nach bekannten blockierenden APIs durchsucht. Wenn keine Aufruflistenübereinstimmung vorliegt, wird die von [!INCLUDE[TLA#tla_mswin](../code-quality/includes/tlasharptla_mswin_md.md)] bereitgestellte Warteursache verwendet. Die [!INCLUDE[TLA#tla_mswin](../code-quality/includes/tlasharptla_mswin_md.md)]-Kategorie basiert jedoch möglicherweise auf einem Implementierungsdetail und entspricht nicht der Absicht des Benutzers. [!INCLUDE[TLA#tla_mswin](../code-quality/includes/tlasharptla_mswin_md.md)] meldet z.B. die Warteursache für das Blockieren einer nativen SRW-Sperre (Slim Reader/Writer) als E/A und nicht als Synchronisierung. In den meisten Fällen können Sie die Ursache eines blockierenden Ereignisses identifizieren, indem Sie die Aufruflisten überprüfen, die Kontextwechselereignissen entsprechen.  
  
 In der Threadansicht werden auch Abhängigkeiten zwischen Threads angezeigt. Wenn Sie z.B. einen Thread identifizieren, der bei einem Synchronisierungsobjekt blockiert, können Sie nach dem Thread suchen, der die Blockierung aufgehoben hat, und Sie können die Aktivität in der Aufrufliste für diesen Thread zu dem Zeitpunkt überprüfen, als er die Blockierung aufgehoben hat.  
  
 Wenn Threads ausgeführt werden, sammelt die Parallelitätsschnellansicht Beispiele. In der Threadansicht können Sie analysieren, welcher Code während eines Ausführungssegments von einem oder mehreren Threads ausgeführt wird. Sie können auch blockierende Berichte und Berichte überprüfen, die für die Aufruflistenstrukturausführung ein Profil erstellen.  
  
## <a name="usage"></a>Verwendung  
 Sie können die Threadansicht unter anderem folgendermaßen verwenden:  
  
-   Gründe identifizieren, warum die Benutzeroberfläche (UI) einer Anwendung in bestimmten Ausführungsphasen nicht reagiert.  
  
-   Die Zeitdauer identifizieren, die für das Blockieren von Synchronisierung, E/A, Seitenfehlern und anderen Ereignissen aufgewendet wird.  
  
-   Den Grad der Störung durch andere Prozesse identifizieren, die auf dem System ausgeführt werden.  
  
-   Lastenausgleichsprobleme bei paralleler Ausführung identifizieren.  
  
-   Gründe für suboptimale oder nicht vorhandene Skalierbarkeit identifizieren, z.B. warum sich die Leistung einer parallelen Anwendung nicht verbessert, wenn mehr logische Kerne verfügbar sind.  
  
-   Den Parallelitätsgrad in der Anwendung verstehen, um die Parallelisierung zu unterstützen.  
  
-   Abhängigkeiten zwischen Arbeitsthreads und kritischen Pfaden der Ausführung verstehen.  
  
## <a name="examining-specific-time-intervals-and-threads"></a>Untersuchen von bestimmten Zeitintervallen und Threads  
 In der Threadansicht wird eine Zeitachse angezeigt. Sie können in der Zeitachse vergrößern und schwenken, um bestimmte Intervalle und Threads der Anwendung zu überprüfen. Die x-Achse gibt die Zeit an und auf der y-Achse gibt es verschiedene Kanäle:  
  
-   Zwei E/A-Kanäle für jedes Laufwerk im System, einen Kanal für Lesevorgänge und einen für Schreibvorgänge.  
  
-   Einen Kanal für jeden Thread im Prozess.  
  
-   Markerkanäle, falls Markerereignisse in der Ablaufverfolgung vorhanden sind. Markerkanäle werden zuerst unter den Threadkanälen angezeigt, die diese Ereignisse generiert haben.  
  
-   GPU-Kanäle.  
  
 Hier ist die Threadansicht veranschaulicht:  
  
 ![Threadansicht](../profiling/media/threadsviewnarrowing.png "ThreadsViewNarrowing")  
Threadansicht  
  
 Die Threads werden zuerst in der Reihenfolge sortiert, in der sie erstellt werden, sodass der Hauptanwendungsthread der erste ist. Sie können die Sortieroption in der linken oberen Ecke der Ansicht verwenden, um Threads nach einem anderen Kriterium zu sortieren (z.B. nach der meisten Arbeit bei der Ausführung).  
  
 Sie können Threads ausblenden, die keine Arbeit ausführen, indem Sie deren Namen in der Spalte auf der linken Seite auswählen und dann auf der Symbolleiste **Ausgewählte Threads ausblenden** auswählen. Es wird empfohlen, vollständig blockierte Threads auszublenden, da ihre Statistiken irrelevant sind und die Berichte überlasten können.  
  
 Um zusätzliche Threads zu ermitteln, die Sie ausblenden können, wählen Sie in der aktiven Legende über die Registerkarte **Profilbericht** den Bericht **Zusammenfassung pro Thread** aus. Dadurch wird das Ausführungsaufschlüsselungsdiagramm angezeigt, das den Zustand von Threads für das derzeit ausgewählte Zeitintervall anzeigt. Auf einigen Zoomstufen, werden mehrere Threads möglicherweise nicht angezeigt. In diesem Fall werden auf der rechten Seite Auslassungszeichen angezeigt.  
  
 Wenn Sie ein Zeitintervall und einige Threads darin ausgewählt haben, können Sie die Leistungsanalyse starten.  
  
## <a name="analysis-tools"></a>Analysetools  
 In diesem Abschnitt geht es um Berichte und andere Analysetools.  
  
### <a name="thread-blocking-details"></a>Details zur Threadblockierung  
 Um Informationen über ein blockierendes Ereignis in einem bestimmten Bereich auf einem Thread abzurufen, können Sie mit dem Mauszeiger auf diesen Bereich gehen, um eine QuickInfo anzuzeigen. Sie enthält Informationen wie Kategorie, Startzeit des Bereichs, Blockierungsdauer und eine blockierende API, sofern vorhanden. Wenn Sie den blockierenden Bereich auswählen, wird der Stapel zu diesem Zeitpunkt im unteren Bereich zusammen mit den Informationen aus der QuickInfo angezeigt. Durch Untersuchen der Aufrufliste können Sie den Grund für das Ereignis bestimmen, das den Thread blockiert. Zusätzliche Prozess- und Threadinformationen erhalten Sie, indem Sie das Segment auswählen und die aktuelle Registerkarte überprüfen.  
  
 Ein Ausführungspfad hat möglicherweise mehrere blockierende Ereignisse. Sie können diese nach Blockierungskategorie überprüfen, sodass Sie Problembereiche schneller finden. Wählen Sie einfach eine der Blockierungskategorien in der Legende links aus.  
  
### <a name="dependencies-between-threads"></a>Abhängigkeiten zwischen Threads  
 Die Parallelitätsschnellansicht kann Abhängigkeiten zwischen Threads im Prozess anzeigen, damit Sie feststellen können, was ein blockierter Thread ausführen wollte, und welcher andere Thread die Ausführung ermöglicht hat. Wählen Sie das relevante Blockierungssegment aus, um festzustellen, welcher Thread die Blockierung eines anderen Threads aufgehoben hat. Wenn die Parallelitätsschnellansicht den die Blockierung aufhebenden Thread bestimmen kann, zeichnet sie eine Linie zwischen diesem und dem ausführenden Segment, das dem blockierenden Segment folgt. Außerdem zeigt die Registerkarte **Stapelblockierung wird aufgehoben** die relevante Aufrufliste an.  
  
### <a name="thread-execution-details"></a>Details zur Threadausführung  
 Im Zeitachsendiagramm eines Threads zeigen die grünen Segmente an, wann Code ausgeführt wurde. Sie können ausführlichere Informationen über ein Ausführungssegment abrufen.  
  
 Wenn Sie einen Punkt in einem Ausführungssegment auswählen, durchsucht die Parallelitätsschnellansicht die relevante Aufrufliste nach diesem Zeitpunkt, zeigt dann darüber ein schwarzes Caretzeichen an sowie die Aufrufliste selbst auf der Registerkarte **Aktueller Stapel**. Sie können auf dem Ausführungssegment mehrere Punkte auswählen.  
  
> [!NOTE]
>  Die Parallelitätsschnellansicht ist möglicherweise nicht in der Lage, eine Auswahl auf einem Ausführungssegment aufzulösen. In der Regel tritt dies auf, wenn die Dauer des Segments weniger als eine Millisekunde beträgt.  
  
 Um ein Ausführungsprofil für alle aktivierten (nicht ausgeblendeten) Threads im aktuell ausgewählten Zeitraum zu erhalten, wählen Sie in der aktiven Legende die Schaltfläche **Ausführung** aus.  
  
### <a name="timeline-graph"></a>Zeitachsendiagramm  
 Im Zeitachsendiagramm wird die Aktivität aller Threads im Prozess sowie aller physischen Laufwerke auf dem Hostcomputer angezeigt. Außerdem werden GPU-Aktivität und Markerereignisse angezeigt.  Sie können die Ansicht vergrößern, um mehr Details anzuzeigen, oder verkleinern, um ein längeres Zeitintervall anzuzeigen. Sie können auch Punkte im Diagramm auswählen, um Details zu Kategorien, Startzeiten, Dauern und Aufruflistenzuständen abzurufen.  
  
 Im Zeitachsendiagramm zeigt eine Farbe den Status eines Threads zu einem bestimmten Zeitpunkt an. So werden z.B. ausführende Segmente grün, für Synchronisierung blockierte Segmente rot, Segmente mit Vorrang gelb und mit der Geräte-E/A beschäftigte Segmente violett angezeigt. In dieser Ansicht können Sie den Lastenausgleich zwischen Threads überprüfen, die an einer parallelen Schleife beteiligt sind oder gleichzeitige Aufgaben ausführen. Wenn ein Thread zum Abschließen mehr Zeit in Anspruch nimmt als die anderen, kann die Arbeit unausgewogen verteilt sein. Sie können diese Informationen verwenden, um die Leistung des Programms zu verbessern, indem Sie die Arbeit unter den Threads gleichmäßiger verteilen.  
  
 Wenn zu einem Zeitpunkt nur ein Thread grün ist (also ausführt), kann die Anwendung die Parallelität auf dem System möglicherweise nicht vollständig nutzen. Sie können das Zeitachsendiagramm verwenden, um Abhängigkeiten zwischen Threads und die zeitlichen Beziehungen zwischen blockierenden und blockierten Threads zu untersuchen. Um Threads neu anzuordnen, wählen Sie einen Thread und dann auf der Symbolleiste die Schaltfläche „Nach oben“ oder „Nach unten“ aus. Um Threads auszublenden, wählen Sie diese aus, und wählen Sie dann die Schaltfläche **Threads ausblenden** aus.  
  
### <a name="profile-reports"></a>Profilberichte  
 Unter dem Zeitachsendiagramm befinden sich ein Zeitachsenprofil und ein Bereich mit Registerkarten für verschiedene Berichte. Die Berichte werden automatisch aktualisiert, wenn Sie die Threadansicht ändern. Für große Ablaufverfolgungen ist der Berichtsbereich möglicherweise nicht verfügbar, während die Updates berechnet werden. Jeder Bericht verfügt über zwei Filteranpassungen: „Rauschunterdrückung“ und „Nur eigenen Code“. Verwenden Sie Rauschunterdrückung, um Aufrufstruktureinträge herauszufiltern, in denen nur wenig Zeit aufgewendet wird. Der Standardfilterwert beträgt 2 %, Sie können ihn jedoch von 0 bis 99 % anpassen. Aktivieren Sie das Kontrollkästchen **Nur eigenen Code**, um nur die Aufrufstruktur für Ihren Code anzuzeigen. Deaktivieren Sie es, um alle Aufrufstrukturen anzuzeigen.  
  
#### <a name="profile-report"></a>Profilbericht  
 In dieser Registerkarte werden Berichte angezeigt, die den Einträgen in der aktiven Legende entsprechen. Wählen Sie einen der Einträge aus, um einen Bericht anzuzeigen.  
  
#### <a name="current-stack"></a>Aktueller Stapel  
 Diese Registerkarte zeigt die Aufrufliste für einen ausgewählten Punkt auf einem Threadsegment im Zeitachsendiagramm an. Die Aufruflisten werden abgeschnitten, um nur die Aktivität anzuzeigen, die mit dem Programm verknüpft ist.  
  
#### <a name="unblocking-stack"></a>Stapelblockierung wird aufgehoben  
 Um zu sehen, welcher Thread die Blockierung des ausgewählten Threads aufgehoben hat und in welcher Codezeile, wählen Sie die Registerkarte **Stapelblockierung wird aufgehoben** aus.  
  
#### <a name="execution"></a>Ausführung  
 Der Ausführungsbericht zeigt die Aufschlüsselung der Zeit an, die die Anwendung zur Ausführung aufgewendet hat.  
  
 Um die Codezeile zu finden, für die Ausführungszeit aufgewendet wird, erweitern Sie die Aufrufstruktur, und wählen Sie dann im Kontextmenü für den Aufrufstruktureintrag **Quelle anzeigen** oder **Aufrufsites anzeigen** aus. **Quelle anzeigen** sucht die ausgeführte Codezeile. **Aufrufsites anzeigen** sucht die Codezeile, die die ausgeführte Codezeile aufgerufen hat. Wenn nur eine Aufrufsite vorhanden ist, wird die Codezeile hervorgehoben. Wenn mehrere Aufrufsites vorhanden sind, können Sie im erscheinenden Dialogfeld die gewünschte auswählen und dann die Schaltfläche **Zu Quelle wechseln** auswählen, um den Aufrufsitecode hervorzuheben. Es ist oft am nützlichsten, die Aufrufsite mit den meisten Instanzen, der meisten Zeit oder beidem zu suchen. Weitere Informationen finden Sie unter [Ausführungsprofilbericht](../profiling/execution-profile-report.md).  
  
#### <a name="synchronization"></a>Synchronisierung  
 Im Synchronisierungsbericht werden die Aufrufe angezeigt, die Blockierungen der Synchronisierung verursachen, sowie die aggregierten Blockierungszeiten der einzelnen Aufruflisten. Weitere Informationen finden Sie unter [Synchronisierungszeit](../profiling/synchronization-time.md).  
  
#### <a name="io"></a>E/A  
 Im E/A-Bericht werden die Aufrufe angezeigt, die E/A-Blockierungen verursachen, sowie die aggregierten Blockierungszeiten der einzelnen Aufruflisten. Weitere Informationen finden Sie unter [E/A-Zeit (Threadansicht)](../profiling/i-o-time-threads-view.md).  
  
#### <a name="sleep"></a>Sleep  
 Im Bericht zum Standbymodus werden die Aufrufe angezeigt, die Blockierungen des Standbymodus verursachen, sowie die aggregierten Blockierungszeiten der einzelnen Aufruflisten. Weitere Informationen finden Sie unter [Standbyzeit](../profiling/sleep-time.md).  
  
#### <a name="memory-management"></a>Speicherverwaltung  
 Im Speicherverwaltungsbericht werden die Aufrufe angezeigt, bei denen Blockierungen der Speicherverwaltung aufgetreten sind, sowie die aggregierten Blockierungszeiten der einzelnen Aufruflisten. Sie können diese Informationen verwenden, um Bereiche zu identifizieren, die eine übermäßige Paging- oder Garbage Collection aufweisen.  Weitere Informationen finden Sie unter [Speicherverwaltungszeit](../profiling/memory-management-time.md).  
  
#### <a name="preemption"></a>Vorzeitige Entfernung  
 Im Bericht über die vorzeitige Entfernung werden die Instanzen angezeigt, bei denen Prozesse auf dem System den aktuellen Prozess vorzeitig entfernt haben, sowie die einzelnen Threads, die Threads im aktuellen Prozess ersetzt haben. Sie können diese Informationen verwenden, um die Prozesse und Threads zu identifizieren, die an der vorzeitigen Entfernung am stärksten beteiligt sind. Weitere Informationen finden Sie unter [Zeit für die vorzeitige Entfernung](../profiling/preemption-time.md).  
  
#### <a name="ui-processing"></a>Benutzeroberflächenverarbeitung  
 Im Bericht zur Benutzeroberflächenverarbeitung werden die Aufrufe angezeigt, die eine Blockierung der Benutzeroberflächenverarbeitung verursachen, sowie die aggregierten Blockierungszeiten der einzelnen Aufruflisten. Weitere Informationen finden Sie unter [Benutzeroberflächenverarbeitungszeit](../profiling/ui-processing-time.md).  
  
#### <a name="per-thread-summary"></a>Zusammenfassung pro Thread  
 In dieser Registerkarte zeigt eine farbcodierte Spaltenansicht die Gesamtzeit an, die die einzelnen Threads im ausführenden oder blockierten Zustand, in der E/A oder anderen Zuständen verbracht haben. Die Spalten sind unten beschriftet. Wenn Sie die Zoomstufe im Zeitachsendiagramm anpassen, wird die Registerkarte automatisch aktualisiert. Auf einigen Zoomstufe werden mehrere Threads möglicherweise nicht angezeigt. In diesem Fall werden auf der rechten Seite Auslassungszeichen angezeigt. Wenn der gewünschte Thread nicht angezeigt wird, können Sie andere Threads ausblenden. Weitere Informationen finden Sie unter [Zusammenfassungsbericht pro Thread](../profiling/per-thread-summary-report.md).  
  
#### <a name="disk-operations"></a>Datenträgervorgänge  
 In dieser Registerkarte wird unter anderem angezeigt, welche Prozesse und Threads durch den aktuellen Prozess an der Datenträger-E/A beteiligt waren, welche Dateien davon betroffen waren (z.B. DLLs, die geladen wurden) und wie viele Bytes gelesen wurden. Sie können diesen Bericht verwenden, um die Zeit auszuwerten, die während der Ausführung für den Zugriff auf Dateien aufgewendet wird, insbesondere wenn der Prozess E/A-gebunden scheint. Weitere Informationen finden Sie unter [Bericht über Datenträgervorgänge](../profiling/disk-operations-report-threads-view.md).  
  
## <a name="see-also"></a>Siehe auch  
 [Parallelitätsschnellansicht](../profiling/concurrency-visualizer.md)