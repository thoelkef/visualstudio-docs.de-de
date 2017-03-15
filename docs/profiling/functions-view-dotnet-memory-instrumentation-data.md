---
title: "Funktionsansicht - .NET-Speicherinstrumentationsdaten im Profiler | Microsoft Docs"
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
ms.assetid: cd45b379-394b-4b71-828c-92cd89e46ae0
caps.latest.revision: 10
caps.handback.revision: 10
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# Funktionsansicht - .NET-Speicherinstrumentationsdaten im Profiler
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Die Funktionsansicht der Profilerstellungsdaten für die .NET\-Speicherbelegung, die mit der Instrumentationsmethode erfasst wurden, führt die Funktionen auf, die während der Profilerstellungsausführung Arbeitsspeicher belegt haben.  In einer Funktionszeile werden die Größe und die Anzahl der Belegungen sowie die Zeitsteuerungsdaten für die Funktion angegeben.  
  
## Allgemein  
  
|Spalte|**Beschreibung**|  
|------------|----------------------|  
|**Function Name**|Der Name der Funktion.|  
|**Function Address**|Die Adresse der Funktion.|  
|**Funktionszeilennummer**|Die Zeilennummer des Anfangs dieser Funktion in der Quelldatei.|  
|**Number of Calls**|Die Gesamtzahl der Aufrufe der Funktion.|  
|**Quelldatei**|Die Quelldatei mit der Definition dieser Funktion.|  
|**Modulname**|Der Name des Moduls, das die Funktion enthält.|  
|**Modulpfad**|Der Pfad des Moduls, das die Funktion enthält.|  
|**Prozess\-ID**|Die Prozess\-ID \(PID\) der Profilerstellung.|  
|**Prozessname**|Der Prozessname.|  
|**Time Exclusive Probe Overhead**|Der durch Instrumentation verursachte zusätzliche Zeitaufwand für diese Funktion.  Der zusätzliche Testaufwand wurde bei allen exklusiven Zeiten subtrahiert.|  
|**Time Inclusive Probe Overhead**|Der von der Instrumentation verursachte zusätzliche Zeitaufwand für diese Funktion und ihre untergeordneten Funktionen.  Der zusätzliche Testaufwand wurde bei allen inklusiven Zeiten subtrahiert.|  
  
## .NET\-Arbeitsspeicherwerte  
 Die inklusiven .NET\-Arbeitsspeicherwerte einer Funktion geben die Anzahl \(Zuordnungen\) und die Größe \(Bytes\) der Objekte an, die von der Funktion und ihren untergeordneten Funktionen erstellt wurden.  
  
 Die exklusiven Arbeitsspeicherwerte geben die Anzahl und die Größe der Objekte an, die von der Funktion, nicht jedoch von den zugehörigen untergeordneten Funktionen erstellt wurden.  
  
|Spalte|**Beschreibung**|  
|------------|----------------------|  
|**Inclusive Allocations**|Die Gesamtzahl der Objekte, die in dieser Funktion erstellt wurden und in Funktionen, die von dieser Funktion aufgerufen wurden.|  
|**Inklusive Zuordnungen in %**|Der Prozentsatz aller Objekte, die während der Profilerstellung zugeordnet wurden und inklusive Belegungen dieser Funktion waren.|  
|**Exclusive Allocations**|Die Gesamtzahl der Objekte, die beim Ausführen von Code im Funktionstext durch die Funktion erstellt wurden.  Diese Zahl umfasst keine Objekte, die in den von dieser Funktion aufgerufenen Funktionen erstellt wurden.|  
|**Exklusive Zuordnungen in %**|Der Prozentsatz aller Objekte, die während der Profilerstellung erstellt wurden und exklusive Belegungen dieser Funktion waren.|  
|**Inklusive Bytes**|Die Anzahl der Bytes im Speicher, die von dieser Funktion und durch von dieser Funktion aufgerufenen Funktionen belegt wurden.|  
|**Inklusive Bytes in %**|Der Prozentsatz aller Bytes des Arbeitsspeichers, die während der Profilerstellung belegt wurden und inklusive Bytes dieser Funktion waren.|  
|**Exklusive Bytes**|Die Anzahl der Bytes im Speicher, die von dieser Funktion, jedoch nicht durch von dieser Funktion aufgerufenen Funktionen, belegt wurden.|  
|**Exklusive Bytes in %**|Der Prozentsatz aller Bytes des Arbeitsspeichers, die während der Profilerstellung belegt wurden und exklusive Bytes dieser Funktion waren.|  
  
## Werte für verstrichene inklusive Zeit  
 Werte für die verstrichene inklusive Zeit geben an, wie lange sich eine Funktion in der Aufrufliste befunden hat.  Die Zeit umfasst die aufgewendete Zeit für untergeordnete Funktionen und für Aufrufe des Betriebssystems, z. B. Kontextwechsel und Eingabe\-\/Ausgabeoperationen.  
  
|Spalte|**Beschreibung**|  
|------------|----------------------|  
|**Elapsed Inclusive Time**|Die insgesamt verstrichene inklusive Zeit aller Aufrufe dieser Funktion.|  
|**Verstrichene inklusive Zeit in %**|Der Prozentsatz der gesamten verstrichenen inklusiven Zeit, die innerhalb der verstrichenen inklusiven Zeit dieser Funktion auf die Profilerstellung entfällt.|  
|**Durchschnittl. verstrichene inklusive Zeit**|Die durchschnittliche verstrichene inklusive Zeit für einen Aufruf dieser Funktion.|  
|**Maximal verstrichene inklusive Zeit**|Die maximal verstrichene inklusive Zeit für einen Aufruf dieser Funktion.|  
|**Mindestens verstrichene inklusive Zeit**|Die mindestens verstrichene inklusive Zeit für einen Aufruf dieser Funktion.|  
  
## Werte für verstrichene exklusive Zeit  
 Werte für verstrichene exklusive Zeit geben die Zeit an, die eine Funktion direkt an erster Stelle in der Aufrufliste ausgeführt wurde.  Die Zeit umfasst die Zeit für Aufrufe des Betriebssystems, z. B. Kontextwechsel und Eingabe\-\/Ausgabeoperationen, jedoch nicht die Zeit für untergeordnete Funktionen.  
  
|Spalte|**Beschreibung**|  
|------------|----------------------|  
|**Elapsed Exclusive Time**|Die insgesamt verstrichene exklusive Zeit aller Aufrufe dieser Funktion.|  
|**Verstrichene exklusive Zeit in %**|Der Prozentsatz der gesamten verstrichenen exklusiven Zeit während der Profilerstellung, die sich auf die insgesamt verstrichene exklusive Zeit dieser Funktion bezieht.|  
|**Durchschnittl. verstrichene exklusive Zeit**|Die durchschnittliche verstrichene exklusive Zeit für einen Aufruf dieser Funktion.|  
|**Maximal verstrichene exklusive Zeit**|Die maximal verstrichene exklusive Zeit für einen Aufruf dieser Funktion.|  
|**Mindestens verstrichene exklusive Zeit**|Die mindestens verstrichene exklusive Zeit für einen Aufruf dieser Funktion.|  
  
## Werte für inklusive Anwendungszeit  
 Werte für die inklusive Anwendungszeit geben die Zeit an, die sich eine Funktion in der Aufrufliste befunden hat.  Die Zeit umfasst die Zeit in untergeordneten Funktionen, jedoch nicht die Zeit für Aufrufe des Betriebssystems, z. B. Kontextwechsel und Eingabe\-\/Ausgabeoperationen.  
  
|Spalte|**Beschreibung**|  
|------------|----------------------|  
|**Application Inclusive Time**|Die gesamte inklusive Anwendungszeit aller Aufrufe dieser Funktion.|  
|**Inklusive Anwendungszeit in %**|Der Prozentsatz der gesamten verstrichenen inklusiven Zeit während der Profilerstellung, die sich auf die gesamte inklusive Anwendungszeit dieser Funktion bezieht.|  
|**Durchschnittl. inklusive Anwendungszeit**|Die durchschnittliche inklusive Anwendungszeit für einen Aufruf dieser Funktion.|  
|**Maximale inklusive Anwendungszeit**|Die maximale inklusive Anwendungszeit für einen Aufruf dieser Funktion.|  
|**Minimale inklusive Anwendungszeit**|Die minimale inklusive Anwendungszeit für einen Aufruf dieser Funktion.|  
  
## Werte für exklusive Anwendungszeit  
 Werte für exklusive Anwendungszeit geben die Zeit an, die eine Funktion direkt an erster Stelle in der Aufrufliste ausgeführt wurde.  Die Zeit umfasst weder die Zeit in untergeordneten Funktionen, noch die Zeit für Aufrufe des Betriebssystems, z. B. Kontextwechsel und Eingabe\-\/Ausgabeoperationen.  
  
|Spalte|**Beschreibung**|  
|------------|----------------------|  
|**Application Exclusive Time**|Die gesamte exklusive Anwendungszeit aller Aufrufe dieser Funktion.|  
|**Exklusive Anwendungszeit in %**|Der Prozentsatz der gesamten verstrichenen exklusiven Zeit während der Profilerstellung, die sich auf die gesamte exklusive Anwendungszeit dieser Funktion bezieht.|  
|**Durchschnittl. exklusive Anwendungszeit**|Die durchschnittliche exklusive Anwendungszeit für einen Aufruf dieser Funktion.|  
|**Maximale exklusive Anwendungszeit**|Die maximale exklusive Anwendungszeit für einen Aufruf dieser Funktion.|  
|**Minimale exklusive Anwendungszeit**|Die minimale exklusive Anwendungszeit für einen Aufruf dieser Funktion.|  
  
## Siehe auch  
 [Gewusst wie: Anpassen von Spalten in Berichtsansichten](../profiling/how-to-customize-report-view-columns.md)   
 [Funktionsansicht \- Sampling](../profiling/functions-view-dotnet-memory-sampling-data.md)   
 [Funktionsansicht](../profiling/functions-view-instrumentation-data.md)   
 [Funktionsansicht](../profiling/functions-view-sampling-data.md)