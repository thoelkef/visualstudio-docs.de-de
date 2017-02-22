---
title: "Aufrufer-/Aufgerufener-Ansicht – Profiler-Samplingdaten | Microsoft Docs"
ms.custom: ""
ms.date: "12/02/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Sampling-Profilerstellungsmethode, Aufrufer-/Aufgerufener-Ansicht"
  - "Aufrufer-/Aufgerufener-Ansicht"
ms.assetid: 28e85ed5-1512-4b59-bb84-138a2abca7dd
caps.latest.revision: 14
caps.handback.revision: 14
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# Aufrufer-/Aufgerufener-Ansicht – Profiler-Samplingdaten
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

In der Aufrufer\-\/Aufgerufener\-Ansicht werden Profilerstellungsinformationen für eine ausgewählte Funktion und die übergeordneten und untergeordneten Funktionen angezeigt.  Die Aufrufer\-\/Aufgerufener\-Ansicht enthält drei Raster.  
  
 **Aktuelle Funktion** wird im mittleren Raster angezeigt und zeigt Profilerstellungsinformationen für die ausgewählte Funktion an.  Die Werte umfassen alle Samplingaufrufe der Funktion.  
  
 **Funktionen, die die aktuelle Funktion aufgerufen haben** wird im obersten Raster angezeigt und zeigt die einzelnen Beiträge der \(übergeordneten\) Aufruferfunktion zu den Werten der ausgewählten \(aktuellen\) Funktion an.  
  
 **Funktionen, die von der aktuellen Funktion aufgerufen wurden** wird im untersten Raster angezeigt und zeigt Profilerstellungsinformationen für die aufgerufenen \(untergeordneten\) Funktionen der ausgewählten Funktion an, wenn die untergeordnete Funktion von der aktuellen Funktion aufgerufen wurde.  
  
> [!NOTE]
>  Verbesserte Sicherheitsfeatures in Windows 8 und Windows Server 2012 erforderten tiefgreifende Änderungen bei der Datenerfassung des Visual Studio\-Profilers auf diesen Plattformen.  Außerdem benötigen Windows Store\-Apps neue Erfassungsmethoden.  Siehe [Profilerstellung für Windows 8\- und Windows Server 2012\-Anwendungen](../profiling/performance-tools-on-windows-8-and-windows-server-2012-applications.md).  
  
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
|**Typ**|Der Kontext der Funktion:<br /><br /> -   **0** – die aktuelle Funktion<br />-   **1** – eine Funktion, die die aktuelle Funktion aufruft<br />-   **2** – eine Funktion, die von der aktuellen Funktion aufgerufen wird|  
|**Name der Stammfunktion**|Der Name der aktuellen Funktion.|  
|**Inclusive Samples**|-   Bei er aktuellen Funktion die Anzahl von Beispielen, die gesammelt wurden, obwohl diese Funktion oder eine ihrer untergeordneten Funktionen ausgeführt wurde.<br />-   Bei einer Aufruferfunktion die Anzahl von inklusiven Samplings der aktuellen Funktion, die gesammelt wurden, als diese Funktion die aktuelle Funktion aufgerufen hat.<br />-   Bei einer aufgerufenen Funktion die Anzahl von inklusiven Samplings dieser Funktion, die gesammelt wurden, als die aktuelle Funktion diese Funktion aufgerufen hat.|  
|**Inklusive Samplings in %**|Der Prozentsatz aller Samplings während der Profilerstellung, die inklusive Samplings dieser Funktion waren.|  
|**Exclusive Samples**|-   Bei der aktuellen Funktion die Anzahl der Samplings während der Profilerstellung, die gesammelt wurden, als diese Funktion direkt ausgeführt wurde \(d. h., während sich diese Funktion an erster Stelle der Aufrufliste befunden hat\).  Samplings, die beim Ausführen von untergeordneten Funktionen dieser Funktion gesammelt wurden, sind nicht in den exklusiven Werten enthalten.<br />-   Bei einer Aufruferfunktion die Anzahl von exklusiven Samplings der aktuellen Funktion, die gesammelt wurden, als diese Funktion die aktuelle Funktion aufgerufen hat.<br />-   Bei einer aufgerufenen Funktion die Anzahl von exklusiven Samplings dieser Funktion, die gesammelt wurden, als die aktuelle Funktion diese Funktion aufgerufen hat.|  
|**Exklusive Samplings in %**|Der Prozentsatz aller Samplings während der Profilerstellung, die exklusive Samplings dieser Funktion waren.|  
  
## Siehe auch  
 [Aufrufer\-\/Aufgerufener\-Ansicht \- Sampling](../profiling/caller-callee-view-dotnet-memory-sampling-data.md)   
 [Aufrufer\-\/Aufgerufener\-Ansicht \- Instrumentation](../profiling/caller-callee-view-net-memory-instrumentation-data.md)   
 [Aufrufer\-\/Aufgerufener\-Ansicht](../profiling/caller-callee-view-instrumentation-data.md)