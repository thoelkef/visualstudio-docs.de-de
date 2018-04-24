---
title: Tools zum Debuggen von Threads und Prozessen | Microsoft Docs
ms.custom: ''
ms.date: 04/21/2017
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- multiprocess debugging
- threading [Visual Studio], debugging
- processes, debugging
- debugging threads
- debugging [Visual Studio], threads
ms.assetid: 9f0c8505-b6b2-452b-adfd-076db14d8115
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: f42159b15bbba4bd092dcde34404459212e26ab3
ms.sourcegitcommit: 3d10b93eb5b326639f3e5c19b9e6a8d1ba078de1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/18/2018
---
# <a name="tools-to-debug-threads-and-processes-in-visual-studio"></a>Tools zum Debuggen von Threads und Prozessen in Visual Studio
*Threads* und *Prozesse* sind verwandte Konzepte der Informatik. Beide stellen Folgen von Anweisungen dar, die in einer bestimmten Reihenfolge ausgeführt werden müssen. Anweisungen von verschiedenen Threads oder Prozessen können aber parallel ausgeführt werden.  
  
 Prozesse werden im Betriebssystem verwaltet und entsprechen dem, was Benutzer als Programme oder Anwendungen sehen. Ein Thread hingegen wird von einem Prozess verwaltet. Aus diesem Grund Threads werden manchmal als *Lightweightprozesse*. Jeder Prozess besteht aus einem oder mehreren Threads.  
  
 Die Möglichkeit, mehrere Prozesse auszuführen, versetzt einen Computer in die Lage, mehr als eine Aufgabe gleichzeitig auszuführen. Das Vorhandensein mehrerer Threads versetzt einen Prozess in die Lage, Arbeiten so aufzuteilen, dass sie parallel ausgeführt werden können. Auf einem Computer mit Multiprozessoren können Prozesse oder Threads auf verschiedenen Prozessoren ausgeführt werden. Dies ermöglicht eine echte Parallelverarbeitung.  
  
 Echte Parallelverarbeitung ist nicht immer möglich. Threads müssen manchmal synchronisiert werden. Ein Thread muss möglicherweise auf das Ergebnis eines anderen Threads warten, oder ein Thread benötigt exklusiven Zugriff auf eine Ressource, die von einem anderen Thread verwendet wird. Synchronisierungsprobleme sind eine häufige Ursache von Programmfehlern in Multithreadanwendungen. Es kann passieren, dass Threads auf eine Ressource warten, die nie verfügbar wird. Dies führt zu einer Bedingung aufgerufen *Deadlock*.  
  
 Der [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]-Debugger stellt leistungsstarke und benutzerfreundliche Tools zum Debuggen von Threads und Prozessen bereit.  
  
## <a name="tools-and-features"></a>Tools und Funktionen
Die Tools Sie zur Verwendung in müssen [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] abhängig, welche Art von Code, die gesuchten Debuggen:

- Für Prozesse, die wichtigsten Tools sind die **an den Prozess anhängen** (Dialogfeld), die **Prozesse** Fenster, und die **Debugspeicherort** Symbolleiste.

- Für Threads, die wichtigsten Tools zum Debuggen von Threads sind die **Threads** , Threadmarker in Quellcodefenstern **parallele Stapel** Fenster **parallele Überwachung** Fenster, und die **Debugspeicherort** Symbolleiste.  
  
- Für Code, verwendet der <xref:System.Threading.Tasks.Task> in der [Task Parallel Library (TPL)](/dotnet/standard/parallel-programming/task-parallel-library-tpl), [Concurrency Runtime](/cpp/parallel/concrt/concurrency-runtime/) (systemeigener Code), die wichtigsten Tools zum Debuggen von Multithreadanwendungen sind die **Parallele Stapel** Fenster die **parallele Überwachung** Fenster, und die **Aufgaben** Fenster (der **Aufgaben** Fenster unterstützt auch die JavaScript Promise-Objekt).

- Ist das wichtigste Tool zum Debuggen von Threads auf dem GPU, die **GPU-Threads** Windows.  
  
 In der folgenden Tabelle sind die verfügbaren Informationen und die an jeder Stelle möglichen Aktionen aufgeführt:  
  
|Benutzeroberfläche|Verfügbare Informationen|Ausführbare Aktionen|  
|--------------------|---------------------------|-----------------------------|  
|**Anfügen an Prozess** (Dialogfeld)|Verfügbare Prozesse, an die angehängt werden kann:<br /><br /> -Prozessnamen (.exe)<br />-Prozess-ID-Nummer<br />-Menüleistentitel<br />-Typ (Managed v4. 0; Managed v2. 0, v1. 1, v1. 0; X86; X64; IA64)<br />-Benutzername (Kontoname)<br />-Die Nummer Sitzung|Auswählen eines Prozesses, an den angehängt werden soll<br /><br /> Auswählen eines Remotecomputers<br /><br /> Ändern des Transporttyps für die Verbindung mit Remotecomputern|  
|**Prozesse** Fenster|Angehängte Prozesse:<br /><br /> -Verarbeitenden Prozessnamen an.<br />-Prozess-ID-Nummer<br />-Pfad zur .exe des Prozesses<br />-Menüleistentitel<br />-Zustand (unterbrechen. Aktiv)<br />-Debuggen (systemeigen, verwaltet, und So weiter.)<br />-Transporttyp (standardmäßig, systemeigen ohne Authentifizierung)<br />-Transportqualifizierer (Remotecomputer)|Tools:<br /><br /> -Anfügen<br />-Trennen<br />– Beenden<br /><br /> Kontextmenü:<br /><br /> -Anfügen<br />-Trennen<br />– Nach Beenden des Debuggens trennen<br />– Beenden|  
|**Threads** Fenster|Threads in aktuellem Prozess:<br /><br /> -Thread ID<br />-Verwaltete ID<br />-Kategorie (Hauptthread, Benutzeroberflächenthread, Remoteprozeduraufruf-Handler oder Arbeitsthread)<br />-Thread Name<br />-Speicherort, in dem Thread erstellt wird<br />-Priorität<br />-Affinitätsmaske<br />-Unterbrechungszähler<br />-Verarbeitenden Prozessnamen an.<br />-Kennzeichenindikator<br />-Angehaltener Indikator|Tools:<br /><br /> -Suche<br />-Aufrufliste suchen<br />-Nur eigenen Code kennzeichnen<br />-Benutzerdefinierte Modulauswahl kennzeichnen<br />-Gruppieren nach<br />-Spalten<br />-Aufruflisten erweitern/reduzieren<br />-Gruppen erweitern/reduzieren<br />-Sperren/Entsperren von Threads<br /><br /> Kontextmenü:<br /><br /> -Threads in Quelle anzeigen<br />– Zu Thread wechseln<br />-Ausgeführten Thread Sperren<br />-Gesperrten Thread entsperren<br />-Flag einen Thread zur weiteren Überprüfung kennzeichnen<br />-Kennzeichnung eines Threads aufheben<br />-Thread umbenennen<br />-Threads anzeigen und ausblenden<br /><br /> Sonstige Aktionen:<br /><br /> -Die Aufrufliste für einen Thread in einem DataTip anzeigen|  
|Quellcodefenster|Threadindikatoren im linken Bundsteg geben einzelne oder mehrere Threads (standardmäßig aktiviert, indem Sie mithilfe von "Kontextmenü" im deaktiviert **Threads** Fenster)|Kontextmenü:<br /><br /> – Zu Thread wechseln<br />-Flag einen Thread zur weiteren Überprüfung kennzeichnen<br />-Kennzeichnung eines Threads aufheben|  
|**Debugspeicherort** Symbolleiste|– Der aktuelle Prozess<br />-Die Anwendung anhalten<br />-Anwendung fortsetzen<br />-Anhalten und Herunterfahren der Anwendung<br />– Der aktuelle thread<br />-Ein-/ausschalten aktuelle Threadzustand-flag<br />-Nur gekennzeichnete Threads anzeigen<br />-Nur aktuellen Prozess anzeigen<br />– Der aktuelle Stapelrahmen|-Wechseln Sie zu einem anderen Prozess<br />-Anhalten, fortsetzen oder Beenden der Anwendung<br />-Wechseln Sie zu einem anderen Thread im aktuellem Prozess<br />-Wechseln Sie zu anderem Stapelrahmen in aktuellem thread<br />-Kennzeichnen bzw. Aufheben der Kennzeichnung aktuellen threads<br />-Nur gekennzeichnete Threads anzeigen<br />-Nur den aktuellen Prozess anzeigen|  
|**Parallele Stapel** Fenster|-Aufruflisten Sie für mehrere Threads in einem Fenster.<br />-Aktiven Stapelrahmen für jeden Thread.<br />-Aufrufer und aufgerufenen für eine beliebige Methode.|-Herausfiltern Sie bestimmter threads<br />-Wechseln Sie zur Ansicht Aufgaben<br />-Kennzeichnen bzw. Aufheben der Kennzeichnung eines Threads<br />/ Vergrößern|   
|**Parallele Überwachung** Fenster|-Die Kennzeichenspalte, in der Sie einen Thread markieren können, dem besondere Aufmerksamkeit erhalten soll werden sollen.<br />-Die framespalte, in der ein Pfeil den ausgewählten Frame angibt.<br />-Eine konfigurierbare Spalte, die die Computer, Prozess-Kachel, Aufgabe und Thread angezeigt werden kann.|-Kennzeichnen bzw. Aufheben der Kennzeichnung eines Threads<br />-Nur gekennzeichnete Threads anzeigen<br />-Frames wechseln<br />-Beim Sortieren einer Spalte<br />-Die Gruppe von threads<br />-Threads einfrieren oder reaktivieren<br />-die Daten in das parallele Überwachungsfenster exportieren| 
|**Aufgaben** Fenster|– Anzeigen von Informationen zu <xref:System.Threading.Tasks.Task> Objekte einschließlich des Task-ID, des Aufgabenstatus (geplant, ausgeführt, wartend, blockiert) und Bestimmung des Threads, die dem Vorgang zugewiesen ist.<br />– Der aktuelle Speicherort in der Aufrufliste.<br />-Delegat, die zum Zeitpunkt der Erstellung an die Aufgabe übergeben|-Wechseln Sie zur aktuellen Aufgabe<br />-Kennzeichnen bzw. Aufheben der Kennzeichnung einer Aufgabe<br />-Einfrieren oder Reaktivieren einer Aufgabe|  
|**GPU-Threads** Fenster|-Die Kennzeichenspalte, in der Sie einen Thread markieren können, dem besondere Aufmerksamkeit erhalten soll werden sollen.<br />– Der aktuelle Thread-Spalte, die in der ein gelber Pfeil gibt den aktuellen Thread an.<br />– Der **Threadanzahl** Spalte, die die Anzahl der Threads an derselben Position anzeigt.<br />– Der **Zeile** Spalte, die die Zeile des Codes angezeigt wird, in dem jede Gruppe von Threads befindet.<br />– Der **Adresse** Spalte, der die Anweisungsadresse angezeigt, wobei jede Gruppe von Threads befindet.<br />– Der **Speicherort** Spalte, die den Speicherort im Code, der die Adresse ist.<br />– Der **Status** Spalte, die zeigt, ob der Thread aktiv oder blockiert ist.<br />– Der **Kachel** Spalte, der der kachelindex für die Threads in der Zeile angezeigt wird.|– Ändern Sie zu einem anderen thread<br />-Zeigt eine bestimmte Kachel und bestimmten thread<br />– Anzeigen oder Ausblenden einer Spalte<br />-Sortieren nach einer Spalte<br />-Die Gruppe von threads<br />-Threads einfrieren oder reaktivieren<br />-Kennzeichnen bzw. Aufheben der Kennzeichnung eines Threads<br />-Nur gekennzeichnete Threads anzeigen|  
  
## <a name="see-also"></a>Siehe auch  
 [Fügen an laufende Prozesse an](../debugger/attach-to-running-processes-with-the-visual-studio-debugger.md)   
 [Debuggen von Multithreadanwendungen](../debugger/debug-multithreaded-applications-in-visual-studio.md)   
 [Debuggen von GPU-Code](../debugger/debugging-gpu-code.md)