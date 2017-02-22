---
title: "Aufrufer-/Aufgerufener-Ansicht - .NET-Speichersamplingdaten im Profiler | Microsoft Docs"
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
  - "Aufrufer-/Aufgerufener-Ansicht"
ms.assetid: 36f5b4de-5686-4f40-9e72-f4aee27d833c
caps.latest.revision: 12
caps.handback.revision: 12
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# Aufrufer-/Aufgerufener-Ansicht - .NET-Speichersamplingdaten im Profiler
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

In der Aufrufer\-\/Aufgerufener\-Ansicht werden .NET\-Speicherdaten einer Profilerstellung für eine ausgewählte Funktion und die übergeordneten und untergeordneten Funktionen angezeigt.  Die Aufrufer\-\/Aufgerufener\-Ansicht enthält drei Raster.  
  
 **Aktuelle Funktion** wird im mittleren Raster angezeigt und zeigt Speicherinformationen zur Profilerstellung für die ausgewählte Funktion an.  Die Werte umfassen alle Samplingaufrufe der Funktion.  
  
 **Funktionen, die die aktuelle Funktion aufgerufen haben** wird im obersten Raster angezeigt und zeigt die Menge der Werte der ausgewählten \(aktuellen\) Funktion an, die durch Aufrufe der \(übergeordneten\) Aufruferfunktion generiert wurden.  
  
 **Funktionen, die von der aktuellen Funktion aufgerufen wurden** wird im untersten Raster angezeigt und zeigt Speicherdaten zur Profilerstellung für die aufgerufenen \(untergeordneten\) Funktionen der ausgewählten Funktion an, wenn die untergeordnete Funktion von der aktuellen Funktion aufgerufen wurde.  
  
 Doppelklicken Sie auf eine Zeile einer Aufrufer\- oder Aufgerufener\-Funktion, um diese Zeile zur aktuellen Funktion zu machen.  
  
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
|**Typ**|Der Kontext der Funktion:<br /><br /> **0** – die aktuelle Funktion<br /><br /> **1** – eine Funktion, die die aktuelle Funktion aufruft<br /><br /> **2** – eine Funktion, die von der aktuellen Funktion aufgerufen wird<br /><br /> Nur in [VSPerfReport](../profiling/vsperfreport.md)\-Befehlszeilenberichten.|  
|**Ebene**|Die Tiefe der Funktion in der Aufrufstruktur.  Nur in [VSPerfReport](../profiling/vsperfreport.md)\-Befehlszeilenberichten.|  
|**Inclusive Allocations**|-   Bei der aktuellen Funktion die Anzahl der Objekte, die während der Profilerstellung von der Funktion zugeordnet wurden.  Diese Zahl schließt in aufgerufenen Funktionen erstellte Objekte ein.<br />-   Bei einer aufrufenden Funktion die Anzahl von inklusiven Zuordnungen der aktuellen Funktion, die von Aufrufen von dieser Funktion generiert wurden.<br />-   Bei einer aufgerufenen Funktion die Anzahl von Objekten, die von den Instanzen dieser Funktion zugeordnet wurden, die von dieser Funktion aufgerufen wurden.  Die Zahl umfasst Zuordnungen von Funktionen, die von dieser aufgerufenen Funktion aufgerufen wurden.|  
|**Inklusive Zuordnungen in %**|Der Prozentsatz aller Objekte, die während der Profilerstellung erstellt wurden und inklusive Belegungen dieser Funktion waren.|  
|**Exclusive Allocations**|-   Bei der aktuellen Funktion die Anzahl der Objekte, die während der Ausführung von Code im Funktionsrumpf \(d. h., während sich die Funktion auf der obersten Ebene der Aufrufliste befand\) erstellt wurden.  Die Zahl umfasst keine Objekte, die in den von dieser Funktion aufgerufenen Funktionen erstellt wurden.<br />-   Bei einer aufrufenden Funktion die Anzahl von exklusiven Zuordnungen der aktuellen Funktion, die von Aufrufen von dieser Funktion generiert wurden.<br />-   Bei einer aufgerufenen Funktion die Anzahl von Objekten, die von den Instanzen dieser Funktion erstellt wurden, die von dieser Funktion aufgerufen wurden.  Die Zahl umfasst keine Objekte, die in den von der aufgerufenen Funktion aufgerufenen Funktionen erstellt wurden.|  
|**Exklusive Zuordnungen in %**|Der Prozentsatz aller Objekte, die während der Profilerstellung erstellt wurden und inklusive Belegungen dieser Funktion waren.|  
|**Inklusive Bytes**|-   Bei der aktuellen Funktion die Anzahl der Bytes im Arbeitsspeicher, die während der Profilerstellung von der Funktion belegt wurden.  Diese Zahl umfasst auch Arbeitsspeicher, der von in dieser Funktion aufgerufenen Funktionen belegt wurde.<br />-   Bei einer aufrufenden Funktion die Anzahl von inklusiven Bytes der aktuellen Funktion, die von Aufrufen von dieser aufrufenden Funktion generiert wurden.<br />-   Bei einer aufgerufenen Funktion die Anzahl von Bytes, die von den durch Aufrufe aus der aktuellen Funktion generierten Instanzen dieser Funktion belegt wurden.  Die Zahl umfasst auch Bytes, die in von dieser aufgerufenen Funktion aufgerufenen Funktionen zugeordnet wurden.|  
|**Inklusive Bytes in %**|Der Prozentsatz aller Bytes des Arbeitsspeichers, die während der Profilerstellung belegt wurden und inklusive Belegungen dieser Funktion waren.|  
|**Exklusive Bytes**|-   Bei der aktuellen Funktion die Anzahl der Bytes im Arbeitsspeicher, die während der Profilerstellung von der Funktion belegt wurden.  Diese Zahl umfasst nicht den Arbeitsspeicher, der von Funktionen belegt wurde, die von der aktuellen Funktion aufgerufen wurden.<br />-   Bei einer aufrufenden Funktion die Anzahl von exklusiven Bytes der aktuellen Funktion, die von Aufrufen von dieser aufrufenden Funktion generiert wurden.<br />-   Bei einer aufgerufenen Funktion die Anzahl von Bytes, die von den durch Aufrufe aus der aktuellen Funktion generierten Instanzen dieser Funktion belegt wurden.  Diese Zahl umfasst nicht die Bytes, die in den von der Funktion aufgerufenen Funktionen zugeordnet wurden.|  
|**Exklusive Bytes in %**|Der Prozentsatz aller Bytes des Arbeitsspeichers, die während der Profilerstellung belegt wurden und exklusive Belegungen dieser Funktion waren.|  
  
## Siehe auch  
 [Gewusst wie: Anpassen von Spalten in Berichtsansichten](../profiling/how-to-customize-report-view-columns.md)   
 [Aufrufer\-\/Aufgerufener\-Ansicht \- Instrumentation](../profiling/caller-callee-view-net-memory-instrumentation-data.md)   
 [Aufrufer\-\/Aufgerufener\-Ansicht](../profiling/caller-callee-view-sampling-data.md)   
 [Aufrufer\-\/Aufgerufener\-Ansicht](../profiling/caller-callee-view-instrumentation-data.md)