---
title: Debuggen von Threads und Prozessen | Microsoft-Dokumentation
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- FSharp
- VB
- CSharp
- C++
helpviewer_keywords:
- multiprocess debugging
- threading [Visual Studio], debugging
- processes, debugging
- debugging threads
- debugging [Visual Studio], threads
ms.assetid: 9f0c8505-b6b2-452b-adfd-076db14d8115
caps.latest.revision: 18
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 711aaeaa76edbb4ea9d070254213f9a7207e12f9
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/12/2018
ms.locfileid: "49191489"
---
# <a name="debug-threads-and-processes"></a>Debuggen von Threads und Prozessen
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Threads * und *Prozesse* sind verwandte Konzepte in Computerwissenschaften absolvierte. Beide stellen Folgen von Anweisungen dar, die in einer bestimmten Reihenfolge ausgeführt werden müssen. Anweisungen von verschiedenen Threads oder Prozessen können aber parallel ausgeführt werden.  
  
 Prozesse werden im Betriebssystem verwaltet und entsprechen dem, was Benutzer als Programme oder Anwendungen sehen. Ein Thread hingegen wird von einem Prozess verwaltet. Aus diesem Grund Threads werden manchmal auch bezeichnet als *Lightweightprozesse*. Jeder Prozess besteht aus einem oder mehreren Threads.  
  
 Die Möglichkeit, mehrere Prozesse auszuführen, versetzt einen Computer in die Lage, mehr als eine Aufgabe gleichzeitig auszuführen. Das Vorhandensein mehrerer Threads versetzt einen Prozess in die Lage, Arbeiten so aufzuteilen, dass sie parallel ausgeführt werden können. Auf einem Computer mit Multiprozessoren können Prozesse oder Threads auf verschiedenen Prozessoren ausgeführt werden. Dies ermöglicht eine echte Parallelverarbeitung.  
  
 Echte Parallelverarbeitung ist nicht immer möglich. Threads müssen manchmal synchronisiert werden. Ein Thread muss möglicherweise auf das Ergebnis eines anderen Threads warten, oder ein Thread benötigt exklusiven Zugriff auf eine Ressource, die von einem anderen Thread verwendet wird. Synchronisierungsprobleme sind eine häufige Ursache von Programmfehlern in Multithreadanwendungen. Es kann passieren, dass Threads auf eine Ressource warten, die nie verfügbar wird. Dies führt zu einer Bedingung aufgerufen *Deadlock*.  
  
 Der [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]-Debugger stellt leistungsstarke und benutzerfreundliche Tools zum Debuggen von Threads und Prozessen bereit.  
  
## <a name="tools-for-debugging-threads-and-processes-in-visual-studio"></a>Tools zum Debuggen von Threads und Prozessen in Visual Studio  
 Die wichtigsten Tools für die Arbeit mit Prozessen in [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] sind die **an den Prozess anhängen** im Dialogfeld die **Prozesse** Fenster, und die **Debugspeicherort** Symbolleiste. Die wichtigsten Tools zum Debuggen von Threads sind die **Threads** , Threadmarker in Quellcodefenstern und **Debugspeicherort** Symbolleiste.  
  
 Die wichtigsten Tools zum Debuggen von Multithreadanwendungen sind die **parallele Stapel** und **Parallele Aufgaben**, **parallele Überwachung**, und **GPU-Threads** Windows.  
  
 In der folgenden Tabelle sind die verfügbaren Informationen und die an jeder Stelle möglichen Aktionen aufgeführt:  
  
|Benutzeroberfläche|Verfügbare Informationen|Ausführbare Aktionen|  
|--------------------|---------------------------|-----------------------------|  
|**An den Prozess anhängen** (Dialogfeld)|Verfügbare Prozesse, an die angehängt werden kann:<br /><br /> -Prozessnamen (.exe)<br />-Prozess-ID-Nummer<br />-Menüleistentitel<br />-Typ (Managed v4. 0; Managed v2. 0, v1. 1, v1. 0; X86; X64; IA64)<br />-Benutzername (Kontoname)<br />-Die Nummer Sitzung|Auswählen eines Prozesses, an den angehängt werden soll<br /><br /> Auswählen eines Remotecomputers<br /><br /> Ändern des Transporttyps für die Verbindung mit Remotecomputern|  
|**Prozesse** Fenster|Angehängte Prozesse:<br /><br /> -Name Prozesses<br />-Prozess-ID-Nummer<br />-Path .exe verarbeiten<br />-Menüleistentitel<br />-Zustand (unterbrechen. Aktiv)<br />-Debuggen (systemeigen, verwaltet, und So weiter.)<br />-Transporttyp (standardmäßig, systemeigen ohne Authentifizierung)<br />-Transportqualifizierer (Remotecomputer)|Tools:<br /><br /> : Fügen Sie<br />-Trennen<br />-Beenden<br /><br /> Kontextmenü:<br /><br /> : Fügen Sie<br />-Trennen<br />-Trennen Sie, wenn das Debuggen beendet<br />-Beenden|  
|**Threads** Fenster|Threads in aktuellem Prozess:<br /><br /> -Thread-ID<br />– Verwaltete ID<br />-Kategorie (Hauptthread, Benutzeroberflächenthread, Remoteprozeduraufruf-Handler oder Arbeitsthread)<br />-Threadname<br />-Location, in dem Thread erstellt wird<br />-Priorität<br />-Affinitätsmaske<br />-Angehaltene Anzahl<br />-Name Prozesses<br />: Indikator kennzeichnen<br />-Angehaltener Indikator|Tools:<br /><br /> -Suche<br />-Aufrufliste suchen<br />-Nur eigenen Code kennzeichnen<br />: Benutzerdefinierte Modulauswahl kennzeichnen<br />-Gruppieren<br />-Spalten<br />-Aufruflisten von aufklappen/Zuklappen<br />-Gruppen erweitern/reduzieren<br />-Sperren/Entsperren von Threads<br /><br /> Kontextmenü:<br /><br /> -Threads in Quelle anzeigen<br />-Wird zu Thread wechseln.<br />-Ausgeführten Thread Sperren<br />-Gesperrten Thread entsperren<br />-Kennzeichnen Sie einen Thread zur weiteren Überprüfung<br />-Kennzeichnung eines Threads aufheben<br />-Thread umbenennen<br />: Threads anzeigen und ausblenden<br /><br /> Sonstige Aktionen:<br /><br /> -Die Aufrufliste für einen Thread in einem DataTip anzeigen|  
|Quellcodefenster|Threadindikatoren im linken Bundsteg geben einzelne oder mehrere Threads (standardmäßig aktiviert, verwenden im Kontextmenü deaktiviert **Threads** Fenster)|Kontextmenü:<br /><br /> -Wird zu Thread wechseln.<br />-Kennzeichnen Sie einen Thread zur weiteren Überprüfung<br />-Kennzeichnung eines Threads aufheben|  
|**Debugspeicherort** Symbolleiste|– Der aktuelle Prozess<br />-Die Anwendung anhalten<br />-Anwendung fortsetzen<br />-Anhalten und Herunterfahren der Anwendungs<br />– Der aktuelle thread<br />-Umschalten des aktuellen Status der Thread-flag<br />: Nur gekennzeichnete Threads anzeigen<br />-Nur aktuellen Prozess anzeigen<br />– Der aktuelle Stapelrahmen|-Wird zu einem anderen Prozess wechseln.<br />-Anhalten, fortsetzen oder Herunterfahren der Anwendungs<br />-Wird zu einem anderen Thread im aktuellem Prozess wechseln.<br />-Wird zu einem anderen Stapelrahmen in aktuellem Thread wechseln.<br />-Flag oder das aktuelle Threadkennzeichnung aufheben<br />: Nur gekennzeichnete Threads anzeigen<br />– Zeigen Sie nur den aktuellen Prozess|  
|**Parallele Stapel** Fenster|-Aufruflisten Sie für mehrere Threads in einem Fenster öffnen.<br />-Active Stapelrahmen für jeden Thread.<br />-Aufrufer und aufgerufenen für jede Methode.|-Herausfiltern Sie bestimmter threads<br />-Wechseln Sie zur Ansicht Parallele Aufgaben<br />-Flag oder das Aufheben der Kennzeichnung eines Threads<br />-Zoom|  
|**Parallele Aufgaben** Fenster|– Anzeigen von Informationen zu <xref:System.Threading.Tasks.Task> Objekte einschließlich des Task-ID, des Aufgabenstatus (geplant, ausgeführt, wartend, blockiert), und welcher Thread die Aufgabe zugewiesen wird.<br />– Der aktuelle Speicherort in der Aufrufliste.<br />-Delegat, die zum Zeitpunkt der Erstellung an die Aufgabe übergeben wurden|-Wechseln Sie zur aktuellen Aufgabe<br />-Flag oder das Aufheben der Kennzeichnung einer Aufgabe<br />-Einfrieren oder Reaktivieren einer Aufgabe|  
|**Parallele Überwachung** Fenster|-Die Spalte zur Kennzeichnung, in der Sie einen Thread markieren können, dem besondere Aufmerksamkeit werden sollen.<br />– Die framespalte, in der ein Pfeil den ausgewählten Frame angibt.<br />-Eine konfigurierbare Spalte, die der Computer, Prozess, Kachel, Aufgabe und Thread anzeigen können.|-Flag oder das Aufheben der Kennzeichnung eines Threads<br />: Nur gekennzeichnete Threads anzeigen<br />-Frames wechseln<br />-Sortieren einer Spalte<br />-Die Gruppe von threads<br />: Threads einfrieren oder reaktivieren<br />-die Daten in das parallele Überwachungsfenster exportieren|  
|**GPU-Threads** Fenster|-Die Spalte zur Kennzeichnung, in der Sie einen Thread markieren können, dem besondere Aufmerksamkeit werden sollen.<br />-Die Spalte mit aktiven Threads, in der ein gelber Pfeil einen aktiven Thread anzeigt. Ein Pfeil gibt den Thread an, in dem die Ausführung durch den Debugger unterbrochen wurde.<br />– Die **Threadanzahl** Spalte, die die Anzahl der Threads an derselben Position anzeigt.<br />– Die **Zeile** Spalte, die die Zeile des Codes angezeigt wird, in dem jede Gruppe von Threads befindet.<br />– Die **Adresse** Spalte, in der die Anweisungsadresse angezeigt wird, in dem jede Gruppe von Threads befindet.<br />– Die **Speicherort** Spalte, die den Speicherort im Code, der die Adresse ist.<br />– Die **Status** Spalte, die anzeigt, ob der Thread aktiv oder blockiert ist.<br />– Die **Kachel** Spalte, in der der kachelindex für die Threads in der Zeile anzeigt.|– Ändern Sie in einem anderen aktiven thread<br />-Zeigt eine bestimmte Kachel und Threads<br />– Anzeigen oder Ausblenden von Spalten<br />: Nach Spalte sortieren<br />-Die Gruppe von threads<br />: Threads einfrieren oder reaktivieren<br />-Flag oder das Aufheben der Kennzeichnung eines Threads<br />: Nur gekennzeichnete Threads anzeigen|  
  
## <a name="see-also"></a>Siehe auch  
 [Fügen an laufende Prozesse an](../debugger/attach-to-running-processes-with-the-visual-studio-debugger.md)   
 [Debuggen von Multithreadanwendungen](../debugger/debug-multithreaded-applications-in-visual-studio.md)   
 [Debuggen von GPU-Code](../debugger/debugging-gpu-code.md)



