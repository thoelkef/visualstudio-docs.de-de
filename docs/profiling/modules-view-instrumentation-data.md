---
title: "Modulansicht - Profiler-Instrumentationsdaten | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Modulansicht"
ms.assetid: 895b9589-1987-4160-916f-53b898a69cf0
caps.latest.revision: 10
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 10
---
# Modulansicht - Profiler-Instrumentationsdaten
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

In der Modulansicht werden die Leistungsdaten nach den in den Profilerstellungsdaten enthaltenen Modulen gruppiert angezeigt.  Die Funktionen des Moduls werden unter dem Modulknoten aufgeführt.  
  
## Allgemein  
 Die allgemeinen Spalten bezeichnen die Funktion in einer Ansichtszeile.  
  
|Spalte|**Beschreibung**|  
|------------|----------------------|  
|**Name**|Der Name der Funktion oder des Moduls.|  
|**Funktionszeilennummer**|Die Zeilennummer des Anfangs dieser Funktion in der Quelldatei.|  
|**Number of Calls**|Die Gesamtzahl von Aufrufen dieser Funktion oder dieses Moduls.|  
|**Quelldatei**|Die Quelldatei, die die Definition der Funktion enthält.|  
|**Modulname**|Der Name des Moduls, das die Funktion enthält.|  
|**Modulpfad**|Der Pfad des Moduls, das die Funktion enthält.|  
|**Prozess\-ID**|Die Prozess\-ID \(PID\) der Profilerstellung.|  
|**Prozessname**|Der Name des Prozesses, in dem das Modul oder die Funktion ausgeführt wurde.|  
|**Time Exclusive Probe Overhead**|Der zusätzliche Zeitaufwand für die Funktion oder das Modul aufgrund der Instrumentation.|  
|**Time Inclusive Probe Overhead**|Der zusätzliche Zeitaufwand für die Funktion oder das Modul und die zugehörigen untergeordneten Funktionen aufgrund der Instrumentation.|  
  
## Werte für verstrichene inklusive Zeit  
 Werte für die verstrichene inklusive Zeit geben an, wie lange sich eine Funktion in der Aufrufliste befunden hat.  Die Zeit umfasst die aufgewendete Zeit für untergeordnete Funktionen und für Aufrufe des Betriebssystems, z. B. Kontextwechsel und Eingabe\-\/Ausgabeoperationen.  
  
|Spalte|**Beschreibung**|  
|------------|----------------------|  
|**Elapsed Inclusive Time**|-   Die in der Funktion für eine Funktion aufgewendete Zeit.  Diese umfasst die aufgewendete Zeit für untergeordnete Funktionen und für Aufrufe des Betriebssystems, z. B. Kontextwechsel und Eingabe\-\/Ausgabeoperationen.<br />-   Bei einem Modul die Zeit, in der sich mindestens eine Funktion im Modul auf der Aufrufliste befunden hat.|  
|**Verstrichene inklusive Zeit in %**|Der Prozentsatz der gesamten verstrichenen inklusiven Zeit während der Profilerstellungsausführung, die sich auf die insgesamt verstrichene inklusive Zeit dieses Moduls oder dieser Funktion bezieht.|  
|**Durchschnittl. verstrichene inklusive Zeit**|-   Bei einer Funktion die durchschnittliche verstrichene inklusive Zeit für einen Aufruf dieser Funktion.<br />-   Bei einem Modul die durchschnittliche verstrichene inklusive Zeit für alle Aufrufe von Funktionen in diesem Modul.|  
|**Maximal verstrichene inklusive Zeit**|-   Bei einer Funktion die maximal verstrichene inklusive Zeit für einen Aufruf dieser Funktion.<br />-   Bei einem Modul die maximal verstrichene inklusive Zeit für alle Aufrufe von Funktionen in diesem Modul.|  
|**Mindestens verstrichene inklusive Zeit**|-   Bei einer Funktion die mindestens verstrichene inklusive Zeit für einen Aufruf dieses Moduls oder dieser Funktion.<br />-   Bei einem Modul die mindestens verstrichene inklusive Zeit für alle Aufrufe von Funktionen in diesem Modul.|  
  
## Werte für verstrichene exklusive Zeit  
 Werte für verstrichene exklusive Zeit geben die Zeit an, die eine Funktion direkt an erster Stelle in der Aufrufliste ausgeführt wurde.  Die Zeit umfasst die Zeit für Aufrufe des Betriebssystems, z. B. Kontextwechsel und Eingabe\-\/Ausgabevorgänge, jedoch nicht die Zeit in untergeordneten Funktionen.  
  
|Spalte|**Beschreibung**|  
|------------|----------------------|  
|**Elapsed Exclusive Time**|-   Die in einer Funktion für Aufrufe des Moduls oder der Funktion aufgewendete Zeit.  Umfasst Aufrufe des Betriebssystems, z. B. Kontextwechsel und Eingabe\-\/Ausgabeoperationen, nicht jedoch in untergeordneten Funktionen aufgewendete Zeit.<br />-   Bei einem Modul die Summe der verstrichenen exklusiven Zeit der Funktionen im Modul.|  
|**Verstrichene exklusive Zeit in %**|Der Prozentsatz der gesamten verstrichenen exklusiven Zeit während der Profilerstellungsausführung, die sich auf die insgesamt verstrichene exklusive Zeit dieses Moduls oder dieser Funktion bezieht.|  
|**Durchschnittl. verstrichene exklusive Zeit**|-   Bei einer Funktion die durchschnittliche verstrichene exklusive Zeit für einen Aufruf dieser Funktion.<br />-   Bei einem Modul die durchschnittliche verstrichene exklusive Zeit für alle Aufrufe von Funktionen in diesem Modul.|  
|**Maximal verstrichene exklusive Zeit**|-   Bei einer Funktion die maximal verstrichene exklusive Zeit für einen Aufruf dieser Funktion.<br />-   Bei einem Modul die maximal verstrichene exklusive Zeit für alle Aufrufe von Funktionen in diesem Modul.|  
|**Mindestens verstrichene exklusive Zeit**|-   Bei einer Funktion die mindestens verstrichene exklusive Zeit für einen Aufruf dieses Moduls oder dieser Funktion.<br />-   Bei einem Modul die mindestens verstrichene exklusive Zeit für alle Aufrufe von Funktionen in diesem Modul.|  
  
## Werte für inklusive Anwendungszeit  
 Werte für die inklusive Anwendungszeit geben die Zeit an, die sich eine Funktion in der Aufrufliste befunden hat.  Die Zeit umfasst nicht die Zeit für Aufrufe des Betriebssystems, z. B. Kontextwechsel und Eingabe\-\/Ausgabeoperationen, jedoch die Zeit für untergeordnete Funktionen.  
  
|Spalte|**Beschreibung**|  
|------------|----------------------|  
|**Application Inclusive Time**|-   Die in einer Funktion für Aufrufe der Funktion aufgewendete Zeit.  Umfasst in untergeordneten Funktionen aufgewendete Zeit, nicht jedoch Aufrufe des Betriebssystems, z. B. Kontextwechsel und Eingabe\-\/Ausgabeoperationen.<br />-   Bei einem Modul die Zeit, in der sich mindestens eine Funktion im Modul auf der Aufrufliste befunden hat.  Berücksichtigt keine Zeit, die in Aufrufen des Betriebssystems aufgewendet wurde.|  
|**Inklusive Anwendungszeit in %**|Der Prozentsatz der gesamten verstrichenen inklusiven Zeit während der Profilerstellungsausführung, die sich auf die inklusive Anwendungszeit dieses Moduls oder dieser Funktion bezieht.|  
|**Durchschnittl. inklusive Anwendungszeit**|-   Bei einer Funktion die durchschnittliche inklusive Anwendungszeit für einen Aufruf dieser Funktion.<br />-   Bei einem Modul die durchschnittliche inklusive Anwendungszeit für alle Aufrufe von Funktionen in diesem Modul.|  
|**Maximale inklusive Anwendungszeit**|-   Bei einer Funktion die maximale inklusive Anwendungszeit für einen Aufruf dieser Funktion.<br />-   Bei einem Modul die maximale inklusive Anwendungszeit für alle Aufrufe von Funktionen in diesem Modul.|  
|**Minimale inklusive Anwendungszeit**|-   Bei einer Funktion die minimale inklusive Anwendungszeit für einen Aufruf dieses Moduls oder dieser Funktion.<br />-   Bei einem Modul die minimale inklusive Anwendungszeit für alle Aufrufe von Funktionen in diesem Modul.|  
  
## Werte für exklusive Anwendungszeit  
 Anwendungsexklusive Werte geben die Zeit an, die im Modul oder in der Funktion verbracht wurde.  Die Zeit umfasst nicht die Zeit in untergeordneten Funktionen und auch nicht die Zeit für Aufrufe des Betriebssystems, z. B. Kontextwechsel und Eingabe\-\/Ausgabevorgänge.  
  
|Spalte|**Beschreibung**|  
|------------|----------------------|  
|**Application Exclusive Time**|Die gesamte exklusive Anwendungszeit aller Aufrufe dieses Moduls oder dieser Funktion.|  
|**Exklusive Anwendungszeit in %**|Der Prozentsatz der gesamten verstrichenen exklusiven Zeit während der Profilerstellungsausführung, die sich auf die exklusive Anwendungszeit dieses Moduls oder dieser Funktion bezieht.|  
|**Durchschnittl. exklusive Anwendungszeit**|-   Bei einer Funktion die durchschnittliche exklusive Anwendungszeit für einen Aufruf dieser Funktion.<br />-   Bei einem Modul die durchschnittliche exklusive Anwendungszeit für alle Aufrufe von Funktionen in diesem Modul.|  
|**Maximale exklusive Anwendungszeit**|-   Bei einer Funktion die maximale exklusive Anwendungszeit für einen Aufruf dieser Funktion.<br />-   Bei einem Modul die maximale exklusive Anwendungszeit für alle Aufrufe von Funktionen in diesem Modul.|  
|**Minimale exklusive Anwendungszeit**|-   Bei einer Funktion die minimale exklusive Anwendungszeit für einen Aufruf dieses Moduls oder dieser Funktion.<br />-   Bei einem Modul die minimale exklusive Anwendungszeit für alle Aufrufe von Funktionen in diesem Modul.|  
  
## Siehe auch  
 [Modulansicht](../profiling/modules-view-sampling-data.md)   
 [Modulansicht \- Instrumentation](../profiling/modules-view-dotnet-memory-instrumentation-data.md)   
 [Modulansicht \- Sampling](../profiling/modules-view-dotnet-memory-sampling-data.md)