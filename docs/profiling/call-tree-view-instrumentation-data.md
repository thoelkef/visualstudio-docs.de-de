---
title: "Aufrufstrukturansicht - Profiler-Instrumentationsdaten | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Aufrufstrukturansicht"
ms.assetid: 306bd176-0ce9-4a10-89ca-20b043d37d4e
caps.latest.revision: 11
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 11
---
# Aufrufstrukturansicht - Profiler-Instrumentationsdaten
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Die Werte einer Funktion in der Aufrufstruktur geben die Zeit für die Funktionsinstanzen an, die von der übergeordneten Funktion in der Aufrufliste aufgerufen wurden.  Prozentwerte werden berechnet, indem der Wert der Funktionsinstanzen mit der gesamten verstrichenen inklusiven Zeit aller Funktionen in der Profilerstellung verglichen wird.  
  
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
|**Prozessname**|Der Name, der dem Prozess zugewiesen wird.|  
|**Time Exclusive Probe Overhead**|Der von der Instrumentation verursachte zusätzliche Zeitaufwand für diese Funktion.  Der zusätzliche Testaufwand wurde bei allen exklusiven Zeiten subtrahiert.|  
|**Time Inclusive Probe Overhead**|Der von der Instrumentation verursachte zusätzliche Zeitaufwand für diese Funktion und ihre untergeordneten Funktionen.  Der zusätzliche Testaufwand wurde bei allen inklusiven Zeiten subtrahiert.|  
|**Ebene**|Die Tiefe der Funktion in der Aufrufstruktur.  Nur in [VSPerfReport](../profiling/vsperfreport.md)\-Befehlszeilenberichten.|  
  
## Werte für verstrichene inklusive Zeit  
 Die Werte der verstrichenen inklusiven Zeit geben die Zeit an, die sich Funktionsinstanzen, die von der übergeordneten Funktion in der Aufrufliste aufgerufen wurden, im Aufrufstapel befinden.  Die Zeit umfasst die Zeit in untergeordneten Funktionen, die von der Funktion aufgerufen wurden, und die Zeit für Aufrufe des Betriebssystems, z. B. Kontextwechsel und Eingabe\-\/Ausgabeoperationen.  
  
|Spalte|**Beschreibung**|  
|------------|----------------------|  
|**Elapsed Inclusive Time**|Die gesamte verstrichene inklusive Zeit aller Aufrufe dieser Funktion in diesem Kontext.|  
|**Verstrichene inklusive Zeit in %**|Der Prozentsatz der gesamten verstrichenen inklusiven Zeit, die innerhalb der verstrichenen inklusiven Zeit dieser Funktion in diesem Kontext auf die Profilerstellung entfällt.|  
|**Durchschnittl. verstrichene inklusive Zeit**|Die durchschnittliche verstrichene inklusive Zeit eines Aufrufs dieser Funktion in diesem Kontext.|  
|**Maximal verstrichene inklusive Zeit**|Die maximal verstrichene inklusive Zeit eines Aufrufs dieser Funktion in diesem Kontext.|  
|**Mindestens verstrichene inklusive Zeit**|Die mindestens verstrichene inklusive Zeit eines Aufrufs dieser Funktion in diesem Kontext.|  
  
## Werte für verstrichene exklusive Zeit  
 Verstrichene exklusive Werte geben die Zeit an, die Funktionsinstanzen, die von der übergeordneten Funktion in der Aufrufstruktur aufgerufen wurde, Code im Funktionsrumpf ausgeführt haben, d. h., als sich die Funktion an erster Stelle der Aufrufliste befunden hat.  Die Zeit beinhaltet die Zeit für Aufrufe des Betriebssystems, z. B. Kontextwechsel und Eingabe\-\/Ausgabeoperationen.  Auch die Zeit, die in von der Funktion aufgerufenen untergeordneten Funktionen aufgewendet wurde, wird jedoch nicht berücksichtigt.  
  
|Spalte|**Beschreibung**|  
|------------|----------------------|  
|**Elapsed Exclusive Time**|Die gesamte verstrichene exklusive Zeit aller Aufrufe dieser Funktion in diesem Kontext.|  
|**Verstrichene exklusive Zeit in %**|Der Prozentsatz der gesamten verstrichenen exklusiven Zeit, die innerhalb der verstrichenen exklusiven Zeit dieser Funktion in diesem Kontext auf die Profilerstellung entfällt.|  
|**Durchschnittl. verstrichene exklusive Zeit**|Die durchschnittlich verstrichene exklusive Zeit eines Aufrufs dieser Funktion in diesem Kontext.|  
|**Maximal verstrichene exklusive Zeit**|Die maximal verstrichene exklusive Zeit eines Aufrufs dieser Funktion in diesem Kontext.|  
|**Mindestens verstrichene exklusive Zeit**|Die mindestens verstrichene exklusive Zeit eines Aufrufs dieser Funktion in diesem Kontext.|  
  
## Werte für inklusive Anwendungszeit  
 Die Werte der inklusiven Anwendungszeit geben die Zeit an, die sich Funktionsinstanzen, die von der übergeordneten Funktion in der Aufrufliste aufgerufen wurden, im Aufrufstapel befanden.  Die Zeit umfasst nicht die Zeit für Aufrufe des Betriebssystems, z. B. Kontextwechsel und Eingabe\-\/Ausgabeoperationen, jedoch die Zeit in untergeordneten Funktionen, die von der Funktion aufgerufen wurden.  
  
|Spalte|**Beschreibung**|  
|------------|----------------------|  
|**Application Inclusive Time**|Die gesamte inklusive Anwendungszeit aller Aufrufe dieser Funktion in diesem Kontext.|  
|**Inklusive Anwendungszeit in %**|Der Prozentsatz der insgesamt verstrichenen inklusiven Zeit, die innerhalb der verstrichenen inklusiven Zeit dieser Funktion in diesem Kontext auf die Profilerstellung entfällt.|  
|**Durchschnittl. inklusive Anwendungszeit**|Die durchschnittliche inklusive Anwendungszeit eines Aufrufs dieser Funktion in diesem Kontext.|  
|**Maximale inklusive Anwendungszeit**|Die maximale inklusive Anwendungszeit eines Aufrufs dieser Funktion in diesem Kontext.|  
|**Minimale inklusive Anwendungszeit**|Die minimale inklusive Anwendungszeit eines Aufrufs dieser Funktion in diesem Kontext.|  
  
## Werte für exklusive Anwendungszeit  
 Die Werte für exklusive Anwendungszeit geben die Zeit an, die Funktionsinstanzen, die von der übergeordneten Funktion in der Aufrufstruktur aufgerufen wurde, direkt Code im Funktionsrumpf ausgeführt haben, d. h., als sich die Funktion an erster Stelle der Aufrufliste befunden hat.  Die Zeit umfasst nicht die Zeit für Aufrufe des Betriebssystems, z. B. Kontextwechsel und Eingabe\-\/Ausgabeoperationen.  Auch die Zeit, die in von der Funktion aufgerufenen untergeordneten Funktionen aufgewendet wurde, wird nicht berücksichtigt.  
  
|Spalte|**Beschreibung**|  
|------------|----------------------|  
|**Application Exclusive Time**|Die gesamte exklusive Anwendungszeit aller Aufrufe dieser Funktion in diesem Kontext.|  
|**Exklusive Anwendungszeit in %**|Der Prozentsatz der gesamten verstrichenen exklusiven Zeit, die innerhalb der exklusiven Gesamtanwendungszeit dieser Funktion in diesem Kontext auf die Profilerstellung entfällt.|  
|**Durchschnittl. exklusive Anwendungszeit**|Die durchschnittliche exklusive Anwendungszeit eines Aufrufs dieser Funktion in diesem Kontext.|  
|**Maximale exklusive Anwendungszeit**|Die maximale exklusive Anwendungszeit eines Aufrufs dieser Funktion in diesem Kontext.|  
|**Minimale exklusive Anwendungszeit**|Die minimale exklusive Anwendungszeit eines Aufrufs dieser Funktion in diesem Kontext.|  
  
## Siehe auch  
 [Gewusst wie: Anpassen von Spalten in Berichtsansichten](../profiling/how-to-customize-report-view-columns.md)   
 [Aufrufstrukturansicht](../profiling/call-tree-view-sampling-data.md)   
 [Aufrufstrukturansicht \- Instrumentation](../profiling/call-tree-view-dotnet-memory-instrumentation-data.md)   
 [Aufrufstrukturansicht \- Sampling](../profiling/call-tree-view-dotnet-memory-sampling-data.md)