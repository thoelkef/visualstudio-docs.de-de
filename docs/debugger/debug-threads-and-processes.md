---
title: "Debuggen von Threads und Prozessen in Visual Studio | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "FSharp"
  - "VB"
  - "CSharp"
  - "C++"
helpviewer_keywords: 
  - "Debuggen [Visual Studio], Threads"
  - "Debuggen von Threads"
  - "Debuggen mehrerer Prozesse"
  - "Prozesse, Debuggen"
  - "Threading [Visual Studio], Debuggen"
ms.assetid: 9f0c8505-b6b2-452b-adfd-076db14d8115
caps.latest.revision: 15
caps.handback.revision: 14
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# Debuggen von Threads und Prozessen in Visual Studio
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

*Threads* und *Prozesse* sind verwandte Konzepte der Informatik.  Beide stellen Folgen von Anweisungen dar, die in einer bestimmten Reihenfolge ausgeführt werden müssen.  Anweisungen von verschiedenen Threads oder Prozessen können aber parallel ausgeführt werden.  
  
 Prozesse werden im Betriebssystem verwaltet und entsprechen dem, was Benutzer als Programme oder Anwendungen sehen.  Ein Thread hingegen wird von einem Prozess verwaltet.  Aus diesem Grund werden Threads gelegentlich als *Lightweightprozesse* bezeichnet.  Jeder Prozess besteht aus einem oder mehreren Threads.  
  
 Die Möglichkeit, mehrere Prozesse auszuführen, versetzt einen Computer in die Lage, mehr als eine Aufgabe gleichzeitig auszuführen.  Das Vorhandensein mehrerer Threads versetzt einen Prozess in die Lage, Arbeiten so aufzuteilen, dass sie parallel ausgeführt werden können.  Auf einem Computer mit Multiprozessoren können Prozesse oder Threads auf verschiedenen Prozessoren ausgeführt werden.  Dies ermöglicht eine echte Parallelverarbeitung.  
  
 Echte Parallelverarbeitung ist nicht immer möglich.  Threads müssen manchmal synchronisiert werden.  Ein Thread muss möglicherweise auf das Ergebnis eines anderen Threads warten, oder ein Thread benötigt exklusiven Zugriff auf eine Ressource, die von einem anderen Thread verwendet wird.  Synchronisierungsprobleme sind eine häufige Ursache von Programmfehlern in Multithreadanwendungen.  Es kann passieren, dass Threads auf eine Ressource warten, die nie verfügbar wird.  Dies führt zu einem Zustand, der *Deadlock* genannt wird.  
  
 Der [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]\-Debugger stellt leistungsstarke und benutzerfreundliche Tools zum Debuggen von Threads und Prozessen bereit.  
  
## Tools zum Debuggen von Threads und Prozessen in Visual Studio  
 Die wichtigsten Tools für die Arbeit mit Prozessen in [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] sind das Dialogfeld **An den Prozess anhängen** sowie das **Prozessfenster** und die Symbolleiste **Debugspeicherort**.  Die wichtigsten Tools für das Debuggen von Threads sind das **Threadfenster**, Threadmarker in Quellcodefenstern sowie die Symbolleiste **Debugspeicherort**.  
  
 Die wichtigsten Tools zum Debuggen von Multithreadanwendungen sind die Fenster **Parallele Stapel**, **Parallele Aufgaben**, **Parallele Überwachung** und **GPU\-Threads**.  
  
 In der folgenden Tabelle sind die verfügbaren Informationen und die an jeder Stelle möglichen Aktionen aufgeführt:  
  
|Benutzeroberfläche|Verfügbare Informationen|Ausführbare Aktionen|  
|------------------------|------------------------------|--------------------------|  
|Dialogfeld **An den Prozess anhängen**|Verfügbare Prozesse, an die angehängt werden kann:<br /><br /> -   Prozessname \(.exe\)<br />-   Prozess\-ID\-Nummer<br />-   Menüleistentitel<br />-   Typ \(Managed v4.0; Managed v2.0, v1.1, v1.0; x86; x64; IA64\)<br />-   Benutzername \(Kontoname\)<br />-   Sitzungsnummer|Auswählen eines Prozesses, an den angehängt werden soll<br /><br /> Auswählen eines Remotecomputers<br /><br /> Ändern des Transporttyps für die Verbindung mit Remotecomputern|  
|**Prozessfenster**|Angehängte Prozesse:<br /><br /> -   Prozessname<br />-   Prozess\-ID\-Nummer<br />-   Pfad zur EXE\-Datei des Prozesses<br />-   Menüleistentitel<br />-   Zustand \(Unterbrechen,  Aktiv\)<br />-   Debuggen \(Systemeigen, Verwaltet usw.\)<br />-   Transporttyp \(standardmäßig, systemeigen ohne Authentifizierung\)<br />-   Transportqualifizierer \(Remotecomputer\)|Tools:<br /><br /> -   Anfügen<br />-   Trennen<br />-   Beenden<br /><br /> Kontextmenü:<br /><br /> -   Anfügen<br />-   Trennen<br />-   Nach Beenden des Debuggens trennen<br />-   Beenden|  
|**Threadfenster**|Threads in aktuellem Prozess:<br /><br /> -   Thread\-ID<br />-   Verwaltete ID<br />-   Kategorie \(Hauptthread, Benutzeroberflächenthread, Remoteprozeduraufruf\-Handler oder Arbeitsthread\)<br />-   Thread Name<br />-   Ort, an dem der Thread erstellt wird<br />-   Priorität<br />-   Affinitätsmaske<br />-   Angehaltene Anzahl<br />-   Prozessname<br />-   Kennzeichenindikator<br />-   Angehaltener Indikator|Tools:<br /><br /> -   Suche<br />-   Aufrufliste suchen<br />-   Nur eigenen Code kennzeichnen<br />-   Benutzerdefinierte Modulauswahl kennzeichnen<br />-   Gruppieren nach<br />-   Columns<br />-   Aufruflisten erweitern\/reduzieren<br />-   Gruppen erweitern\/reduzieren<br />-   Threads sperren\/entsperren<br /><br /> Kontextmenü:<br /><br /> -   Threads in Quelle anzeigen<br />-   Zu Thread wechseln<br />-   Ausgeführten Thread sperren<br />-   Gesperrten Thread entsperren<br />-   Thread zur weiteren Überprüfung kennzeichnen<br />-   Kennzeichnung eines Threads aufheben<br />-   Thread umbenennen<br />-   Threads anzeigen und ausblenden<br /><br /> Sonstige Aktionen:<br /><br /> -   Aufrufliste für einen Thread in einem DataTip anzeigen|  
|Quellcodefenster|Threadindikatoren im linken Bundsteg geben einzelne oder mehrere Threads an \(standardmäßig deaktiviert, die Aktivierung erfolgt über das Kontextmenü im Fenster **Threads**\)|Kontextmenü:<br /><br /> -   Zu Thread wechseln<br />-   Thread zur weiteren Überprüfung kennzeichnen<br />-   Kennzeichnung eines Threads aufheben|  
|Symbolleiste **Debugspeicherort**|-   Aktueller Prozess<br />-   Miniaturansicht der Anwendung anzeigen<br />-   Anwendung anhalten<br />-   Anwendung fortsetzen<br />-   Anwendung anhalten und herunterfahren<br />-   Aktueller Thread<br />-   Aktuellen Status des Thread\-Flags umkehren<br />-   Nur gekennzeichnete Threads anzeigen<br />-   Nur aktuellen Prozess anzeigen<br />-   Aktueller Stapelrahmen|-   Zu einem anderen Prozess wechseln<br />-   Anwendung anhalten, fortsetzen oder herunterfahren<br />-   Zu einem anderen Thread im aktuellem Prozess wechseln<br />-   Zu einem anderen Stapelrahmen in aktuellem Thread wechseln<br />-   Kennzeichnen bzw. Aufheben der Kennzeichnung von aktuellen Threads<br />-   Nur gekennzeichnete Threads anzeigen<br />-   Nur den aktuellen Prozess anzeigen|  
|Fenster **Parallele Stapel**|-   Aufruflisten für mehrere Threads in einem Fenster.<br />-   Aktiver Stapelrahmen für jeden Thread.<br />-   Aufrufer und Aufgerufene für die einzelnen Methoden.|-   Herausfiltern bestimmter Threads<br />-   Wechseln zur Ansicht Parallele Aufgaben<br />-   Kennzeichnen bzw. Aufheben der Kennzeichnung eines Threads<br />-   Zoom|  
|Fenster **Parallele Aufgaben**|-   Anzeigen von Informationen zu <xref:System.Threading.Tasks.Task>\-Objekten, einschließlich der Aufgaben\-ID, des Aufgabenstatus \(geplant, ausgeführt, wartend, blockiert\) und der der Aufgabe zugewiesenen Threads.<br />-   Aktuelle Position in der Aufrufliste.<br />-   Zur Erstellungszeit an die Aufgabe übergebener Delegat|-   Wechseln zur aktuellen Aufgabe<br />-   Kennzeichnen oder Aufheben der Kennzeichnung einer Aufgabe<br />-   Einfrieren oder Reaktivieren einer Aufgabe|  
|Fenster **Parallele Überwachung**|-   Die Kennzeichenspalte, in der Sie einen Thread markieren können, der besondere Aufmerksamkeit erhalten soll.<br />-   Die Framespalte, in der ein Pfeil den ausgewählten Frame angibt.<br />-   Eine konfigurierbare Spalte, in der der Computer, der Prozess, die Kachel, die Aufgabe und der Thread angezeigt werden können.|-   Kennzeichnen bzw. Aufheben der Kennzeichnung eines Threads<br />-   Nur gekennzeichnete Threads anzeigen<br />-   Frames wechseln<br />-   Spalte sortieren<br />-   Threads gruppieren<br />-   Threads einfrieren oder reaktivieren<br />-   Daten in das parallele Überwachungsfenster exportieren|  
|Fenster **GPU\-Threads**|-   Die Kennzeichenspalte, in der Sie einen Thread markieren können, der besondere Aufmerksamkeit erhalten soll.<br />-   Die Spalte mit aktiven Threads, in der ein gelber Pfeil einen aktiven Thread anzeigt.  Ein Pfeil gibt den Thread an, in dem die Ausführung durch den Debugger unterbrochen wurde.<br />-   Die Spalte **Threadanzahl**, in der die Anzahl von Threads an derselben Position angezeigt wird.<br />-   Die Spalte **Zeile**, in der die Codezeile angezeigt wird, in der sich die jeweilige Threadgruppe befindet.<br />-   Die Spalte **Adresse**, in der die Anweisungsadresse angezeigt wird, in der sich die jeweilige Threadgruppe befindet.<br />-   Die Spalte **Speicherort**, in der der Ort im Code die Adresse angegeben ist.<br />-   Die Spalte **Status**, in der angegeben ist, ob der Thread aktiv oder blockiert ist.<br />-   Die Spalte **Kachel**, in der der Kachelindex für die Threads in der Zeile angezeigt wird.|-   Zu einem anderen aktiven Thread wechseln<br />-   Bestimmte Kachel und bestimmten Thread anzeigen<br />-   Spalte ein\- oder ausblenden<br />-   Nach Spalte sortieren<br />-   Threads gruppieren<br />-   Threads einfrieren oder reaktivieren<br />-   Kennzeichnen bzw. Aufheben der Kennzeichnung eines Threads<br />-   Nur gekennzeichnete Threads anzeigen|  
  
## Siehe auch  
 [Anhängen an laufende Prozesse](../debugger/attach-to-running-processes-with-the-visual-studio-debugger.md)   
 [Debuggen von Multithreadanwendungen](../debugger/debug-multithreaded-applications-in-visual-studio.md)   
 [Debuggen von GPU\-Code](../debugger/debugging-gpu-code.md)