---
title: "Aufrufer-/Aufgerufener-Ansicht – Profiler-Instrumentationsdaten | Microsoft Docs"
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
  - "Aufrufer-/Aufgerufener-Ansicht"
ms.assetid: 0908d354-aa5c-4518-8631-e25b8e7649e5
caps.latest.revision: 13
caps.handback.revision: 13
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# Aufrufer-/Aufgerufener-Ansicht – Profiler-Instrumentationsdaten
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

In der Aufrufer\-\/Aufgerufener\-Ansicht werden Profilerstellungsinformationen zu einer ausgewählten Funktion und den übergeordneten und untergeordneten Funktionen in der Aufrufstruktur angezeigt.  Die Aufrufer\-\/Aufgerufener\-Ansicht enthält drei Raster.  
  
 **Aktuelle Funktion** wird im mittleren Raster angezeigt und zeigt Profilerstellungsinformationen zur ausgewählten Funktion an.  Die Werte enthalten alle Aufrufe der Funktion.  
  
 **Funktionen, die die aktuelle Funktion aufgerufen haben** befindet sich im obersten Raster und zeigt Profilerstellungsinformationen zu den aufrufenden \(übergeordneten\) Funktionen der ausgewählten Funktion an.  Die Werte geben die Menge der Werte der aktuellen Funktion an, die durch Aufrufe von dieser aufrufenden Funktion generiert wurde.  
  
 **Funktionen, die von der aktuellen Funktion aufgerufen wurden** wird im untersten Raster angezeigt und zeigt Profilerstellungsinformationen zu Instanzen der aufgerufenen \(untergeordneten\) Funktionen der ausgewählten Funktion an.  Die Werte geben nur die Zeit an, die in der untergeordneten Funktion aufgewendet wurde, wenn diese von der aktuellen Funktion aufgerufen wurde.  
  
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
|**Time Exclusive Probe Overhead**|Der von der Instrumentation verursachte zusätzliche Zeitaufwand für diese Funktion.  Der zusätzliche Testaufwand wurde bei allen exklusiven Zeiten subtrahiert.|  
|**Time Inclusive Probe Overhead**|Der von der Instrumentation verursachte zusätzliche Zeitaufwand für diese Funktion und ihre untergeordneten Funktionen.  Der zusätzliche Testaufwand wurde bei allen inklusiven Zeiten subtrahiert.|  
|**Typ**|Der Kontext der Funktion:<br /><br /> **0** – die aktuelle Funktion<br /><br /> **1** – eine Funktion, die die aktuelle Funktion aufruft<br /><br /> **2** – eine Funktion, die von der aktuellen Funktion aufgerufen wird<br /><br /> Nur in [VSPerfReport](../profiling/vsperfreport.md)\-Befehlszeilenberichten.|  
|**Name der Stammfunktion**|Der Name der aktuellen Funktion.  Nur in [VSPerfReport](../profiling/vsperfreport.md)\-Befehlszeilenberichten.|  
  
## Werte für verstrichene inklusive Zeit  
 Werte für die verstrichene inklusive Zeit geben an, wie lange sich eine Funktion in der Aufrufliste befunden hat.  Die Zeit umfasst die Zeit in untergeordneten Funktionen und die Zeit für Aufrufe des Betriebssystems, z. B. Kontextwechsel und Eingabe\-\/Ausgabevorgänge.  
  
|Spalte|**Beschreibung**|  
|------------|----------------------|  
|**Elapsed Inclusive Time**|-   Die in der Funktion für die aktuelle Funktion aufgewendete Zeit.  Der Wert umfasst die Zeit in untergeordneten Funktionen und für Aufrufe des Betriebssystems, z. B. Kontextwechsel und Eingabe\-\/Ausgabeoperationen.<br />-   Bei einer aufrufenden Funktion die Menge an verstrichener inklusiver Zeit für die aktuelle Funktion, die von Aufrufen von dieser aufrufenden Funktion generiert wurde.<br />-   Bei einer aufgerufenen Funktion die Zeit für die Instanzen der Funktion, die durch Aufrufe aus der aktuellen Funktion generiert wurden.  Der Wert umfasst die Zeit in untergeordneten Funktionen der aufgerufenen Funktion und die Zeit für Aufrufe des Betriebssystems, z. B. Kontextwechsel und Eingabe\-\/Ausgabevorgänge.|  
|**Verstrichene inklusive Zeit in %**|Der Prozentsatz der gesamten verstrichenen inklusiven Zeit, die innerhalb der verstrichenen inklusiven Zeit dieser Funktion in diesem Kontext auf die Profilerstellung entfällt.|  
|**Durchschnittl. verstrichene inklusive Zeit**|Die durchschnittliche verstrichene inklusive Zeit eines Aufrufs dieser Funktion in diesem Kontext.|  
|**Maximal verstrichene inklusive Zeit**|Die maximal verstrichene inklusive Zeit eines Aufrufs dieser Funktion in diesem Kontext.|  
|**Mindestens verstrichene inklusive Zeit**|Die mindestens verstrichene inklusive Zeit eines Aufrufs dieser Funktion in diesem Kontext.|  
  
## Werte für verstrichene exklusive Zeit  
 Werte für verstrichene exklusive Zeit geben die Zeit an, die eine Funktion direkt an erster Stelle in der Aufrufliste ausgeführt wurde.  Die Zeit umfasst die Zeit für Aufrufe des Betriebssystems, z. B. Kontextwechsel und Eingabe\-\/Ausgabevorgänge, jedoch nicht die Zeit in untergeordneten Funktionen.  
  
|Spalte|**Beschreibung**|  
|------------|----------------------|  
|**Elapsed Exclusive Time**|-   Bei der aktuellen Funktion die Zeit, die für die direkte Ausführung der Funktion aufgewendet wurde.  Der Wert umfasst die Zeit in untergeordneten Funktionen und für Aufrufe des Betriebssystems, z. B. Kontextwechsel und Eingabe\-\/Ausgabeoperationen.<br />-   Bei einer aufrufenden Funktion die Menge an verstrichener exklusiver Zeit für die aktuelle Funktion, die von Aufrufen von dieser aufrufenden Funktion generiert wurde.<br />-   Bei einer aufgerufenen Funktion die Zeit für die Instanzen der Funktion, die durch Aufrufe aus der aktuellen Funktion generiert wurden.  Der Wert umfasst die Zeit für Aufrufe des Betriebssystems, z. B. Kontextwechsel und Eingabe\-\/Ausgabevorgänge, jedoch nicht die Zeit in untergeordneten Funktionen der aufgerufenen Funktion.|  
|**Verstrichene exklusive Zeit in %**|Der Prozentsatz der gesamten verstrichenen exklusiven Zeit, die innerhalb der verstrichenen exklusiven Zeit dieser Funktion in diesem Kontext auf die Profilerstellung entfällt.|  
|**Durchschnittl. verstrichene exklusive Zeit**|Die durchschnittlich verstrichene exklusive Zeit eines Aufrufs dieser Funktion in diesem Kontext.|  
|**Maximal verstrichene exklusive Zeit**|Die maximal verstrichene exklusive Zeit eines Aufrufs dieser Funktion in diesem Kontext.|  
|**Mindestens verstrichene exklusive Zeit**|Die mindestens verstrichene exklusive Zeit eines Aufrufs dieser Funktion in diesem Kontext.|  
  
## Werte für inklusive Anwendungszeit  
 Werte für die inklusive Anwendungszeit geben die Zeit an, die sich eine Funktion in der Aufrufliste befunden hat.  Die Zeit umfasst die Zeit in untergeordneten Funktionen, jedoch nicht die Zeit für Aufrufe des Betriebssystems, z. B. Kontextwechsel und Eingabe\-\/Ausgabeoperationen.  
  
|Spalte|**Beschreibung**|  
|------------|----------------------|  
|**Application Inclusive Time**|-   Bei der aktuellen Funktion die Zeit, die für die Funktion und die zugehörigen untergeordneten Funktionen aufgewendet wurde.  Der Wert umfasst nicht die Zeit für Aufrufe des Betriebssystems, z. B. Kontextwechsel und Eingabe\-\/Ausgabeoperationen.<br />-   Bei einer aufrufenden Funktion die Menge an inklusiver Anwendungszeit für die aktuelle Funktion, die von Aufrufen von dieser aufrufenden Funktion generiert wurde.<br />-   Bei einer aufgerufenen Funktion die Zeit für die Instanzen der Funktion, die durch Aufrufe aus der aktuellen Funktion generiert wurden.  Der Wert umfasst die Zeit in untergeordneten Funktionen der aufgerufenen Funktion, jedoch nicht die Zeit für Aufrufe des Betriebssystems, z. B. Kontextwechsel und Eingabe\-\/Ausgabevorgänge.|  
|**Inklusive Anwendungszeit in %**|Der Prozentsatz der insgesamt verstrichenen inklusiven Zeit, die innerhalb der verstrichenen inklusiven Zeit dieser Funktion in diesem Kontext auf die Profilerstellung entfällt.|  
|**Durchschnittl. inklusive Anwendungszeit**|Die durchschnittliche inklusive Anwendungszeit eines Aufrufs dieser Funktion in diesem Kontext.|  
|**Maximale inklusive Anwendungszeit**|Die maximale inklusive Anwendungszeit eines Aufrufs dieser Funktion in diesem Kontext.|  
|**Minimale inklusive Anwendungszeit**|Die minimale inklusive Anwendungszeit eines Aufrufs dieser Funktion in diesem Kontext.|  
  
## Werte für exklusive Anwendungszeit  
 Anwendungsexklusive Werte geben die Zeit an, die in der Funktion verbracht wurde.  Die Zeit umfasst nicht die Zeit in untergeordneten Funktionen und auch nicht die Zeit für Aufrufe des Betriebssystems, z. B. Kontextwechsel und Eingabe\-\/Ausgabevorgänge.  
  
|Spalte|**Beschreibung**|  
|------------|----------------------|  
|**Application Exclusive Time**|-   Bei der aktuellen Funktion die Zeit, die für die direkte Ausführung der Funktion aufgewendet wurde.  Der Wert umfasst weder die Zeit in untergeordneten Funktionen noch die Aufrufe des Betriebssystems, z. B. Kontextwechsel und Eingabe\-\/Ausgabeoperationen.<br />-   Bei einer aufrufenden Funktion die Menge an exklusiver Anwendungszeit für die aktuelle Funktion, die von Aufrufen aus dieser aufrufenden Funktion generiert wurde.<br />-   Bei einer aufgerufenen Funktion die Zeit für die Instanzen der Funktion, die durch Aufrufe aus der aktuellen Funktion generiert wurden.  Der Wert umfasst weder die Zeit in untergeordneten Funktionen der aufgerufenen Funktion noch die Zeit für Aufrufe des Betriebssystems, z. B. Kontextwechsel und Eingabe\-\/Ausgabeoperationen.|  
|**Exklusive Anwendungszeit in %**|Der Prozentsatz der gesamten verstrichenen exklusiven Zeit, die innerhalb der exklusiven Gesamtanwendungszeit dieser Funktion in diesem Kontext auf die Profilerstellung entfällt.|  
|**Durchschnittl. exklusive Anwendungszeit**|Die durchschnittliche exklusive Anwendungszeit eines Aufrufs dieser Funktion in diesem Kontext.|  
|**Maximale exklusive Anwendungszeit**|Die maximale exklusive Anwendungszeit eines Aufrufs dieser Funktion in diesem Kontext.|  
|**Minimale exklusive Anwendungszeit**|Die minimale exklusive Anwendungszeit eines Aufrufs dieser Funktion in diesem Kontext.|  
  
## Siehe auch  
 [Gewusst wie: Anpassen von Spalten in Berichtsansichten](../profiling/how-to-customize-report-view-columns.md)   
 [Aufrufer\-\/Aufgerufener\-Ansicht](../profiling/caller-callee-view-sampling-data.md)   
 [Aufrufer\-\/Aufgerufener\-Ansicht \- Sampling](../profiling/caller-callee-view-dotnet-memory-sampling-data.md)   
 [Aufrufer\-\/Aufgerufener\-Ansicht \- Instrumentation](../profiling/caller-callee-view-net-memory-instrumentation-data.md)