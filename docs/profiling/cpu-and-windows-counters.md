---
title: "CPU- und Windows-Indikatoren in den Profilerstellungstools | Microsoft Docs"
ms.custom: ""
ms.date: "12/16/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.performance.property.counters"
helpviewer_keywords: 
  - "Windows-Indikatoren in Profilerstellungstools"
  - "CPU-Indikatoren in Profilerstellungstools"
ms.assetid: d2c45c6a-f975-45ab-b8a5-4768ddd518fb
caps.latest.revision: 28
caps.handback.revision: 26
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# CPU- und Windows-Indikatoren in den Profilerstellungstools
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Mit dem [!INCLUDE[vs_dev11_long](../data-tools/includes/vs_dev11_long_md.md)]\-Profiler können Sie vom Betriebssystem \(Windows\-Indikatoren\) und von der Prozessoreinheit \(CPU\-Indikatoren\) generierte Leistungsdaten sammeln.  
  
 **Voraussetzungen**  
  
-   [!INCLUDE[vsUltLong](../code-quality/includes/vsultlong_md.md)], [!INCLUDE[vsPreLong](../code-quality/includes/vsprelong_md.md)], [!INCLUDE[vsPro](../code-quality/includes/vspro_md.md)]  
  
> [!NOTE]
>  Verbesserte Sicherheitsfeatures in Windows 8 und Windows Server 2012 erforderten tiefgreifende Änderungen bei der Datenerfassung des Visual Studio\-Profilers auf diesen Plattformen.  Außerdem benötigen Windows Store\-Apps neue Erfassungsmethoden.  Siehe [Profilerstellung für Windows 8\- und Windows Server 2012\-Anwendungen](../profiling/performance-tools-on-windows-8-and-windows-server-2012-applications.md).  
  
## Windows\-Indikatoren  
 Windows\-Indikatoren sind Teil der Windows\-Diagnoseinfrastruktur, die Informationen über die Leistung des Betriebssystems oder einer Anwendung, eines Diensts oder eines Treibers bereitstellt.  Windows\-Indikatoren hängen von der Konfiguration des aktuellen Computers ab und sind auf anderen Computern unter Umständen nicht verfügbar.  Windows\-Leistungsindikatoren werden in Profilerstellungs\-Datendateien als Profilerstellungsmarkierungen gesammelt, mit denen dann wiederum Ansichten und Berichte gefiltert werden können.  
  
## CPU\-Indikatoren  
 CPU\-Indikatoren sind ein Feature der Computer\-CPU und speichern die Anzahl hardware\-bezogener Ereignisse.  Wenn Sie CPU\-Indikatordaten mit der instrumentierten Profilerstellungsmethode sammeln, werden die Daten an die Daten für Funktionen und Module angefügt.  Sie können mehrere CPU\-Indikatoren mit der Instrumentationsmethode sammeln.  Wenn Sie die Samplingmethode verwenden, wählen Sie einen Indikator aus, der als zu überprüfendes Ereignis verwendet werden soll.  
  
 Leistungsindikatoren sind CPU\-spezifisch.  Unterschiedliche CPU\-Modelle und \-Versionen können deutlich abweichende Konfigurationseinstellungen für denselben Leistungsindikator aufweisen.  Portable [!INCLUDE[vs_dev11_long](../data-tools/includes/vs_dev11_long_md.md)]\-Profiler\-Ereignisse koppeln einige der gängigen Leistungsindikatoren von bestimmten Prozessoren ab und ermöglichen es Ihnen, allgemeine Leistungsereignisse zu erfassen oder ein Sampling für diese auszuführen.  
  
 Wenn Sie bei Verwendung des Profilers ein bestimmtes Ereignis berücksichtigen möchten, z. B. erfolglose E2\-Cachezugriffe, können Sie eine Leistungssitzung für den Absender des Ereignisses erstellen.  Dieser Vorgang kann für jede CPU mit einem E2\-Cache ausgeführt werden.  Die Leistungssitzung kann ohne weitere Änderung zwischen Plattformen verschoben werden.  
  
 Der Visual Studio\-Profiler weiterhin, um bestimmte Ereignisse für eine spezifische Plattform zu unterstützen.  Beispielsweise kann ein Entwickler auf einer Pentium 4\-Plattform die Ereignisse erfassen, die spezifisch für die NetBurst\-Architektur sind.  Dieses Ereignis ist zwar nicht portabel, steht dem Entwickler aber für eine bestimmte Leistungssitzung auf einer spezifischen Plattform weiterhin zur Verfügung.  
  
## Portable Ereignisse und Plattformereignisse  
 Bei portablen Ereignissen handelt es sich um eine Gruppe von CPU\-Indikatoren, die nicht spezifisch für einen bestimmten Prozessor sind.  Alle anderen CPU\-Indikatoren werden als Plattformereignisse bezeichnet, die auf verschiedenen Plattformen unterstützt werden oder nicht.  
  
 Beschreibungen sowohl für portable Ereignisse als auch für Plattformereignisse sind in XML\-Dateien enthalten, in denen auch spezifische Werte in Bezug auf die Indikatoren angegeben sind.  Da die Daten für Intel\- und AMD\-CPUs beispielsweise unterschiedlich sind, werden mehrere Dateien für die verschiedenen CPUs bereitgestellt.  Der [!INCLUDE[vs_orcas_long](../debugger/includes/vs_orcas_long_md.md)] Profiler nutzt diese Informationen, um dem Benutzer für Leistungsmessungen die geeigneten Indikatoren – sowohl portable Indikatoren als auch Plattformindikatoren – zur Verfügung zu stellen.  
  
### Portable Ereignisse  
 Portable Ereignisse enthalten die folgenden Ereignisse:  
  
 **Allgemeine Ereignisse**  
  
|Ereignisname|Ereignisbeschreibung|  
|------------------|--------------------------|  
|Instructions Retired|Gibt die Anzahl der Anweisungen an, die bis zum Abschluss des Ereignisses ausgeführt wurden.|  
|Non Halted Cycles|Gibt nur diejenigen Zyklen an, in denen der Prozessor nicht angehalten wird, z. B. weil auf E\/A gewartet wird.|  
  
 **Front\-End\-Ereignisse**  
  
|Ereignisname|Ereignisbeschreibung|  
|------------------|--------------------------|  
|ITLB Misses|Gibt die Anzahl der ITLB\-Suchen \(Instruction Translation Look\-aside Buffer\) an, die zu einem Fehler führten.|  
  
 **Verzweigungsereignisse**  
  
|Ereignisname|Ereignisbeschreibung|  
|------------------|--------------------------|  
|Branches Retired|Gibt die Anzahl der Verzweigungsanweisungen an, die bis zum Abschluss des Ereignisses ausgeführt wurden.|  
|Mis\-predicted Branches|Gibt falsch vorhergesagte Verzweigungen an, zu denen es kommt, weil der Prozessor einen falschen Pfad vorhergesagt hat.  Falsch vorhergesagte Verzweigungen führen zu Leistungseinbußen, weil der Prozessor alle bereits ausgeführten Arbeiten verwerfen und mit einem korrekten Pfad erneut starten muss.|  
  
 **Speicherereignisse:**  
  
|Ereignisname|Ereignisbeschreibung|  
|------------------|--------------------------|  
|L2 Cache Read Misses|Gibt die Anzahl der Lesefehler im Cache der 2. Ebene an.|  
|L2 Cache Read References|Gibt die Anzahl der Leseverweise im Cache der 2. Ebene an.  Dies schließt Ladefehler sowie RFO\-Fehler und \-Treffer \(Read For Ownership\) ein.|  
  
## Anzeigen verfügbarer Indikatoren  
 Sie können die verfügbaren CPU\-Indikatoren in der Visual Studio IDE in einem Eingabeaufforderungsfenster aufführen.  
  
### Visual Studio\-Benutzeroberfläche  
 Um die verfügbaren Indikatoren auf einem Computer in der Visual Studio IDE aufzuführen, muss eine Profiler\-Leistungssitzung die, im Leistungs\-Explorer geöffnet ist.  
  
##### So zeigen Sie eine Liste einer Liste aller CPU\-Indikatoren an, die auf der aktuellen Plattform unterstützt werden  
  
1.  Klicken Sie im Leistungs\-Explorer mit der rechten Maustaste auf die Leistungssitzung, und klicken Sie dann auf **Eigenschaften**.  
  
2.  Führen Sie eine der folgenden Aktionen aus:  
  
    -   Klicken Sie auf **Sampling**. Wählen Sie dann aus der Ereignisliste **Beispiel** die Option **Leistungsindikator** aus.  Die CPU\-Indikatoren werden unter **Verfügbare Leistungsindikatoren** aufgeführt.  
  
         **Hinweis** Klicken Sie auf **Abbrechen**, um zur vorherigen Samplingkonfiguration zurückzukehren.  
  
     \- oder \-  
  
    -   Wählen Sie **CPU\-Indikatoren** und dann **CPU\-Indikatoren auflisten** aus.  Die CPU\-Indikatoren werden unter **Verfügbare Indikatoren** aufgeführt.  
  
         **Hinweis** Klicken Sie auf **Abbrechen**, um zur vorherigen Indikatorauflistungskonfiguration zurückzukehren.  
  
##### So zeigen Sie eine Liste aller Windows\-Indikatoren an, die auf der aktuellen Plattform unterstützt werden  
  
1.  Klicken Sie im Leistungs\-Explorer mit der rechten Maustaste auf die Leistungssitzung, und klicken Sie dann auf **Eigenschaften**.  
  
2.  Klicken Sie auf **Windows\-Indikatoren**.  
  
3.  Wählen Sie **Windows\-Indikatoren auflisten** aus.  
  
4.  Wählen Sie in der Liste **Indikatorenkategorie** eine Indikatorgruppe aus.  Der Windows\-Leistungsindikator für die Gruppe wird im Listenfeld angezeigt.  
  
     **Hinweis:** Klicken Sie auf **Abbrechen**, um zur vorherigen Indikatorauflistungskonfiguration zurückzukehren.  
  
### Befehlszeile  
 Mit dem Befehlszeilentool [VSPerfCmd](../profiling/vsperfcmd.md) können Sie die auf einem Computer verfügbaren CPU\-Indikatoren in der Befehlszeile aufführen.  
  
##### So führen Sie die CPU\-Indikatoren auf, die auf der aktuellen Plattform unterstützt werden  
  
1.  Öffnen Sie ein Eingabeaufforderungsfenster.  
  
2.  Typ  
  
     **\<Visual Studio Performance Tools Directory\>\\VSPerfCmd \/querycounters**  
  
     Dabei ist **\<Visual Studio Performance Tools Directory\>**  der Pfad zum Verzeichnis Performance Tools der Visual Studio\-Installation. Dieser lautet normalerweise  
  
     C:\\Programme\\Microsoft Visual Studio 10.0\\Team Tools\\Performance Tools  
  
## Siehe auch  
 [Übersichten](../profiling/overviews-performance-tools.md)   
 [Gewusst wie: Auswählen von Samplingereignissen](../profiling/how-to-choose-sampling-events.md)   
 [Gewusst wie: Sammeln von CPU\-Indikatordaten](../profiling/how-to-collect-cpu-counter-data.md)   
 [Gewusst wie: Sammeln von Windows\-Indikatordaten](../profiling/how-to-collect-windows-counter-data.md)