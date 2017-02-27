---
title: "Funktionsansicht – Profiler-Samplingdaten | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Sampling-Profilerstellungsmethode,Funktionsansicht"
  - "Funktionsansicht"
ms.assetid: 029d5ebb-e551-46b0-b64e-2c553d9dbb8e
caps.latest.revision: 12
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 12
---
# Funktionsansicht – Profiler-Samplingdaten
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

In der Funktionsberichtsansicht für die Samplingprofilmethode werden die Funktionen angezeigt, für die während der Profilerstellung ein Sampling ausgeführt wurde.  
  
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
|**Inclusive Samples**|Die Gesamtzahl von Samplings, die beim Ausführen dieser Funktion erfasst wurden, d. h., die Anzahl von Samplings, die erfasst wurden, während sich die Funktion in der Aufrufliste befand.  Die Anzahl umfasst Samplings, die erfasst wurden, als von dieser Funktion aufgerufene Funktionen ausgeführt wurden.|  
|**Inklusive Samplings in %**|Der Prozentsatz aller Samplings während der Profilerstellung, die inklusive Samplings dieser Funktion waren.|  
|**Exclusive Samples**|Die Gesamtzahl von Samplings, die beim Ausführen von Code im Text dieser Funktion erfasst wurden, d. h., während sich die Funktion am Beginn der Aufrufliste befand.  Dazu zählen keine Samplings, die in den Funktionen erfasst wurden, die von dieser Funktion aufgerufen wurden.|  
|**Exklusive Samplings in %**|Der Prozentsatz aller Samplings während der Profilerstellung, die exklusive Samplings dieser Funktion waren.|  
  
## Siehe auch  
 [Gewusst wie: Anpassen von Spalten in Berichtsansichten](../profiling/how-to-customize-report-view-columns.md)   
 [Funktionsansicht \- Instrumentation](../profiling/functions-view-dotnet-memory-instrumentation-data.md)   
 [Funktionsansicht \- Sampling](../profiling/functions-view-dotnet-memory-sampling-data.md)   
 [Funktionsansicht](../profiling/functions-view-instrumentation-data.md)