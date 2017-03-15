---
title: "Funktionsansicht - Profiler-Instrumentationsdaten | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Funktionsansicht"
ms.assetid: 595d91c8-a42b-4644-85b8-39e8140a5dfe
caps.latest.revision: 11
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 11
---
# Funktionsansicht - Profiler-Instrumentationsdaten
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Die Funktionsberichtsansicht führt Profilerstellungsdaten nach dem Funktionsnamen auf.  
  
## Allgemein  
 Die allgemeinen Spalten bezeichnen die Funktion in einer Ansichtszeile.  
  
|Spalte|**Beschreibung**|  
|------------|----------------------|  
|**Function Name**|Der Name der Funktion.|  
|**Function Address**|Die Adresse der Funktion.|  
|**Funktionszeilennummer**|Die Zeilennummer des Anfangs dieser Funktion in der Quelldatei.|  
|**Number of Calls**|Die Gesamtzahl der Aufrufe der Funktion.|  
|**Quelldatei**|Die Quelldatei, die die Definition der Funktion enthält.|  
|**Modulname**|Der Name des Moduls, das die Funktion enthält.|  
|**Modulpfad**|Der Pfad des Moduls, das die Funktion enthält.|  
|**Prozess\-ID**|Die Prozess\-ID \(PID\) der Profilerstellung.|  
|**Prozessname**|Der Prozessname.|  
|**Time Exclusive Probe Overhead**|Der von der Instrumentation verursachte zusätzliche Zeitaufwand für diese Funktion.  Dieser umfasst jedoch nicht den zusätzlichen Zeitaufwand in Funktionen, die von dieser Funktion aufgerufen wurden.  Der zusätzliche Testaufwand wurde bei allen exklusiven Zeiten subtrahiert.|  
|**Time Inclusive Probe Overhead**|Der von der Instrumentation verursachte zusätzliche Zeitaufwand für diese Funktion und ihre untergeordneten Funktionen.  Dieser umfasst auch den zusätzlichen Zeitaufwand in Funktionen, die von dieser Funktion aufgerufen wurden.  Der zusätzliche Testaufwand wurde bei allen inklusiven Zeiten subtrahiert.|  
  
## Werte für verstrichene inklusive Zeit  
 Werte für die verstrichene inklusive Zeit geben an, wie lange sich eine Funktion in der Aufrufliste befunden hat.  Die Zeit umfasst sowohl die Zeit in untergeordneten Funktionen der aufgerufenen Funktion als auch die Zeit für Aufrufe des Betriebssystems, z. B. Kontextwechsel und Eingabe\-\/Ausgabeoperationen.  
  
|Spalte|**Beschreibung**|  
|------------|----------------------|  
|**Elapsed Inclusive Time**|Die insgesamt verstrichene inklusive Zeit aller Aufrufe dieser Funktion.|  
|**Verstrichene inklusive Zeit in %**|Der Prozentsatz der gesamten verstrichenen inklusiven Zeit, die innerhalb der verstrichenen inklusiven Zeit dieser Funktion auf die Profilerstellung entfällt.|  
|**Durchschnittl. verstrichene inklusive Zeit**|Die durchschnittliche verstrichene inklusive Zeit für einen Aufruf dieser Funktion.|  
|**Maximal verstrichene inklusive Zeit**|Die maximal verstrichene inklusive Zeit für einen Aufruf dieser Funktion.|  
|**Mindestens verstrichene inklusive Zeit**|Die mindestens verstrichene inklusive Zeit für einen Aufruf dieser Funktion.|  
  
## Werte für verstrichene exklusive Zeit  
 Die Werte für verstrichene exklusive Zeit geben die Zeit an, die eine Funktion Code im Funktionsrumpf ausgeführt hat, d. h., als sich die Funktion an erster Stelle der Aufrufliste befunden hat.  Die Zeit umfasst die Zeit für Aufrufe des Betriebssystems, z. B. Kontextwechsel und Eingabe\-\/Ausgabeoperationen, jedoch nicht die Zeit in Funktionen, die von der Funktion aufgerufen wurden.  
  
|Spalte|**Beschreibung**|  
|------------|----------------------|  
|**Elapsed Exclusive Time**|Die insgesamt verstrichene exklusive Zeit aller Aufrufe dieser Funktion.|  
|**Verstrichene exklusive Zeit in %**|Der Prozentsatz der gesamten verstrichenen exklusiven Zeit während der Profilerstellung, die sich auf die insgesamt verstrichene exklusive Zeit dieser Funktion bezieht.|  
|**Durchschnittl. verstrichene exklusive Zeit**|Die durchschnittliche verstrichene exklusive Zeit für einen Aufruf dieser Funktion.|  
|**Maximal verstrichene exklusive Zeit**|Die maximal verstrichene exklusive Zeit für einen Aufruf dieser Funktion.|  
|**Mindestens verstrichene exklusive Zeit**|Die mindestens verstrichene exklusive Zeit für einen Aufruf dieser Funktion.|  
  
## Werte für inklusive Anwendungszeit  
 Werte für die inklusive Anwendungszeit geben die Zeit an, die sich eine Funktion in der Aufrufliste befunden hat.  Die Zeit umfasst nicht die Zeit für Aufrufe des Betriebssystems, z. B. Kontextwechsel und Eingabe\-\/Ausgabeoperationen, sie enthält jedoch die Zeit in Funktionen, die von der Funktion aufgerufen wurden.  
  
|Spalte|**Beschreibung**|  
|------------|----------------------|  
|**Application Inclusive Time**|Die gesamte inklusive Anwendungszeit aller Aufrufe dieser Funktion.|  
|**Inklusive Anwendungszeit in %**|Der Prozentsatz der gesamten verstrichenen inklusiven Zeit während der Profilerstellung, die sich auf die gesamte inklusive Anwendungszeit dieser Funktion bezieht.|  
|**Durchschnittl. inklusive Anwendungszeit**|Die durchschnittliche inklusive Anwendungszeit für einen Aufruf dieser Funktion.|  
|**Maximale inklusive Anwendungszeit**|Die maximale inklusive Anwendungszeit für einen Aufruf dieser Funktion.|  
|**Minimale inklusive Anwendungszeit**|Die minimale inklusive Anwendungszeit für einen Aufruf dieser Funktion.|  
  
## Werte für exklusive Anwendungszeit  
 Werte für exklusive Anwendungszeit geben die Zeit an, die eine Funktion direkt an erster Stelle in der Aufrufliste ausgeführt wurde.  Die Zeit umfasst weder die Zeit für Aufrufe des Betriebssystems, z. B. Kontextwechsel und Eingabe\-\/Ausgabeoperationen, noch die Zeit in Funktionen, die von der Funktion aufgerufen wurden.  
  
|Spalte|**Beschreibung**|  
|------------|----------------------|  
|**Application Exclusive Time**|Die gesamte exklusive Anwendungszeit aller Aufrufe dieser Funktion.|  
|**Exklusive Anwendungszeit in %**|Der Prozentsatz der gesamten verstrichenen exklusiven Zeit während der Profilerstellung, die sich auf die gesamte exklusive Anwendungszeit dieser Funktion bezieht.|  
|**Durchschnittl. exklusive Anwendungszeit**|Die durchschnittliche exklusive Anwendungszeit für einen Aufruf dieser Funktion.|  
|**Maximale exklusive Anwendungszeit**|Die maximale exklusive Anwendungszeit für einen Aufruf dieser Funktion.|  
|**Minimale exklusive Anwendungszeit**|Die minimale exklusive Anwendungszeit für einen Aufruf dieser Funktion.|  
  
## Siehe auch  
 [Gewusst wie: Anpassen von Spalten in Berichtsansichten](../profiling/how-to-customize-report-view-columns.md)   
 [Funktionsansicht](../profiling/functions-view-sampling-data.md)   
 [Funktionsansicht \- Sampling](../profiling/functions-view-dotnet-memory-sampling-data.md)   
 [Funktionsansicht \- Instrumentation](../profiling/functions-view-dotnet-memory-instrumentation-data.md)