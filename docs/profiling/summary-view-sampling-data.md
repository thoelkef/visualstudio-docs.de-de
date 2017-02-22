---
title: "Zusammenfassungsansicht - Profiler-Samplingdaten | Microsoft Docs"
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
  - "Sampling-Profilerstellungsmethode, Zusammenfassungsansicht"
  - "Zusammenfassungsansicht"
ms.assetid: 79056873-2985-40be-9112-cdbc26a65156
caps.latest.revision: 13
caps.handback.revision: 13
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# Zusammenfassungsansicht - Profiler-Samplingdaten
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Die Zusammenfassungsansicht zeigt Informationen zu den leistungsintensivsten Funktionen während einer Profilerstellung an.  Weitere Informationen, einschließlich einer Beschreibung der Benachrichtigungslinks und Berichtslisten, finden Sie unter [Zusammenfassungsansicht](../profiling/summary-view.md).  
  
> [!NOTE]
>  Verbesserte Sicherheitsfeatures in Windows 8 und Windows Server 2012 erforderten tiefgreifende Änderungen bei der Datenerfassung des Visual Studio\-Profilers auf diesen Plattformen.  Außerdem benötigen Windows Store\-Apps neue Erfassungsmethoden.  Siehe [Profilerstellung für Windows 8\- und Windows Server 2012\-Anwendungen](../profiling/performance-tools-on-windows-8-and-windows-server-2012-applications.md).  
  
## Zeitachsendiagramm  
 Das Zeitachsendiagramm in der Zusammenfassungsansicht zeigt die CPU\-Auslastung \(Prozessorauslastung\) der profilierten Anwendung über den Zeitraum der Profilerstellung in Prozent an.  Sie können die Ansicht mithilfe des Zeitachsendiagramms nach einem ausgewählten Zeitraum filtern.  Weitere Informationen finden Sie unter [Gewusst wie: Filtern von Berichtsansichten aus der Zeitachsenübersicht](../profiling/how-to-filter-report-views-from-the-summary-timeline.md).  
  
## Langsamster Pfad  
 Durch die Option **Langsamster Pfad** wird der Ausführungspfad angezeigt, an dem die meisten Samplings erfasst wurden.  Sie können auf eine Funktion klicken, um die Ansicht "Funktionsdetails" für die Funktion anzuzeigen.  Klicken Sie mit der rechten Maustaste auf eine Funktion, und klicken Sie danach auf eine Ansicht in der Liste, um andere Ansichten für die Funktion anzuzeigen.  
  
 **Langsamster Pfad** umfasst die folgenden Daten für jede Funktion:  
  
|Spalte|**Beschreibung**|  
|------------|----------------------|  
|**Name**|Der Name der Funktion.|  
|**Inklusive Samplings in %**|Der Prozentsatz aller Samplings, die aufgetreten sind, als diese Funktion oder eine Funktion, die von dieser Funktion aufgerufen wurde, ausgeführt wurde.|  
|**Exklusive Samplings in %**|Der Prozentsatz aller Samplings, die aufgetreten sind, als die Funktion Code im Funktionsrumpf ausführte.  Samplings, die in Funktionen gesammelt wurden, die von dieser Funktion aufgerufen wurden, sind nicht eingeschlossen.|  
  
## Funktionen mit den meisten einzelnen Aufgaben  
 Die Liste **Funktionen, die die meisten Einzelaufgaben durchführen** zeigt die Funktionen an, die über die größte Anzahl von exklusiven Samplings in der Profilerstellung verfügen.  Ein exklusives Sampling wird einer Funktion zugewiesen, wenn die Funktion zum Zeitpunkt der Erfassung des Samplings ihren eigenen Code ausführt.  Ein exklusives Sampling wird einer Funktion nicht zugewiesen, wenn die Funktion zum Zeitpunkt der Erfassung des Samplings eine andere Funktion aufruft.  Eine große Anzahl von exklusiven Samplings gibt an, dass viel Zeit in der Funktion selbst aufgewendet wurde.  
  
 Sie können auf eine Funktion klicken, um die Ansicht "Funktionsdetails" für die Funktion anzuzeigen.  Klicken Sie mit der rechten Maustaste auf eine Funktion, und klicken Sie danach auf eine Ansicht in der Liste, um andere Ansichten für die Funktion anzuzeigen.  
  
 **Funktionen mit den meisten einzelnen Aufgaben** enthält folgende Daten für jede Funktion:  
  
|Spalte|**Beschreibung**|  
|------------|----------------------|  
|**Name**|Der Name der Funktion.|  
|**Exklusive Samplings in %**|Der Prozentsatz aller Samplings in der Profilerstellung, die gesammelt wurden, als die Funktion Code in ihrem Funktionsrumpf ausführte.  Der Prozentsatz schließt Samplings aus, die gesammelt wurden, als Funktionen ausgeführt wurden, die von dieser Funktion aufgerufen wurden.|  
  
## Siehe auch  
 [Zusammenfassungsansicht](../profiling/summary-view-dotnet-memory-data.md)   
 [Zusammenfassungsansicht](../profiling/summary-view-instrumentation-data.md)