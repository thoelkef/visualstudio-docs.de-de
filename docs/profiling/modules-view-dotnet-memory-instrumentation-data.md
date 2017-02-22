---
title: "Modulansicht – .NET-Speicherinstrumentationsdaten im Profiler | Microsoft Docs"
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
  - "Modulansicht"
ms.assetid: 26516139-0981-41de-917d-ad5769391b8d
caps.latest.revision: 10
caps.handback.revision: 10
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# Modulansicht – .NET-Speicherinstrumentationsdaten im Profiler
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

In der Modulansicht der .NET\-Speicherbelegungsdaten, die mit der Instrumentationsmethode gesammelt wurden, werden die Arbeitsspeicher\- und Zeitsteuerungsdaten nach den Modulen gruppiert, die während der Profilerstellung ausgeführt wurden.  Die Profilerstellungsdaten für die Funktionen des Moduls werden unter dem Modulknoten aufgeführt.  
  
## Allgemein  
  
|Spalte|**Beschreibung**|  
|------------|----------------------|  
|**Name**|Der Name der Funktion oder des Moduls.|  
|**Funktionszeilennummer**|Die Zeilennummer des Anfangs dieser Funktion in der Quelldatei.|  
|**Number of Calls**|Die Gesamtzahl von Aufrufen dieser Funktion oder dieses Moduls.|  
|**Quelldatei**|Die Quelldatei mit der Definition dieser Funktion.|  
|**Modulname**|Der Name des Moduls, das die Funktion enthält.|  
|**Modulpfad**|Der Pfad des Moduls, das die Funktion enthält.|  
|**Prozess\-ID**|Die Prozess\-ID \(PID\) der Profilerstellung.|  
|**Prozessname**|Der Name des Prozesses, in dem das Modul oder die Funktion ausgeführt wurde.|  
|**Time Exclusive Probe Overhead**|Der zusätzliche Zeitaufwand für die Funktion oder das Modul aufgrund der Instrumentation.|  
|**Time Inclusive Probe Overhead**|Der zusätzliche Zeitaufwand für die Funktion oder das Modul und die zugehörigen untergeordneten Funktionen aufgrund der Instrumentation.|  
  
## .NET\-Arbeitsspeicherwerte  
 Die inklusiven .NET\-Arbeitsspeicherwerte einer Funktion geben die Anzahl \(Zuordnungen\) und die Größe \(Bytes\) der Objekte an, die von der Funktion und ihren untergeordneten Funktionen erstellt wurden.  
  
 Die exklusiven Arbeitsspeicherwerte geben die Anzahl und die Größe der Objekte an, die von der Funktion, nicht jedoch von den zugehörigen untergeordneten Funktionen erstellt wurden.  
  
 Die Werte des inklusiven und des exklusiven Arbeitsspeichers eines Moduls sind die Summe der Werte des inklusiven und des exklusiven Arbeitsspeichers der Funktionen in dem Modul.  
  
|Spalte|**Beschreibung**|  
|------------|----------------------|  
|**Inclusive Allocations**|-   Bei einer Funktion die Gesamtzahl von Objekten, die von der Funktion erstellt wurden.  Die Zahl umfasst auch Objekte, die von den von der Funktion aufgerufenen Funktionen erstellt wurden.<br />-   Bei einem Modul die Anzahl von Objekten während einer Profilerstellung, die zugeordnet wurden, als mindestens eine Funktion des Moduls ausgeführt wurde.  Diese Zahl umfasst auch Objekte, die von durch den Aufruf von Modulfunktionen generierten Funktionen zugeordnet wurden.|  
|**Inklusive Zuordnungen in %**|Der Prozentsatz aller Objekte, die während der Profilerstellung zugeordnet wurden und inklusive Zuordnungen dieses Moduls oder dieser Funktion waren.|  
|**Exclusive Allocations**|-   Bei einer Funktion die Anzahl der Objekte, die während der Ausführung von Code im Funktionstext \(d. h., während sich die Funktion auf der obersten Ebene der Aufrufliste befand\) erstellt wurden.  Diese Zahl umfasst keine Objekte, die in den von dieser Funktion aufgerufenen Funktionen erstellt wurden.<br />-   Bei einem Modul die Summe der exklusiven Zuordnungen der Funktionen im Modul.|  
|**Exklusive Zuordnungen in %**|Der Prozentsatz aller Objekte, die während der Profilerstellung zugeordnet wurden und exklusive Zuordnungen dieses Moduls oder dieser Funktion waren.|  
|**Exklusive Bytes**|-   Bei einer Funktion die gesamte Anzahl von Bytes im Arbeitsspeicher, die während der Ausführung von Code im Funktionstext \(d. h., während sich die Funktion auf der obersten Ebene der Aufrufliste befand\) zugeordnet wurden.  Diese Zahl umfasst nicht die Bytes, die in den von der Funktion aufgerufenen Funktionen zugeordnet wurden.<br />-   Bei einem Modul die Summe der exklusiven Bytes, die von den Funktionen im Modul zugeordnet wurden.|  
|**Exklusive Bytes in %**|Der Prozentsatz aller während der Profilerstellung zugeordneten Bytes, die exklusive Bytes des Moduls, der Funktion, der Zeile oder der Anweisung waren.|  
|**Inklusive Bytes**|-   Bei einer Funktion die Gesamtzahl von Bytes, die von der Funktion zugeordnet wurden.  Diese Zahl umfasst auch Bytes, die in von der Funktion aufgerufenen Funktionen zugeordnet wurden.<br />-   Bei einem Modul die Anzahl von zugeordneten Bytes während einer Profilerstellung, die bei der Ausführung von mindestens einer Funktion des Moduls zugeordnet wurden.  Diese Zahl umfasst auch Objekte, die in allen von den Modulfunktionen aufgerufenen Funktionen erstellt wurden.|  
|**Inklusive Bytes in %**|Der Prozentsatz aller Bytes, die während der Profilerstellung zugeordnet wurden und inklusive Bytes dieses Moduls oder dieser Funktion waren.|  
  
## Werte für verstrichene inklusive Zeit  
 Werte für die verstrichene inklusive Zeit geben an, wie lange sich eine Funktion in der Aufrufliste befunden hat.  Die Zeit umfasst die aufgewendete Zeit für untergeordnete Funktionen und für Aufrufe des Betriebssystems, z. B. Kontextwechsel und Eingabe\-\/Ausgabeoperationen.  
  
|Spalte|**Beschreibung**|  
|------------|----------------------|  
|**Elapsed Inclusive Time**|-   Die in der Funktion für eine Funktion aufgewendete Zeit.  Diese umfasst die aufgewendete Zeit für untergeordnete Funktionen und für Aufrufe des Betriebssystems, z. B. Kontextwechsel und Eingabe\-\/Ausgabeoperationen.<br />-   Bei einem Modul der Zeitraum, in dem sich mindestens eine Funktion im Modul auf der Aufrufliste befunden hat.|  
|**Verstrichene inklusive Zeit in %**|Der Prozentsatz der gesamten verstrichenen inklusiven Zeit während der Profilerstellungsausführung, die sich auf die insgesamt verstrichene inklusive Zeit dieses Moduls oder dieser Funktion bezieht.|  
|**Durchschnittl. verstrichene inklusive Zeit**|-   Bei einer Funktion die durchschnittliche verstrichene inklusive Zeit für einen Aufruf dieser Funktion.<br />-   Bei einem Modul die durchschnittliche verstrichene inklusive Zeit für alle Aufrufe von Funktionen in diesem Modul.|  
|**Maximal verstrichene inklusive Zeit**|-   Bei einer Funktion die maximal verstrichene inklusive Zeit für einen Aufruf dieser Funktion.<br />-   Bei einem Modul die maximal verstrichene inklusive Zeit für alle Aufrufe von Funktionen in diesem Modul.|  
|**Mindestens verstrichene inklusive Zeit**|-   Bei einer Funktion die mindestens verstrichene inklusive Zeit für einen Aufruf dieses Moduls oder dieser Funktion.<br />-   Bei einem Modul die mindestens verstrichene inklusive Zeit für alle Aufrufe von Funktionen in diesem Modul.|  
  
## Werte für verstrichene exklusive Zeit  
 Werte für verstrichene exklusive Zeit geben die Zeit an, die eine Funktion direkt an erster Stelle in der Aufrufliste ausgeführt wurde.  Die Zeit umfasst die Zeit für Aufrufe des Betriebssystems, z. B. Kontextwechsel und Eingabe\-\/Ausgabeoperationen, jedoch nicht die Zeit für untergeordnete Funktionen.  
  
|Spalte|**Beschreibung**|  
|------------|----------------------|  
|**Elapsed Exclusive Time**|-   Die in einer Funktion für Aufrufe des Moduls oder der Funktion aufgewendete Zeit.  Umfasst Aufrufe des Betriebssystems, z. B. Kontextwechsel und Eingabe\-\/Ausgabeoperationen, nicht jedoch in untergeordneten Funktionen aufgewendete Zeit.<br />-   Bei einem Modul die Summe der verstrichenen exklusiven Zeit der Funktionen im Modul.|  
|**Verstrichene exklusive Zeit in %**|Der Prozentsatz der gesamten verstrichenen exklusiven Zeit während der Profilerstellungsausführung, die sich auf die insgesamt verstrichene exklusive Zeit dieses Moduls oder dieser Funktion bezieht.|  
|**Durchschnittl. verstrichene exklusive Zeit**|-   Bei einer Funktion die durchschnittliche verstrichene exklusive Zeit für einen Aufruf dieser Funktion.<br />-   Bei einem Modul die durchschnittliche verstrichene exklusive Zeit für alle Aufrufe von Funktionen in diesem Modul.|  
|**Maximal verstrichene exklusive Zeit**|-   Bei einer Funktion die maximal verstrichene exklusive Zeit für einen Aufruf dieser Funktion.<br />-   Bei einem Modul die maximal verstrichene exklusive Zeit für alle Aufrufe von Funktionen in diesem Modul.|  
|**Mindestens verstrichene exklusive Zeit**|-   Bei einer Funktion die mindestens verstrichene exklusive Zeit für einen Aufruf dieses Moduls oder dieser Funktion.<br />-   Bei einem Modul die mindestens verstrichene exklusive Zeit für alle Aufrufe von Funktionen in diesem Modul.|  
  
## Werte für inklusive Anwendungszeit  
 Werte für die inklusive Anwendungszeit geben die Zeit an, die sich eine Funktion in der Aufrufliste befunden hat.  Die Zeit umfasst die Zeit in untergeordneten Funktionen, jedoch nicht die Zeit für Aufrufe des Betriebssystems, z. B. Kontextwechsel und Eingabe\-\/Ausgabeoperationen.  
  
|Spalte|**Beschreibung**|  
|------------|----------------------|  
|**Application Inclusive Time**|-   Die in einer Funktion für Aufrufe der Funktion aufgewendete Zeit.  Umfasst in untergeordneten Funktionen aufgewendete Zeit, nicht jedoch Aufrufe des Betriebssystems, z. B. Kontextwechsel und Eingabe\-\/Ausgabeoperationen.<br />-   Bei einem Modul der Zeitraum, in dem sich mindestens eine Funktion des Moduls auf der Aufrufliste befunden hat, jedoch nicht die Zeit für Aufrufe des Betriebssystems.|  
|**Inklusive Anwendungszeit in %**|Der Prozentsatz der gesamten verstrichenen inklusiven Zeit während der Profilerstellungsausführung, die sich auf die inklusive Anwendungszeit dieses Moduls oder dieser Funktion bezieht.|  
|**Durchschnittl. inklusive Anwendungszeit**|-   Bei einer Funktion die durchschnittliche inklusive Anwendungszeit für einen Aufruf dieser Funktion.<br />-   Bei einem Modul die durchschnittliche inklusive Anwendungszeit für alle Aufrufe von Funktionen in diesem Modul.|  
|**Maximale inklusive Anwendungszeit**|-   Bei einer Funktion die maximale inklusive Anwendungszeit für einen Aufruf dieser Funktion.<br />-   Bei einem Modul die maximale inklusive Anwendungszeit für alle Aufrufe von Funktionen in diesem Modul.|  
|**Minimale inklusive Anwendungszeit**|-   Bei einer Funktion die minimale inklusive Anwendungszeit für einen Aufruf dieses Moduls oder dieser Funktion.<br />-   Bei einem Modul die minimale inklusive Anwendungszeit für alle Aufrufe von Funktionen in diesem Modul.|  
  
## Werte für exklusive Anwendungszeit  
 Anwendungsexklusive Werte geben die Gesamtzeit an, die im Modul oder in der Funktion verbracht wurde, ohne die Zeit, die in untergeordneten Funktionen verbracht wurde.  Die angegebene Zeit berücksichtigt außerdem keine Aufrufe des Betriebssystems, z. B. Kontextwechsel und Eingabe\-\/Ausgabeoperationen.  
  
|Spalte|**Beschreibung**|  
|------------|----------------------|  
|**Application Exclusive Time**|-   Bei einer Funktion die gesamte exklusive Anwendungszeit für Aufrufe dieser Funktion.<br />-   Bei einem Modul die gesamte exklusive Anwendungszeit für alle Aufrufe von Funktionen in diesem Modul.|  
|**Exklusive Anwendungszeit in %**|Der Prozentsatz der gesamten verstrichenen exklusiven Zeit während der Profilerstellungsausführung, die sich auf die exklusive Anwendungszeit dieses Moduls oder dieser Funktion bezieht.|  
|**Durchschnittl. exklusive Anwendungszeit**|-   Bei einer Funktion die durchschnittliche exklusive Anwendungszeit für einen Aufruf dieser Funktion.<br />-   Bei einem Modul die durchschnittliche exklusive Anwendungszeit für alle Aufrufe von Funktionen in diesem Modul.|  
|**Maximale exklusive Anwendungszeit**|-   Bei einer Funktion die maximale exklusive Anwendungszeit für einen Aufruf dieser Funktion.<br />-   Bei einem Modul die maximale exklusive Anwendungszeit für alle Aufrufe von Funktionen in diesem Modul.|  
|**Minimale exklusive Anwendungszeit**|-   Bei einer Funktion die minimale exklusive Anwendungszeit für einen Aufruf dieses Moduls oder dieser Funktion.<br />-   Bei einem Modul die minimale exklusive Anwendungszeit für alle Aufrufe von Funktionen in diesem Modul.|  
  
## Siehe auch  
 [Modulansicht \- Sampling](../profiling/modules-view-dotnet-memory-sampling-data.md)   
 [Modulansicht](../profiling/modules-view-instrumentation-data.md)   
 [Modulansicht](../profiling/modules-view-sampling-data.md)