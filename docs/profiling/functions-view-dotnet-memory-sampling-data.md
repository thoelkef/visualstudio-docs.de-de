---
title: "Funktionsansicht - .NET-Speichersamplingdaten im Profiler | Microsoft Docs"
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
  - "Funktionsansicht"
ms.assetid: 5d9c6302-2ffd-430e-9535-13ce795f9f7c
caps.latest.revision: 9
caps.handback.revision: 9
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# Funktionsansicht - .NET-Speichersamplingdaten im Profiler
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

In der Funktionsansicht für Profilerstellungsdaten zur .NET\-Speicherbelegung, die mit der Samplingmethode gesammelt wurden, werden die Funktionen aufgeführt, die während der Profilerstellung Speicher belegt haben. Außerdem wird die Größe und Anzahl der Zuordnungen angegeben.  
  
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
|**Inclusive Allocations**|Die Gesamtzahl der Objekte, die in dieser Funktion und den zugehörigen untergeordneten Funktionen zugeordnet wurden.|  
|**Inklusive Zuordnungen in %**|Der Prozentsatz aller Objekte, die während der Profilerstellung zugeordnet wurden und inklusive Belegungen dieser Funktion waren.|  
|**Exclusive Allocations**|Die Anzahl der Objekte, die während der direkten Ausführung der Funktion auf der obersten Ebene der Aufrufliste erstellt wurden.  Diese Zahl schließt keine in untergeordneten Funktionen erstellten Objekte ein.|  
|**Exklusive Zuordnungen in %**|Der Prozentsatz aller Objekte, die während der Profilerstellung zugeordnet wurden und exklusive Belegungen dieser Funktion waren.|  
|**Inklusive Bytes**|Die Anzahl der Bytes im Speicher, die von dieser Funktion und seinen untergeordneten Funktionen belegt wurden.|  
|**Inklusive Bytes in %**|Der Prozentsatz aller Bytes des Arbeitsspeichers, die während der Profilerstellung belegt wurden und inklusive Bytes dieser Funktion waren.|  
|**Exklusive Bytes**|Die Anzahl der Bytes im Speicher, die von dieser Funktion, jedoch nicht von den zugehörigen untergeordneten Funktionen belegt wurden.|  
|**Exklusive Bytes in %**|Der Prozentsatz aller Bytes des Arbeitsspeichers, die während der Profilerstellung belegt wurden und exklusive Bytes dieser Funktion waren.|  
  
## Siehe auch  
 [Funktionsansicht \- Instrumentation](../profiling/functions-view-dotnet-memory-instrumentation-data.md)   
 [Funktionsansicht](../profiling/functions-view-sampling-data.md)   
 [Funktionsansicht](../profiling/functions-view-instrumentation-data.md)