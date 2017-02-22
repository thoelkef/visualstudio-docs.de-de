---
title: "Threadansicht (Parallele Leistung) | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.performance.view.threadblocking"
helpviewer_keywords: 
  - "Nebenläufigkeitsschnellansicht, Threadansicht (Parallele Leistung)"
ms.assetid: 2e441103-a266-407b-88c3-fb58716257a3
caps.latest.revision: 21
caps.handback.revision: 21
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# Threadansicht (Parallele Leistung)
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Threadansicht ist die detaillierteste und der Funktionreichen Ansicht in der Parallelitätsschnellansicht.  In dieser Ansicht verwenden, können Sie feststellen, ob die Threads blockiert sind, ausgeführt werden oder aufgrund von Synchronisierungs\-, E\/A\- oder anderen Gründen.  
  
 Während der Profilanalyse werden von der Parallelitätsschnellansicht alle Betriebssystem\-Kontextwechselereignisse für alle Anwendungsthreads untersucht.  Kontextwechsel können aus vielen Gründen, z diese auftreten:  
  
-   Ein Thread wird für einen Synchronisierungsprimitiven blockiert.  
  
-   Das Quantum eines Threads läuft ab.  
  
-   Von einem Thread erfolgt eine blockierende E\/A\-Anforderung.  
  
 Threadansicht wird jedem Kontextwechsel eine Kategorie zugewiesen, wenn die Ausführung eines Threads beendet wurde.  Die Kategorien werden in der Legende im unteren linken Teil der Ansicht angezeigt.  Die Parallelitätsschnellansicht kategorisiert Kontextwechselereignisse, indem die Aufrufliste des Threads nach bekannten blockierenden APIs durchsucht.  Wenn keine Aufruflistenabgleichung gibt, wird der Wartevorgangsgrund, der vom [!INCLUDE[TLA#tla_mswin](../code-quality/includes/tlasharptla_mswin_md.md)] bereitgestellt wird, verwendet.  jedoch unter Umständen die Kategorie [!INCLUDE[TLA#tla_mswin](../code-quality/includes/tlasharptla_mswin_md.md)] kann auf einem Implementierungsdetail und nicht die Absicht des Benutzers.  Beispielsweise meldet den [!INCLUDE[TLA#tla_mswin](../code-quality/includes/tlasharptla_mswin_md.md)] Wartevorgangsgrund für das Blockieren in einer systemeigenen Slim Lese\-\/Schreibsperren als E\/A anstelle der Synchronisierung.  In den meisten Fällen können Sie die Ursache eines blockierenden Ereignis identifizieren, indem Sie die Aufruflisten, überprüfen die Kontextwechselereignissen entsprechen.  
  
 Die Threadansicht werden auch Abhängigkeiten zwischen Threads angezeigt.  Wenn Sie beispielsweise einen Thread identifizieren, der in einem Synchronisierungsobjekt blockiert wird, können Sie nach dem Thread suchen, der das die Blockierung Nicht zugewiesen, und Sie können die Aktivität auf der Aufrufliste für diesen Thread am Punkt überprüfen, als er das andere die Blockierung Unterstützen.  
  
 Wenn Threads ausführen, sammelt die Parallelitätsschnellansicht Beispiele.  In der Threadansicht können Sie analysieren, das Code von einer oder mehrere Threads während eines Ausführungssegments ausgeführt wird.  Sie können das Blockieren von Berichten und Berichten auch überprüfen, die Aufruflistenstrukturausführung ein Profil erstellen.  
  
## Verwendung  
 Im Folgenden einige Methoden, dass Sie die Threadansicht verwenden können:  
  
-   Identifizieren von Gründen, warum die Benutzeroberfläche \(UI\) eine App in bestimmten Ausführungsphasen nicht reagiert ist.  
  
-   Identifizieren der Zeitspanne, die auf das Blockieren der Synchronisierung, E\/A, Seitenfehler und anderen Ereignissen.  
  
-   Identifizieren des Grades an Interferenz von anderen Prozessen, die auf dem System ausgeführt werden.  
  
-   Identifizieren von Problemen mit dem Lastenausgleich bei einer parallelen Ausführung.  
  
-   Identifizieren der Gründe für Skalierbarkeit, die optimale oder nicht vorhanden ist \(beispielsweise, warum sich die Leistung einer parallelen Anwendung nicht verbessert, wenn mehr logische Kerne verfügbar sind\).  
  
-   Verstehen des Parallelitätsgrades in der App, um die Parallelisierung zu unterstützen.  
  
-   Verstehen der Abhängigkeiten zwischen Arbeitsthreads und kritischen Pfaden der Ausführung  
  
## Untersuchen bestimmte Zeitintervalle und Threads  
 Die Threadansicht wird eine Zeitachse an.  Sie können in der Zeitachse vergrößern und schwenken, um bestimmte Jahresintervalle und Threads der Anwendung zu überprüfen.  Auf der x\-Achse Zeit ist und auf der Y\-Achse sind einige Kanal:  
  
-   Zwei E\/A\-Channels für jedes Laufwerk im System, ein Kanal für liest und eines für Schreiben.  
  
-   Ein Channel für jeden Thread des Prozesses.  
  
-   Markerchannel, wenn Markerereignisse in der Ablaufverfolgung gibt.  Markerchannel werden zuerst unter den Threadchannels, die diese Ereignisse generierten.  
  
-   GPU\-Channel.  
  
 Hier sehen Sie eine Abbildung der Threadansicht:  
  
 ![Threadansicht](../profiling/media/threadsviewnarrowing.png "ThreadsViewNarrowing")  
Threadansicht  
  
 Zuerst werden die Threads in der Reihenfolge sortiert, in der sie erstellt werden, sodass der Hauptanwendungsthread erster ist.  Sie können die Sortierungsoption in der linken oberen Ecke der Ansicht verwenden, Threads nach einem anderen Kriterium sortieren \(beispielsweise, von den größten ausgeführt\).  
  
 Sie können Threads ausblenden, die Arbeit nicht ausführen, indem Sie links die Namen in der Spalte auswählen und dann die Schaltfläche **Ausgewählte Threads ausblenden** auf der Symbolleiste auswählen.  Es wird empfohlen, dass Sie Threads ausblenden, die vollständig blockiert werden, da ihre Statistik nicht relevant und Berichten verstopfen kann.  
  
 Um zusätzliche Threads ermitteln um, in der aktiven Legende auszublenden, wählen Sie den Bericht **Zusammenfassung pro Thread** über die Registerkarte **Profilbericht**.  Dadurch wird das Anzeigen des Ausführungsaufteilungsdiagramms an, das den Zustand von Threads für das derzeit ausgewählte Zeitintervall anzeigt.  Auf einigen Zoomstufen würden mehrere Threads möglicherweise nicht angezeigt.  Wenn dies auftritt, werden Auslassungszeichen rechts angezeigt.  
  
 Wenn Sie ein Intervall Zeitpunkt und mehrerer Threads in diese ausgewählt haben, können Sie die Leistungsanalyse beginnen.  
  
## Analyse\-Tools  
 Dieser Abschnitt beschreibt Berichte und andere Analysetools.  
  
### Details zur Threadblockierung  
 Um Informationen über ein blockierendes Ereignis in einem bestimmten Bereich auf einem Thread abzurufen, kommunizieren Sie auf diesem Bereich ruhen lassen um eine QuickInfo anzuzeigen.  Sie enthält Informationen wie Kategorie, die Blockierungen, Dauer und eine blockierende API, sofern vorhanden.  Wenn dem blockierenden Bereich auswählen, wird der Stapel zu diesem Zeitpunkt im unteren Bereich, zusammen mit den gleichen Informationen angezeigt, die in der QuickInfo angezeigt wird.  Durch eine Untersuchung der Aufrufliste können Sie den Grund für das den Thread blockierende Ereignis bestimmen.  Sie können zusätzliche Prozess und Thread suchen, indem Sie das Segment auswählen und die aktuelle Registerkarte überprüfen.  
  
 Ein Ausführungspfad hat möglicherweise mehreren blockierenden Ereignissen.  Sie können diese durch Blockierungskategorie überprüfen, damit Sie Problembereiche schneller finden.  Wählen Sie einfach eine der blockierenden Kategorien in der Legende links aus.  
  
### Abhängigkeiten zwischen Threads  
 Die Parallelitätsschnellansicht kann Abhängigkeiten zwischen Threads in Ihrem Prozess, damit Sie feststellen können, was ein blockierter Thread versucht, auszuführen und zu erfahren, was anderer Thread ermöglicht haben, um sie auszuführen.  Um festzustellen die sämtlichen Unterstützen eines anderen Threads, das relevante Blockierungssegment die Blockierung.  Wenn die Parallelitätsschnellansicht den die Blockierung aufhebenden Thread bestimmen kann, zeichnet sie eine Zeile zwischen dem die Blockierung aufhebenden Thread und dem ausgeführten Segment, das dem blockierenden Segment folgt.  Darüber hinaus zeigt die Registerkarte **Stapelblockierung wird aufgehoben.** die relevante Aufrufliste angezeigt.  
  
### Details zur Threadausführung  
 Im Zeitachsendiagramm eines Threads, stellen die grüne Segmente dar, als er Code ausführte.  Sie können ausführlichere Informationen über ein Ausführungssegment abrufen.  
  
 Wenn Sie einen Punkt in ein Ausführungssegment auswählen, durchsucht die Parallelitätsschnellansicht dass Zeitpunkt auf die relevante Aufrufliste wird dann ein schwarzes Caretzeichen über dem ausgewählten Punkt im Ausführungssegment angezeigt und die Aufrufliste selbst auf der Registerkarte **Aktueller Stapel** an.  Sie können mehrere Punkte auf dem Ausführungssegment auswählen.  
  
> [!NOTE]
>  Die Parallelitätsschnellansicht kann nicht in der Lage, eine Auswahl auf ein Ausführungssegment aufzulösen.  In der Regel tritt dies auf, wenn die Dauer des Segments weniger als eine Millisekunde ist.  
  
 So ein Ausführungsprofil für alle aktiviert abzurufen \(eingeblendet\) Tabellen im momentan ausgewählten Zeitraum, die Schaltfläche **Ausführung** in der aktiven Legende.  
  
### Zeitachsendiagramm  
 Im Zeitachsendiagramm wird die Aktivität aller Threads im Prozess sowie aller physischen Laufwerke auf dem Hostcomputer angezeigt.  Außerdem wird GPU\-Aktivitäts\- und \-Markerereignisse an.  können Sie vergrößern, um weitere Details anzuzeigen oder jetzt ein Intervall der die Zeit abgelaufen anzuzeigen.  Sie können Punkte im Diagramm auch auswählen, um Details zu Kategorien, Startzeiten, Dauer und Aufruflistenzustände abzurufen.  
  
 Im Zeitachsendiagramm gibt eine Farbe den Status eines Threads zu einem bestimmten Zeitpunkt an.  Beispielsweise können grüne Segmente aus, wurden rote Segmente für Synchronisierung blockiert, gelbe Segmente wurden entfernt, und klicken mit Geräte\-E\/A beschäftigt.  Sie können diese Ansicht verwenden, um die Bilanz der Arbeit mithilfe Threads zu überprüfen, die in einer parallelen Schleife oder in gleichzeitige Aufgaben ausführen werden.  Wenn ein Thread, um mehr Zeit als andere abzuschließen, kann die Arbeit unausgewogen.  Sie können diese Informationen verwenden, um die Leistung des Programms zu verbessern, indem Sie gleichmäßiger Arbeit unter den Threads verteilen.  
  
 Wenn nur ein Thread \(also ausgeführt wird\) zu einem Zeitpunkt grün ist, wird möglicherweise die App nicht vollem Umfang der Parallelität im System.  Sie können das Zeitachsendiagramm verwenden, um Abhängigkeiten zwischen Threads und den temporären Beziehungen zwischen den blockierenden und blockierten Threads untersuchen.  Um Threads neu anzuordnen, wählen Sie einen Thread und anschließend auf der Symbolleiste auswählen, das auf oder ab Knöpfung aus.  Um Threads ausgeblendet, und wählen Sie dann die Schaltfläche **Threads ausblenden** aus.  
  
### Profilberichte  
 Unter dem Zeitachsendiagramm ist ein Zeitachsenprofil und ein Bereich, der für verschiedene Registerkarten Berichten.  Die Berichte werden automatisch aktualisiert, während Sie die Threadansicht ändern.  Für große Ablaufverfolgungen kann der Berichtsbereich nicht verfügbar, die während Aktualisierungen abgeleitet werden.  Jeder Bericht stehen zwei Filteranpassungen: Rauschunterdrückung und Nur mein Code.  Verwendungsrauschunterdrückung, um von Aufrufstruktureinträgen herauszufiltern, in die nur wenig Zeit aufgewendet wird.  Der Standardfilterwert ist 2 Prozent, jedoch von 0 bis 99 % anpassen.  Um nur die Aufrufstruktur für den Code anzuzeigen, aktivieren Sie das Kontrollkästchen **Nur eigenen Code**.  Um alle Aufrufstrukturen anzuzeigen, löschen Sie sie.  
  
#### Profilbericht  
 Diese Registerkarte werden Berichte angezeigt, die den Einträgen in der aktiven Legende entsprechen.  Um einen Bericht anzuzeigen, wählen Sie einen der Einträge.  
  
#### Aktueller Stapel  
 Diese Registerkarte zeigt die Aufruflisten für einen Punkt auf einem ausgewählten Threadsegment im Zeitachsendiagramm an.  Die Aufruflisten werden abgeschnitten, um nur Aktivität anzuzeigen, die dem Programm verknüpft ist.  
  
#### Stapelblockierung wird aufgehoben  
 Um an welcher Thread die Blockierung des ausgewählten Threads haben und in welcher Codezeile anzuzeigen, wählen Sie die Registerkarte **Stapelblockierung wird aufgehoben.**.  
  
#### Ausführung  
 Der Ausführungsbericht zeigt der Aufteilung der Zeit die Anwendung an, die im Testlauf aufgewendet wird.  
  
 Um die Codezeile zu suchen der Ausführungszeit entfällt, erweitern Sie die Aufrufstruktur, und klicken Sie dann im Kontextmenü für den Aufrufstruktureintrag, wählen Sie **Aufrufsites anzeigen** oder **Quelle anzeigen** aus.  **Quelle anzeigen** sucht die ausgeführte Codezeile.  **Aufrufsites anzeigen** wird die Codezeile gesucht, die ausgeführte Codezeile aufgerufen wurden.  Wenn nur eine Aufrufsite vorhanden ist, wird die Codezeile hervorgehoben.  Wenn mehrere Aufrufsites vorhanden sind, können Sie den Knoten auswählen, das Sie im Dialogfeld, möchten, und dann die Schaltfläche **Zu Quelle wechseln** wählen, um den Aufrufsitecode hervorzuheben.  Es ist häufig nützlich, die Aufrufsite zu suchen, die den meisten Instanzen, die meiste Zeit oder beide hat.  Weitere Informationen finden Sie unter [Ausführungsprofilbericht](../profiling/execution-profile-report.md).  
  
#### Synchronisierung  
 Der Synchronisierungsbericht zeigt die Aufrufe, die Blockierungen der Synchronisierung verursachen, sowie die aggregierten Blockierungszeiten der einzelnen Aufruflisten.  Weitere Informationen finden Sie unter [Synchronisierungszeit](../profiling/synchronization-time.md).  
  
#### E\/A  
 Der E\/A\-Bericht zeigt die Aufrufe, die E\/A\-Blockierungen verursachen, sowie die aggregierten Blockierungszeiten der einzelnen Aufruflisten.  Weitere Informationen finden Sie unter [E\/A\-Zeit \(Threadansicht\)](../profiling/i-o-time-threads-view.md).  
  
#### Sleep  
 Der Bericht zum Standbymodus zeigt die Aufrufe, die Blockierung des Standbymodus verursachen, sowie die aggregierten Blockierungszeiten der einzelnen Aufruflisten.  Weitere Informationen finden Sie unter [Standbyzeit](../profiling/sleep-time.md).  
  
#### Speicherverwaltung  
 Der Speicherverwaltungsbericht enthält die Aufrufe, bei denen Speicherverwaltungsblöcke aufgetreten sind, sowie die aggregierten Blockierungszeiten der einzelnen Aufruflisten.  Sie können diese Informationen verwenden, um Bereiche zu identifizieren, die eine übermäßige Paging\- oder Garbage Collection verwendet haben.  Weitere Informationen finden Sie unter [Speicherverwaltungszeit](../profiling/memory-management-time.md).  
  
#### Vorzeitige Entfernung  
 Der Bericht für die vorzeitige Entfernung enthält den Instanzen an, wohin Prozesse im System den aktuellen Prozess sowie die Einzelpersonenthreads benannt, die Threads in aktuellem Prozess ersetzten.  Sie können diese Informationen verwenden, um die Prozesse und die Threads zu identifizieren, die für die vorzeitige Entfernung am zuständigsten sind.  Weitere Informationen finden Sie unter [Zeit für die vorzeitige Entfernung](../profiling/preemption-time.md).  
  
#### Benutzeroberflächenverarbeitung  
 Der Bericht zur Benutzeroberflächenverarbeitung enthält die Aufrufe, durch die eine Blockierung der Benutzeroberflächenverarbeitung verursacht wird, sowie die aggregierten Blockierungszeiten der einzelnen Aufruflisten.  Weitere Informationen finden Sie unter [Benutzeroberflächenverarbeitungszeit](../profiling/ui-processing-time.md).  
  
#### Zusammenfassung pro Thread  
 Diese Registerkarte zeigt eine farbcodierte Spaltenansicht der Gesamtzeit dass jeder Thread, der in der Ausführung ausgegeben wird, blockiert, in der E\/A und anderen Zustände.  Die Spalten sind unten beschriftet.  Wenn Sie die Zoomstufe im Zeitachsendiagramm anpassen, wird die Registerkarte automatisch aktualisiert.  Auf einigen Zoomstufen würden mehrere Threads möglicherweise nicht angezeigt.  Wenn dies auftritt, werden Auslassungszeichen rechts angezeigt.  Wenn der Thread, den Sie möchten, nicht, können Sie andere Threads ausblenden wird.  Weitere Informationen finden Sie unter [Zusammenfassungsbericht pro Thread](../profiling/per-thread-summary-report.md).  
  
#### Datenträgervorgänge  
 Diese Registerkarte zeigt, welche Prozesse und Threads in Datenträger\-E\/A im Namen des Stromprozesses beteiligt waren, den betroffenen Dateien \(beispielsweise, DLLs an, die geladen wurden\), Anzahl der gelesenen Bytes und weitere Informationen.  Sie können diesen Bericht verwenden, um die Auswertung der Zeit, die aufgewendet wird, wenn es während der Ausführung für den Zugriff, insbesondere wenn der Prozess E\/A\-gebunden scheint, die sein.  Weitere Informationen finden Sie unter [Bericht über Datenträgervorgänge](../profiling/disk-operations-report-threads-view.md).  
  
## Siehe auch  
 [Parallelitätsschnellansicht](../profiling/concurrency-visualizer.md)