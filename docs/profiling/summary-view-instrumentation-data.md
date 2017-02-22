---
title: "Zusammenfassungsansicht – Profiler-Instrumentationsdaten | Microsoft Docs"
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
  - "Zusammenfassungsansicht"
ms.assetid: 0a3b3a1f-e22b-4ac8-b46e-71694e9b2cf1
caps.latest.revision: 11
caps.handback.revision: 11
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# Zusammenfassungsansicht – Profiler-Instrumentationsdaten
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Die Zusammenfassungsansicht zeigt Informationen zu den leistungsintensivsten Funktionen während einer Profilerstellung an.  Weitere Informationen, einschließlich einer Beschreibung der Benachrichtigungslinks und Berichtslisten, finden Sie unter [Zusammenfassungsansicht](../profiling/summary-view.md).  
  
## Zeitachsendiagramm  
 Das Zeitachsendiagramm in der Zusammenfassungsansicht zeigt die CPU\-Auslastung \(Prozessorauslastung\) durch die profilierte Anwendung über den Zeitraum der Profilerstellung an.  Sie können die Ansicht mithilfe des Zeitachsendiagramms nach einem ausgewählten Zeitraum filtern.  Weitere Informationen finden Sie unter [Gewusst wie: Filtern von Berichtsansichten aus der Zeitachsenübersicht](../profiling/how-to-filter-report-views-from-the-summary-timeline.md).  
  
## Langsamster Pfad  
 Unter **Langsamster Pfad** wird der Ausführungspfad angezeigt, für den die meiste Zeit aufgewendet wurde.  Sie können auf eine Funktion klicken, um die Ansicht "Funktionsdetails" für die Funktion anzuzeigen.  Klicken Sie mit der rechten Maustaste auf eine Funktion, und klicken Sie danach auf eine Ansicht in der Liste, um andere Ansichten für die Funktion anzuzeigen.  
  
 **Langsamster Pfad** umfasst die folgenden Daten für jede Funktion:  
  
|Spalte|**Beschreibung**|  
|------------|----------------------|  
|**Name**|Der Name der Funktion.|  
|**Verstrichene inklusive Zeit in %**|Der Prozentsatz der gesamten Zeit für Profilerstellungsdaten, die die Funktion zur Ausführung von Code im Funktionstext und in den von der Funktion aufgerufenen Funktionen aufgewendet hat.|  
|**Verstrichene exklusive Zeit in %**|Der Prozentsatz der gesamten Zeit für Profilerstellungsdaten, die die Funktion zur Ausführung von Code im Funktionstext aufgewendet hat.  Die Zeit, die für von der Funktion aufgerufene Funktionen aufgewendet wurde, ist nicht enthalten.|  
  
## Funktionen mit den meisten einzelnen Aufgaben  
 Eine Liste der Funktionen, die die meiste Zeit für das Ausführen von Code im Funktionstext und nicht für aufgerufene Funktionen aufgewendet haben.  
  
 **Funktionen mit den meisten einzelnen Aufgaben** enthält folgende Daten für jede Funktion:  
  
|Spalte|**Beschreibung**|  
|------------|----------------------|  
|**Name**|Der Name der Funktion.|  
|**Exklusive Zeit %**|Der Prozentsatz der gesamten Zeit für Profilerstellungsdaten, die die Funktion zur Ausführung von Code im Funktionstext aufgewendet hat.  Die Zeit, die für von der Funktion aufgerufene Funktionen aufgewendet wurde, ist nicht enthalten.|  
  
## Siehe auch  
 [Zusammenfassungsansicht](../profiling/summary-view-sampling-data.md)   
 [Zusammenfassungsansicht](../profiling/summary-view-dotnet-memory-data.md)