---
title: "Festlegen allgemeiner Leistungsoptionen f&#252;r Sitzungen | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.performance.property.general"
ms.assetid: 6b60bd1b-2198-4261-b84e-9b2d8494a992
caps.latest.revision: 10
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 10
---
# Festlegen allgemeiner Leistungsoptionen f&#252;r Sitzungen
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Sie können die Auflistungsmethode und Benennungskonventionen für Profilerstellungsdaten für eine Leistungssitzung der [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]\-Profilerstellungstools auf der Seite **Allgemein** des Eigenschaftendialogfelds für die Leistungssitzung festlegen.  Zum Öffnen dieses Dialogfelds klicken Sie im **Leistungs\-Explorer** mit der rechten Maustaste auf die Leistungssitzung, und klicken Sie dann auf **Eigenschaften**.  
  
 **Voraussetzungen**  
  
-   [!INCLUDE[vsUltLong](../code-quality/includes/vsultlong_md.md)], [!INCLUDE[vsPreLong](../code-quality/includes/vsprelong_md.md)], [!INCLUDE[vsPro](../code-quality/includes/vspro_md.md)]  
  
## Auswählen von Datensammlungsmethoden  
 Die Basisauflistungsmethode kann durch Auswählen einer der Optionen unter **Profilauflistung** festgelegt werden.  Die Optionen sind in der folgenden Tabelle beschrieben:  
  
|||  
|-|-|  
|**Sampling**.  Die Samplingmethode sammelt in regelmäßigen Abständen Profilerstellungsinformationen.  Diese Methode ist nützlich für das Auffinden von Prozessornutzungsproblemen und ist die vorgeschlagene Methode zum Starten der meisten Leistungsuntersuchungen.|-   [Sammeln von Leistungsstatistiken durch Sampling](../profiling/collecting-performance-statistics-by-using-sampling.md)|  
|**Instrumentation**.  Die Instrumentationsmethode springt in eine Kopie eines Modulprofilerstellungscodes, durch den jeder Eintritt, jeder Austritt und jeder Funktionsaufruf der Funktionen in dem Modul während der Profilerstellungsausführung aufgezeichnet wird.  Mithilfe dieser Methode können ausführliche Zeitsteuerungsdaten zu einem Abschnitt des Codes erfasst werden. Zudem werden mit dieser Methode die Auswirkungen von Eingabe\- und Ausgabeoperationen auf die Leistung der Anwendung besser verständlich.|-   [Sammeln ausführlicher Zeitsteuerungsdaten mithilfe der Instrumentation](../profiling/collecting-detailed-timing-data-by-using-instrumentation.md)|  
|**Parallelität**.  Die Parallelitätsmethode erfasst Daten für jedes Ereignis, das die Ausführung des Codes blockiert, z. B., wenn ein Thread darauf wartet, dass der gesperrte Zugriff auf eine Anwendungsressource freigegeben wird.  Diese Methode ist hilfreich für das Analysieren von Multithreadanwendungen.|-   [Sammeln von Parallelitätsdaten zu Threads und Prozessen](../profiling/collecting-thread-and-process-concurrency-data.md)|  
  
 .NET\-Arbeitsspeicherdaten können mit der Sampling\- oder Instrumentationsmethode erfasst werden.  Sie wählen den Typ der Daten unter **.NET\-Arbeitsspeicherprofilerstellung** aus.  
  
|||  
|-|-|  
|**.NET\-Objektzuordnungsinformationen auflisten**.  Standardmäßig enthalten Daten die Anzahl und die Größe von zugeordneten Objekten.  Aktivieren oder deaktivieren Sie dieses Kontrollkästchen, um die .NET\-Arbeitsspeicherdatensammlung zu aktivieren oder zu deaktivieren.<br /><br /> **Lebensdauerinformationen für .NET\-Objekt auflisten**.  Aktivieren Sie dieses Kontrollkästchen, um Daten zu den Garbage Collection\-Generierungen einzuschließen, die verwendet wurden, um die Speicherobjekte freizugeben.|-   [Sammeln von Daten zur .NET\-Speicherbelegung und Lebensdauer](../profiling/collecting-dotnet-memory-allocation-and-lifetime-data.md)|  
  
 Eine Profilerstellungs\-Sitzungsseite wird angezeigt, wenn Sie beginnen, ein Profil für eine Anwendung zu erstellen, bei dem Sie die Profilerstellung anhalten, fortsetzen und beenden können.  
  
 ![Seite einer Profilerstellungssitzung](../profiling/media/prof_profilingsessionpage.png "PROF\_ProfilingSessionPage")  
  
## Festlegen von Optionen für die Profilerstellungs\-Datendatei  
  
|||  
|-|-|  
|**Bericht** Standardmäßig erhält die Profilerstellungs\-Datendatei \(.vsp\) den Namen der profilierten Anwendung, und sie befindet sich im Projektmappen\- oder Projektordner.  Es wird auch eine Datumszeichenfolge an den Namen angefügt, und Datendateien, die andernfalls doppelte Namen hätten, wird eine inkrementierte Zahl hinzugefügt.  Sie können diese Optionen ändern.|-   [Gewusst wie: Dateinamenoptionen für Profilerstellungsdaten](../profiling/how-to-set-performance-data-file-name-options.md)|