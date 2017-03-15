---
title: "&#220;bersicht &#252;ber die Berichte der Profilerstellungstools | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Profilerstellungstools, Informationen über Leistungsberichte"
  - "Leistung, Berichte"
  - "Leistungsberichte, Informationen über Leistungsberichte"
ms.assetid: 7324c24c-fd09-479b-b2ad-e0c3b613e040
caps.latest.revision: 45
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 45
---
# &#220;bersicht &#252;ber die Berichte der Profilerstellungstools
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Sie können die Profilerstellungsdaten einer Leistungssitzung im Fenster **Leistungsbericht** der Visual Studio Team System\-Entwicklungs\-Editions\-integrierten Entwicklungsumgebung \(IDE\) anzeigen.  Die Profilerstellungsdaten werden in .vsp\- und .vsps\-Dateien gespeichert.  In den Berichtsansichtsfenstern können Sie Anwendungsleistungsprobleme einsehen und analysieren.  
  
> [!CAUTION]
>  Eine Profilerstellungsdatendatei enthält vertrauliche Informationen wie Computername, Betriebssystemversion, Dateipfade, Informationen zum Arbeitsspeicher und andere Informationen zur Computerinstallation.  Ihnen allein sollte daher die Kontrolle über die Verteilung der Daten, sei es im systemeigenen VSP\-Format oder als exportierte CSV\- oder XML\-Datei, obliegen.  
>   
>  Beim Erfassen von Informationen zur Ereignisablaufverfolgung im Rahmen der Leistungssitzung werden möglicherweise weitere Informationen im Ereignisablaufverfolgungsprotokoll \(ETL\-Datei\) angezeigt.  Zu diesen Informationen gehören der Domänen\- und der Benutzername, d. h., die Kontrolle über die Verteilung der Protokolldatei sollte allein Ihnen obliegen.  
  
## Fenster Leistungsbericht  
 Das Fenster Leistungsbericht ist ein Toolfenster, mit dem Leistungsdaten angezeigt, verwaltet und gefiltert werden können. Darüber hinaus enthält das Fenster ein anpassbares Abfragesteuerelement.  
  
 Über die Hauptsymbolleiste des Fensters Leistungsbericht können Sie auf die einzelnen Ansichten zugreifen.  Klicken Sie auf den Pfeil neben der Liste **Aktuelle Ansicht**, um die einzelnen verfügbaren Ansichten anzuzeigen und auszuwählen.  
  
 Das Fenster Leistungsbericht verfügt über die folgenden Datenansichten:  
  
### Zusammenfassungsansicht  
 Standardmäßig werden Profilerstellungsdaten in der Zusammenfassungsansicht angezeigt.  Diese Ansicht dient als Ausgangspunkt bei der Überprüfung auf Leistungsprobleme.  Von den einzelnen Zeilen in der Zusammenfassungsansicht können Sie zu detaillierteren Ansichten wechseln, indem Sie mit der rechten Maustaste auf den Funktions\- oder Modulnamen klicken.  Weitere Informationen finden Sie unter [Zusammenfassungsansicht](../profiling/summary-view.md).  
  
### Aufrufer\-\/Aufgerufener\-Ansicht  
 Die Aufrufer\-\/Aufgerufener\-Ansicht zeigt eine Aufrufstruktur für eine einzelne Funktion an.  Die Ansicht ist in drei Bereiche unterteilt:  
  
-   Die Zielfunktion wird in der Mitte der Ansicht angezeigt.  
  
-   Die Funktionen, die die Funktion aufgerufen haben \(Aufrufer\), werden oberhalb der Zielfunktion angezeigt.  
  
-   Die Funktionen, die von der Zielfunktion aufgerufen werden \(Aufgerufene\), werden unter dem Ziel angezeigt.  
  
 Sie können eine andere Funktion auswählen, indem Sie in der Liste der Aufrufer oder Aufgerufenen auf eine beliebige Funktion doppelklicken.  Weitere Informationen finden Sie unter [Aufrufer\-\/Aufgerufener\-Ansicht](../profiling/caller-callee-view.md).  
  
### Aufrufstrukturansicht  
 Die Aufrufstrukturansicht zeigt die Funktionsausführungspfade an, die in der profilierten Anwendung durchlaufen wurden.  Der Stamm der Struktur ist der Einstiegspunkt in die Anwendung oder Komponente.  Jeder Funktionsknoten führt alle Funktionen, die er aufgerufen hat, sowie Leistungsdaten über diese Funktionsaufrufe auf.  
  
 Die Aufrufstrukturansicht kann erweitert werden und den Ausführungspfad einer Funktion markieren, die die meiste Zeit in Anspruch genommen hat oder für die am häufigsten ein Sampling ausgeführt wurde.  Um den aktivsten Pfad anzuzeigen, klicken Sie mit der rechten Maustaste auf die Funktion, und klicken Sie dann auf **Langsamsten Pfad erweitern**.  Weitere Informationen finden Sie unter [Aufrufstrukturansicht](../profiling/call-tree-view.md).  
  
### Prozessansicht  
 Die Prozessansicht zeigt Leistungsdaten für jeden profilierten Prozess und Thread an.  Weitere Informationen finden Sie unter [Prozessansicht](../profiling/process-view.md).  
  
### Modulansicht  
 In der Modulansicht werden die Module im Projekt aufgelistet und Profilerstellungsdaten für jedes Modul aufgeführt.  Erweitern oder reduzieren Sie den Modulnamen, um die Funktionsprofilerstellungsdaten anzuzeigen.  Wenn die Daten mit der Samplingmethode erfasst wurden, sind darüber hinaus Profilerstellungsdaten zur Quellcodezeile und zum Anweisungszeiger verfügbar.  Weitere Informationen finden Sie unter [Modulansicht](../profiling/modules-view.md).  
  
### Funktionsansicht  
 In der Funktionsansicht werden die während der Profilerstellung aufgerufenen Funktionen aufgeführt.  Weitere Informationen finden Sie unter [Funktionsansicht](../profiling/functions-view.md).  
  
### Zeilenansicht  
 Mit der Zeilenansicht können Sie die Quellcodezeilen anzeigen, die während der Sampling\-Profilerstellung ausgeführt wurden.  Weitere Informationen finden Sie unter [Zeilenansicht](../profiling/lines-view.md).  
  
### IP\-Ansicht  
 Die IP\-Ansicht \(Instruction Pointer \- Anweisungszeiger\) ermöglicht es Ihnen, bestimmte Anweisungen anzuzeigen, die während der Sampling\-Profilerstellung ausgeführt werden.  Weitere Informationen finden Sie unter [Anweisungszeigeransicht](../profiling/instruction-pointers-ips-view.md).  
  
### Zuordnungsansicht  
 Die Zuordnungsansicht ist verfügbar, wenn im Dialogfeld **Leistungssitzung** auf der Seite **Allgemein** die Option **.NET\-Objektzuordnungsinformationen auflisten** aktiviert wurde.  Siehe [Übersicht über Leistungssitzungen](../profiling/performance-session-overview.md).  Die Zuordnungsansicht führt die .NET\-Objekte auf, die von der Anwendung oder der Komponente zugeordnet wurden.  Wenn eine Objektzeile erweitert wird, wird eine Aufrufstruktur angezeigt.  Die Aufrufstruktur zeigt die Ausführungspfade an, die zur Erstellung des Objekts geführt haben.  Informationen werden auch zur Anzahl der inklusiven und exklusiven Zuordnungen für jede Funktion in der Aufrufstruktur angezeigt.  Die Zuordnungsansicht kann erweitert werden und den Ausführungspfad einer Funktion markieren, die die höchste Anzahl an Objekten zugeordnet hat.  Um den aktivsten Pfad anzuzeigen, klicken Sie mit der rechten Maustaste auf die Funktion, und klicken Sie dann auf **Langsamsten Pfad erweitern**.  Weitere Informationen finden Sie unter [Sammeln von Daten zur .NET\-Speicherbelegung und Lebensdauer](../profiling/collecting-dotnet-memory-allocation-and-lifetime-data.md) und [Zuordnungsansicht](../profiling/dotnet-memory-allocations-view.md).  
  
### Objektlebensdaueransicht  
 Die Objektlebensdaueransicht ist verfügbar, wenn im Eigenschaftendialogfeld **Leistungssitzung** auf der Seite **Allgemein** die Optionen **.NET\-Objektzuordnungsinformationen auflisten** und **Lebensdauerinformationen für .NET\-Objekt auflisten** aktiviert wurden.  
  
 In der Objektlebensdaueransicht werden die Gesamtzahl der Instanzen der einzelnen Typen und die Anzahl der Objekte angezeigt, die in jeder Garbage Collection\-Generation erfasst wurden.  Weitere Informationen finden Sie unter [Objektlebensdaueransicht](../profiling/object-lifetime-view.md).  
  
## Anpassbares Filtersteuerelement  
 Das anpassbare Filtersteuerelement verfügt über die folgenden Optionen:  
  
-   **Filter importieren**: Ruft eine zuvor gespeicherte benutzerdefinierte Abfrage ab.  
  
-   **Filter exportieren**: Speichert die benutzerdefinierte Abfrage an dem angegebenen Speicherort.  
  
-   **Abfrage ausführen**: Führt die Abfrage wie im benutzerdefinierten Abfragesteuerelement angezeigt aus.  
  
-   **Abfrage beenden**: Beendet die Ausführung einer laufenden Abfrage.  Diese Schaltfläche ist nicht verfügbar, wenn keine Abfrage ausgeführt wird.  
  
-   **Abfrage anzeigen**: Blendet das benutzerdefinierte Abfragesteuerelement ein\/aus.  
  
-   **Analysierte Daten speichern**: Speichert den Bericht zusammen mit der aktuellen Analyse als VSPS\-Datei.  
  
-   **Exportieren**: Speichert den aktuellen Bericht mit Optionen zum Speichern der verschiedenen Ansichten in einer Datei im CVS\- oder XML\-Format.  
  
## Siehe auch  
 [Analysieren der durch Profilerstellungstools erstellten Daten](../profiling/analyzing-performance-tools-data.md)   
 [Berichtsansichten für Profilerstellungstools](../profiling/performance-report-views.md)