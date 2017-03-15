---
title: "Zusammenfassungsansicht – Profiler-.NET-Arbeitsspeicherdaten | Microsoft Docs"
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
ms.assetid: 0cb317c3-0ae6-4531-aaa8-447576eec037
caps.latest.revision: 11
caps.handback.revision: 11
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# Zusammenfassungsansicht – Profiler-.NET-Arbeitsspeicherdaten
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

In der Zusammenfassungsansicht finden Sie Informationen zu den .NET\-Funktionen und \-Typen mit der höchsten Belegung von Arbeitsspeicher und zu den Typen, die zumeist während einer Profilerstellung erstellt wurden.  Weitere Informationen, einschließlich einer Beschreibung der Benachrichtigungslinks und Berichtslisten, finden Sie unter [Zusammenfassungsansicht](../profiling/summary-view.md).  
  
## Zeitachsendiagramm  
 Das Zeitachsendiagramm in der Zusammenfassungsansicht zeigt die CPU\-Auslastung \(Prozessorauslastung\) durch die profilierte Anwendung über den Zeitraum der Profilerstellung an.  Sie können die Ansicht mithilfe des Zeitachsendiagramms nach einem ausgewählten Zeitraum filtern.  Weitere Informationen finden Sie unter [Gewusst wie: Filtern von Berichtsansichten aus der Zeitachsenübersicht](../profiling/how-to-filter-report-views-from-the-summary-timeline.md).  
  
## Funktionen, die den meisten Speicher zuordnen  
 Führt die Funktionen auf, die die größte Anzahl von Bytes im Arbeitsspeicher während der Profilerstellung belegt haben.  
  
|Spalte|**Beschreibung**|  
|------------|----------------------|  
|**Name**|Der Name der Funktion.|  
|**Bytes %**|Der Prozentsatz aller zugeordneten Bytes, die während der Profilerstellung entweder von dieser Funktion oder von einer untergeordneten, von dieser Funktion aufgerufenen Funktion belegt wurden.|  
  
## Typen mit der größten Speicherbelegung  
 Führt die Typen auf, die während der Profilerstellung die größte Anzahl von Arbeitsspeicherbytes belegt haben.  
  
|Spalte|**Beschreibung**|  
|------------|----------------------|  
|**Name**|Der Name des Typs.|  
|**Bytes %**|Der Prozentsatz aller belegten Bytes, die während der Profilerstellung diesem Typ zugeordnet wurden.|  
  
## Typen mit den meisten Instanzen  
 Listet die Typen aufgeführt, die die meisten Zeiten während der Profilerstellung erstellt wurden. hatte  
  
|Spalte|**Beschreibung**|  
|------------|----------------------|  
|**Name**|Der Name des Typs.|  
|**Instanzen %**|Der Prozentsatz aller während der Profilerstellung erstellten .NET\-Objekte, bei denen es sich um Instanzen dieses Typs handelte.|  
  
## Siehe auch  
 [Zusammenfassungsansicht](../profiling/summary-view-sampling-data.md)   
 [Zusammenfassungsansicht](../profiling/summary-view-instrumentation-data.md)