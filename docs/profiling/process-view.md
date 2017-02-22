---
title: "Prozessansicht | Microsoft Docs"
ms.custom: ""
ms.date: "12/02/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.performance.view.process"
helpviewer_keywords: 
  - "Leistungstoolberichte, Prozessansicht"
  - "Leistungstools, Prozessansicht"
  - "Prozessansicht"
  - "Profilerstellungstools, Prozessbericht"
  - "Profilerstellungstools, Prozessansicht"
ms.assetid: 6d4e2a5d-9f17-4ece-a6f1-75836e1fc382
caps.latest.revision: 12
caps.handback.revision: 12
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# Prozessansicht
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Die Prozessansicht zeigt Profilerstellungsdaten für die Prozesse und Threads an, die während der Profilerstellung ausgeführt wurden.  
  
 Prozesse werden nach Namen aufgeführt.  Threads werden als untergeordnete Knoten des Prozesses aufgeführt, der sie erstellt hat.  Threads werden nach der Funktion benannt, die den Thread gestartet hat, oder sie erhalten die Bezeichnung **\[ntdll.dll\]**, wenn keine Symbole verfügbar sind.  
  
 Um Spalten hinzuzufügen oder zu entfernen, klicken Sie mit der rechten Maustaste in die Ansicht, und wählen Sie dann **Spalten hinzufügen\/entfernen** aus.  Sie können die Daten auch durch Klicken auf einen Spaltennamen sortieren.  Weitere Informationen finden Sie unter [Gewusst wie: Anpassen von Spalten in Berichtsansichten](../profiling/how-to-customize-report-view-columns.md).  
  
 Die Spalten in der Prozessansicht sind identisch für Daten, die mit der Sampling\- oder Instrumentationsmethode generiert wurden oder .NET\-Arbeitsspeicherdaten enthalten.  Diese Spaltenwerte werden in der folgenden Tabelle beschrieben.  
  
|Spalte|**Beschreibung**|  
|------------|----------------------|  
|**Unique ID**|Ein vom Profiler generierter eindeutiger Bezeichner für den Prozess oder Thread.|  
|**ID**|Ein vom System generierter Bezeichner für den Prozess oder Thread.|  
|**Name**|Der Name des Prozesses oder Threads.|  
|**Anfangszeit**|Die Zeit in Millisekunden oder Prozessorzyklen vom Start der Profilerstellung bis zum Start des Prozesses oder Threads.|  
|**Endzeit**|Die Zeit in Millisekunden oder Prozessorzyklen vom Start der Profilerstellung bis zum Ende des Prozesses oder Threads.|  
  
## Siehe auch  
 [Datenansichten der Samplingmethode](../profiling/profiler-sampling-method-data-views.md)   
 [Instrumentationsmethoden\-Datenansichten](../profiling/instrumentation-method-data-views.md)   
 [.NET\-Arbeitsspeicherdatenansichten](../profiling/dotnet-memory-data-views.md)