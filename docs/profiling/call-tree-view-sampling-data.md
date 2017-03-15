---
title: "Aufrufstrukturansicht - Profiler-Samplingdaten | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Sampling-Profilerstellungsmethode, Aufrufstrukturansicht"
  - "Aufrufstrukturansicht"
ms.assetid: 5c4e8ec3-d0d3-485a-93bd-9060df4eb739
caps.latest.revision: 16
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 16
---
# Aufrufstrukturansicht - Profiler-Samplingdaten
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Die Aufrufstrukturansicht zeigt die Funktionsausführungspfade an, die in der profilierten Anwendung durchlaufen wurden.  
  
> [!NOTE]
>  Verbesserte Sicherheitsfeatures in Windows 8 und Windows Server 2012 erforderten tiefgreifende Änderungen bei der Datenerfassung des Visual Studio\-Profilers auf diesen Plattformen.  Außerdem benötigen Windows Store\-Apps neue Erfassungsmethoden.  Siehe [Profilerstellung für Windows 8\- und Windows Server 2012\-Anwendungen](../profiling/performance-tools-on-windows-8-and-windows-server-2012-applications.md).  
  
 Der Stamm der Struktur ist der Einstiegspunkt in die Anwendung oder Komponente.  Jeder Funktionsknoten führt alle Funktionen, die er aufgerufen hat, sowie Leistungsdaten über diese Funktionsaufrufe auf.  
  
 Die Werte in der Aufrufstrukturansicht beziehen sich auf die Funktionsinstanzen, die von der übergeordneten Funktion in der Aufrufstruktur aufgerufen wurden.  Prozentwerte werden berechnet, indem der Funktionsinstanzwert mit der Gesamtzahl der Samplings in der Profilerstellung verglichen wird.  
  
## Hervorheben des langsamsten Ausführungspfads  
 Die Ansicht der Aufrufstruktur kann erweitert werden und den Ausführungspfad des Prozesses oder der Funktion hervorheben, für die die meisten Samplings durchgeführt wurden.  Um den aktivsten Pfad anzuzeigen, klicken Sie mit der rechten Maustaste auf den den Prozess oder die Funktion, und klicken Sie dann auf **Langsamsten Pfad erweitern**.  
  
## Festlegen des Stammknotens der Aufrufstruktur  
 Jeder Prozess in der Profilerstellungsausführung wird als Stammknoten angezeigt.  Sie können den Startknoten der Aufrufstrukturansicht festlegen, indem Sie mit der rechten Maustaste auf den Knoten klicken, der als Startknoten festgelegt werden soll, und dann **Stamm festlegen** auswählen.  
  
 Durch Festlegen des Stammknotens verhindern Sie, dass alle anderen Einträge außer der Teilstruktur des ausgewählten Knotens in der Ansicht angezeigt werden.  Um den Stammknoten auf den ursprünglichen Knoten zurückzusetzen, klicken Sie mit der rechten Maustaste auf das Fenster der Aufrufstrukturansicht und dann auf **Stamm zurücksetzen**.  
  
|Spalte|**Beschreibung**|  
|------------|----------------------|  
|**Prozess\-ID**|Die Prozess\-ID \(PID\) der Profilerstellung.|  
|**Prozessname**|Der Prozessname.|  
|**Modulname**|Der Name des Moduls, das die Funktion enthält.|  
|**Modulpfad**|Der Pfad des Moduls, das die Funktion enthält.|  
|**Quelldatei**|Die Quelldatei, die die Definition der Funktion enthält.|  
|**Function Name**|Der vollqualifizierte Name der Funktion.|  
|**Funktionszeilennummer**|Die Zeilennummer des Anfangs dieser Funktion in der Quelldatei.|  
|**Function Address**|Die Adresse der Funktion.|  
|**Ebene**|Die Tiefe der Funktion in der Aufrufstruktur.  Nur in [VSPerfReport](../profiling/vsperfreport.md)\-Befehlszeilenberichten.|  
|**Exclusive Samples**|Die Anzahl der gesammelten Samplings in dieser Funktion bei einem Aufruf durch die übergeordnete Funktion in der Aufrufstruktur.  Diese Zahl umfasst nicht die Samplings, die in den von der Funktion aufgerufenen Funktionen gesammelt wurden.|  
|**Exklusive Samplings in %**|Der Prozentsatz aller Samplings während der Profilerstellung, die auf exklusive Samplings dieser Funktion entfallen, wenn diese von der übergeordneten Funktion in der Aufrufstruktur aufgerufen wurde.|  
|**Inclusive Samples**|Die Anzahl der gesammelten Samplings in dieser Funktion bei einem Aufruf durch die übergeordnete Funktion in der Aufrufstruktur.  Diese Zahl umfasst auch Samplings, die in von der Funktion aufgerufenen Funktionen gesammelt wurden.|  
|**Inklusive Samplings in %**|Der Prozentsatz aller Samplings während der Profilerstellung, die auf inklusive Samplings dieser Funktion entfallen, wenn diese von der übergeordneten Funktion in der Aufrufstruktur aufgerufen wurde.|  
  
## Siehe auch  
 [Gewusst wie: Anpassen von Spalten in Berichtsansichten](../profiling/how-to-customize-report-view-columns.md)   
 [Call Tree View \- Profiler Sampling Data](../profiling/call-tree-view-sampling-data.md)   
 [Aufrufstrukturansicht \- Sampling](../profiling/call-tree-view-dotnet-memory-sampling-data.md)   
 [Aufrufstrukturansicht \- Instrumentation](../profiling/call-tree-view-dotnet-memory-instrumentation-data.md)   
 [Aufrufstrukturansicht](../profiling/call-tree-view-instrumentation-data.md)