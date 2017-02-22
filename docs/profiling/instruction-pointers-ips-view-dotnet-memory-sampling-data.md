---
title: "Anweisungszeigeransicht - .NET-Speichersamplingdaten im Profiler | Microsoft Docs"
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
  - "Anweisungszeiger (Ansicht)"
ms.assetid: 7d91cc14-e8e9-4ebb-b14f-b9f0da770508
caps.latest.revision: 9
caps.handback.revision: 9
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# Anweisungszeigeransicht - .NET-Speichersamplingdaten im Profiler
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Die Anweisungszeigeransicht der Profilerstellungsdaten für die .NET\-Speicherbelegung, die mit der Samplingmethode erfasst wurden, führt die Assemblyanweisungen auf, die während der Profilerstellungsausführung Arbeitsspeicher belegt haben.  In Spalten der Ansicht werden auch die Größe und die Anzahl von Zuordnungen angezeigt.  
  
 Nur exklusive Werte werden aufgeführt.  
  
|Spalte|**Beschreibung**|  
|------------|----------------------|  
|**Prozess\-ID**|Die Prozess\-ID \(PID\) der Profilerstellung.|  
|**Prozessname**|Der Prozessname.|  
|**Modulname**|Der Name des Moduls, das die Anweisung enthält.|  
|**Modulpfad**|Der Pfad des Moduls, das die Anweisung enthält.|  
|**Quelldatei**|Die Quelldatei, die die Anweisung enthält.|  
|**Function Name**|Der Name der Funktion.|  
|**Funktionszeilennummer**|Die Zeilennummer des Anfangs dieser Funktion in der Quelldatei.|  
|**Function Address**|Die Startadresse der Funktion.|  
|**Source Line Begin**|Die Startzeilennummer in der Quelldatei, bei der die Zuordnung aufgetreten ist.|  
|**Source Line End**|Die Endzeilennummer in der Quelldatei, bei der die Zuordnung aufgetreten ist.|  
|**Source Character Begin**|Der Offset des Startzeichens in der Quelldateizeile, bei dem die Zuordnung aufgetreten ist.|  
|**Source Character End**|Der Offset des Endzeichens in der Quelldateizeile, bei dem die Zuordnung aufgetreten ist.|  
|**Instruction Address**|Die Adresse der Anweisung.|  
|**Exclusive Allocations**|Die Gesamtzahl der von der Anweisung erstellten Objekte.|  
|**Exklusive Zuordnungen in %**|Der Prozentsatz aller in der Profilerstellungsausführung erstellten Objekte, die von der Anweisung zugeordnet wurden.|  
|**Exklusive Bytes**|Die Anzahl der für Profilerstellung belegten Bytes des Arbeitsspeichers, die von der Anweisung zugeordnet wurden.|  
|**Exklusive Bytes in %**|Der Prozentsatz aller bei der Profilerstellung belegten Bytes des Arbeitsspeichers, die von der Anweisung zugeordnet wurden.|  
  
## Siehe auch  
 [Anweisungszeigeransicht](../profiling/instruction-pointers-ips-view-sampling-data.md)