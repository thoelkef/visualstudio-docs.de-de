---
title: "Aufrufer-/Aufgerufener-Ansicht - .NET-Speicherinstrumentationsdaten im Profiler | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Aufrufer-/Aufgerufener-Ansicht"
ms.assetid: da624c06-8741-4afb-aad1-f8c0002f3de2
caps.latest.revision: 12
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 12
---
# Aufrufer-/Aufgerufener-Ansicht - .NET-Speicherinstrumentationsdaten im Profiler
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Die Aufrufer\/Aufgerufener\-Ansicht für Profilerstellungsdaten zum .NET\-Speicher, die mit der Instrumentationsmethode gesammelt wurden, zeigt Belegungs\- und Zeitsteuerungsdaten für eine ausgewählte Funktion und die zugehörigen übergeordneten und untergeordneten Funktionen dieser ausgewählten Funktion an.  Die Aufrufer\-\/Aufgerufener\-Ansicht enthält drei Raster.  
  
 **Aktuelle Funktion** wird im mittleren Raster angezeigt und zeigt Speicherinformationen zur Profilerstellung für die ausgewählte Funktion an.  Die Werte umfassen alle Samplingaufrufe der Funktion.  
  
 **Funktionen, die die aktuelle Funktion aufgerufen haben** wird im obersten Raster angezeigt und zeigt die Menge der Werte der ausgewählten \(aktuellen\) Funktion an, die durch Aufrufe der \(übergeordneten\) Aufruferfunktion generiert wurden.  
  
 **Funktionen, die von der aktuellen Funktion aufgerufen wurden** wird im untersten Raster angezeigt und zeigt Speicherdaten zur Profilerstellung für die aufgerufenen \(untergeordneten\) Funktionen der ausgewählten Funktion an, wenn die untergeordnete Funktion von der aktuellen Funktion aufgerufen wurde.  
  
 Doppelklicken Sie auf eine Zeile einer Aufrufer\- oder Aufgerufener\-Funktion, um diese Zeile zur aktuellen Funktion zu machen.  
  
## Allgemein  
  
|Spalte|**Beschreibung**|  
|------------|----------------------|  
|**Function Name**|Der Name der Funktion.|  
|**Function Address**|Die Adresse der Funktion.|  
|**Funktionszeilennummer**|Die Zeilennummer des Anfangs dieser Funktion in der Quelldatei.|  
|**Number of Calls**|Die Gesamtzahl der Aufrufe der Funktion.|  
|**Quelldatei**|Die Quelldatei, die die Definition der Funktion enthält.|  
|**Modulname**|Der Name des Moduls, das die Funktion enthält.|  
|**Modulpfad**|Der Pfad des Moduls, das die Funktion enthält.|  
|**Prozess\-ID**|Die Prozess\-ID der Profilerstellungsausführung.|  
|**Prozessname**|Der Name, der dem Prozess zugewiesen wird.|  
|**Time Exclusive Probe Overhead**|Der durch Instrumentation verursachte zusätzliche Zeitaufwand für diese Funktion.  Der zusätzliche Testaufwand wurde bei allen exklusiven Zeiten subtrahiert.|  
|**Time Inclusive Probe Overhead**|Der von der Instrumentation verursachte zusätzliche Zeitaufwand für diese Funktion und ihre untergeordneten Funktionen.  Der zusätzliche Testaufwand wurde bei allen inklusiven Zeiten subtrahiert.|  
|**Typ**|Der Kontext der Funktion:<br /><br /> **0** – die aktuelle Funktion<br /><br /> **1** – eine Funktion, die die aktuelle Funktion aufruft<br /><br /> **2** – eine Funktion, die von der aktuellen Funktion aufgerufen wird<br /><br /> Nur in [VSPerfReport](../profiling/vsperfreport.md)\-Befehlszeilenberichten.|  
|**Name der Stammfunktion**|Der Name der aktuellen Funktion.  Nur in [VSPerfReport](../profiling/vsperfreport.md)\-Befehlszeilenberichten.|  
  
## Werte zur .NET\-Speicherbelegung  
  
|Spalte|**Beschreibung**|  
|------------|----------------------|  
|**Exclusive Allocations**|-   Bei der aktuellen Funktion die Anzahl der Objekte, die während der Ausführung von Code im Funktionsrumpf \(d. h., während sich die Funktion auf der obersten Ebene der Aufrufliste befand\) erstellt wurden.  Die Zahl umfasst keine Objekte, die in den von dieser Funktion aufgerufenen Funktionen erstellt wurden.<br />-   Bei einer aufrufenden Funktion die Anzahl von exklusiven Zuordnungen der aktuellen Funktion, die von Aufrufen von dieser aufrufenden Funktion generiert wurden.<br />-   Bei einer aufgerufenen Funktion die Anzahl von Objekten, die von den Instanzen dieser Funktion erstellt wurden, die von dieser Funktion aufgerufen wurden.  Diese Zahl umfasst keine Objekte, die in den von der aufgerufenen Funktion aufgerufenen Funktionen erstellt wurden.|  
|**Exklusive Zuordnungen in %**|Der Prozentsatz aller Objekte, die während der Profilerstellung erstellt wurden und exklusive Belegungen dieser Funktion waren.|  
|**Inclusive Allocations**|-   Bei der aktuellen Funktion die Anzahl der Objekte, die während der Profilerstellung von der Funktion zugeordnet wurden.  Die Zahl umfasst auch Objekte, die in den von der Funktion aufgerufenen Funktionen erstellt wurden.<br />-   Bei einer aufrufenden Funktion die Anzahl von inklusiven Zuordnungen der aktuellen Funktion, die von Aufrufen von dieser aufrufenden Funktion generiert wurden.<br />-   Bei einer aufgerufenen Funktion die Anzahl von Objekten, die von den durch Aufrufe aus der aktuellen Funktion generierten Instanzen dieser Funktion belegt wurden.  Diese Zahl umfasst Zuordnungen von Funktionen, die von dieser aufgerufenen Funktion aufgerufen wurden.|  
|**Inklusive Zuordnungen in %**|Der Prozentsatz aller Objekte, die während der Profilerstellung erstellt wurden und inklusive Belegungen dieser Funktion waren.|  
|**Exklusive Bytes**|-   Bei der aktuellen Funktion die Anzahl der Bytes im Arbeitsspeicher, die während der Profilerstellung von der Funktion belegt wurden.  Diese Zahl umfasst nicht den Speicher, der in den von der Funktion aufgerufenen Funktionen belegt wurde.<br />-   Bei einer aufrufenden Funktion die Anzahl von exklusiven Bytes der aktuellen Funktion, die von Aufrufen von dieser aufrufenden Funktion generiert wurden.<br />-   Bei einer aufgerufenen Funktion die Anzahl von Bytes, die von den durch Aufrufe aus der aktuellen Funktion generierten Instanzen dieser Funktion belegt wurden.  Diese Zahl umfasst nicht die Bytes, die in den von der Funktion aufgerufenen Funktionen zugeordnet wurden.|  
|**Exklusive Bytes in %**|Der Prozentsatz aller Bytes des Arbeitsspeichers, die während der Profilerstellung belegt wurden und exklusive Belegungen dieser Funktion waren.|  
|**Inklusive Bytes**|-   Bei der aktuellen Funktion die Anzahl der Bytes im Arbeitsspeicher, die während der Profilerstellung von der Funktion belegt wurden.  Diese Zahl umfasst nicht den Speicher, der in den von der Funktion aufgerufenen Funktionen belegt wurde.<br />-   Bei einer aufrufenden Funktion die Anzahl von inklusiven Bytes der Instanzen der aktuellen Funktion, die von Aufrufen von dieser aufrufenden Funktion generiert wurden.<br />-   Bei einer aufgerufenen Funktion die Anzahl von Bytes, die von den durch Aufrufe aus der aktuellen Funktion generierten Instanzen dieser Funktion belegt wurden.  Die Zahl umfasst auch Bytes, die in von dieser aufgerufenen Funktion aufgerufenen Funktionen zugeordnet wurden.|  
|**Inklusive Bytes in %**|Der Prozentsatz aller Bytes des Arbeitsspeichers, die während der Profilerstellung belegt wurden und inklusive Belegungen dieser Funktion waren.|  
  
## Werte für verstrichene inklusive Zeit  
 Werte für die verstrichene inklusive Zeit geben an, wie lange sich eine Funktion in der Aufrufliste befunden hat.  Die Zeit umfasst die aufgewendete Zeit für untergeordnete Funktionen und für Aufrufe des Betriebssystems, z. B. Kontextwechsel und Eingabe\-\/Ausgabeoperationen.  
  
|Spalte|**Beschreibung**|  
|------------|----------------------|  
|**Elapsed Inclusive Time**|-   Die in der Funktion für die aktuelle Funktion aufgewendete Zeit.  Der Wert umfasst die Zeit in untergeordneten Funktionen und für Aufrufe des Betriebssystems, z. B. Kontextwechsel und Eingabe\-\/Ausgabeoperationen.<br />-   Bei einer aufrufenden Funktion die Menge an verstrichener inklusiver Zeit für die aktuelle Funktion, die von Aufrufen von dieser aufrufenden Funktion generiert wurde.<br />-   Bei einer aufrufenden Funktion die Zeit in dieser Funktion, die auf Aufrufe aus der aktuellen Funktion entfällt.  Der Wert umfasst die Zeit in untergeordneten Funktionen und für Aufrufe des Betriebssystems, z. B. Kontextwechsel und Eingabe\-\/Ausgabeoperationen.|  
|**Verstrichene inklusive Zeit in %**|Der Prozentsatz der gesamten verstrichenen inklusiven Zeit, die innerhalb der verstrichenen inklusiven Zeit dieser Funktion in diesem Kontext auf die Profilerstellung entfällt.|  
|**Durchschnittl. verstrichene inklusive Zeit**|Die durchschnittliche verstrichene inklusive Zeit eines Aufrufs dieser Funktion in diesem Kontext.|  
|**Maximal verstrichene inklusive Zeit**|Die maximal verstrichene inklusive Zeit eines Aufrufs dieser Funktion in diesem Kontext.|  
|**Mindestens verstrichene inklusive Zeit**|Die mindestens verstrichene inklusive Zeit eines Aufrufs dieser Funktion in diesem Kontext.|  
  
## Werte für verstrichene exklusive Zeit  
 Werte für verstrichene exklusive Zeit geben die Zeit an, die eine Funktion direkt an erster Stelle in der Aufrufliste ausgeführt wurde.  Die Zeit umfasst die Zeit für Aufrufe des Betriebssystems, z. B. Kontextwechsel und Eingabe\-\/Ausgabeoperationen, jedoch nicht die Zeit für untergeordnete Funktionen.  
  
|Spalte|**Beschreibung**|  
|------------|----------------------|  
|**Elapsed Exclusive Time**|-   Bei der aktuellen Funktion die Zeit, die für die direkte Ausführung im Funktionsrumpf aufgewendet wurde.  Der Wert umfasst nicht die Zeit in untergeordneten Funktionen, Aufrufe des Betriebssystems, z. B. Kontextwechsel und Eingabe\-\/Ausgabeoperationen, sind jedoch enthalten.<br />-   Bei einer aufrufenden Funktion die Menge an verstrichener exklusiver Zeit für die aktuelle Funktion, die von Aufrufen von dieser aufrufenden Funktion generiert wurde.<br />-   Bei einer aufrufenden Funktion die Zeit in dieser Funktion, die auf Aufrufe aus der aktuellen Funktion entfällt.  Der Wert umfasst die Zeit für Aufrufe des Betriebssystems, z. B. Kontextwechsel und Eingabe\-\/Ausgabeoperationen, jedoch nicht die Zeit in untergeordneten Funktionen der aufgerufenen Funktion.|  
|**Verstrichene exklusive Zeit in %**|Der Prozentsatz der gesamten verstrichenen exklusiven Zeit, die innerhalb der verstrichenen exklusiven Zeit dieser Funktion in diesem Kontext auf die Profilerstellung entfällt.|  
|**Durchschnittl. verstrichene exklusive Zeit**|Die durchschnittlich verstrichene exklusive Zeit eines Aufrufs dieser Funktion in diesem Kontext.|  
|**Maximal verstrichene exklusive Zeit**|Die maximal verstrichene exklusive Zeit eines Aufrufs dieser Funktion in diesem Kontext.|  
|**Mindestens verstrichene exklusive Zeit**|Die mindestens verstrichene exklusive Zeit eines Aufrufs dieser Funktion in diesem Kontext.|  
  
## Werte für inklusive Anwendungszeit  
 Werte für die inklusive Anwendungszeit geben die Zeit an, die sich eine Funktion in der Aufrufliste befunden hat.  Die Zeit umfasst die Zeit in untergeordneten Funktionen, jedoch nicht die Zeit für Aufrufe des Betriebssystems, z. B. Kontextwechsel und Eingabe\-\/Ausgabeoperationen.  
  
|Spalte|**Beschreibung**|  
|------------|----------------------|  
|**Application Inclusive Time**|-   Bei der aktuellen Funktion die Zeit, die für die Funktion und die zugehörigen untergeordneten Funktionen aufgewendet wurde.  Der Wert umfasst nicht die Zeit für Aufrufe des Betriebssystems, z. B. Kontextwechsel und Eingabe\-\/Ausgabeoperationen.<br />-   Bei einer aufrufenden Funktion die Menge an inklusiver Anwendungszeit für die aktuelle Funktion, die von Aufrufen von dieser aufrufenden Funktion generiert wurde.<br />-   Bei einer aufgerufenen Funktion die Zeit in dieser Funktion und den zugehörigen untergeordneten Funktionen, die durch Aufrufe aus der aktuellen Funktion generiert wurden.  Der Wert umfasst nicht die Zeit für Aufrufe des Betriebssystems, z. B. Kontextwechsel und Eingabe\-\/Ausgabeoperationen.|  
|**Inklusive Anwendungszeit in %**|Der Prozentsatz der insgesamt verstrichenen inklusiven Zeit, die innerhalb der verstrichenen inklusiven Zeit dieser Funktion in diesem Kontext auf die Profilerstellung entfällt.|  
|**Durchschnittl. inklusive Anwendungszeit**|Die durchschnittliche inklusive Anwendungszeit eines Aufrufs dieser Funktion in diesem Kontext.|  
|**Maximale inklusive Anwendungszeit**|Die maximale inklusive Anwendungszeit eines Aufrufs dieser Funktion in diesem Kontext.|  
|**Minimale inklusive Anwendungszeit**|Die minimale inklusive Anwendungszeit eines Aufrufs dieser Funktion in diesem Kontext.|  
  
## Werte für exklusive Anwendungszeit  
 Anwendungsexklusive Werte geben die Gesamtzeit an, die in der Funktion verbracht wurde, ohne die Zeit, die in untergeordneten Funktionen verbracht wurde.  Die angegebene Zeit berücksichtigt außerdem keine Zeit für Aufrufe des Betriebssystems, z. B. Kontextwechsel und Eingabe\-\/Ausgabeoperationen.  
  
|Spalte|**Beschreibung**|  
|------------|----------------------|  
|**Application Exclusive Time**|-   Bei der aktuellen Funktion die Zeit, die für die direkte Ausführung im Funktionsrumpf aufgewendet wurde.  Der Wert umfasst weder die Zeit in untergeordneten Funktionen noch die Aufrufe des Betriebssystems, z. B. Kontextwechsel und Eingabe\-\/Ausgabeoperationen.<br />-   Bei einer aufrufenden Funktion die Menge an exklusiver Anwendungszeit für die aktuelle Funktion, die von Aufrufen aus dieser aufrufenden Funktion generiert wurde.<br />-   Bei einer aufrufenden Funktion die Zeit in dieser Funktion, die auf Aufrufe aus der aktuellen Funktion entfällt.  Der Wert umfasst weder die Zeit in untergeordneten Funktionen der aufgerufenen Funktion noch die Zeit für Aufrufe des Betriebssystems, z. B. Kontextwechsel und Eingabe\-\/Ausgabeoperationen.|  
|**Exklusive Anwendungszeit in %**|Der Prozentsatz der gesamten verstrichenen exklusiven Zeit, die innerhalb der exklusiven Gesamtanwendungszeit dieser Funktion in diesem Kontext auf die Profilerstellung entfällt.|  
|**Durchschnittl. exklusive Anwendungszeit**|Die durchschnittliche exklusive Anwendungszeit eines Aufrufs dieser Funktion in diesem Kontext.|  
|**Maximale exklusive Anwendungszeit**|Die maximale exklusive Anwendungszeit eines Aufrufs dieser Funktion in diesem Kontext.|  
|**Minimale exklusive Anwendungszeit**|Die minimale exklusive Anwendungszeit eines Aufrufs dieser Funktion in diesem Kontext.|  
  
## Siehe auch  
 [Gewusst wie: Anpassen von Spalten in Berichtsansichten](../profiling/how-to-customize-report-view-columns.md)   
 [Aufrufer\-\/Aufgerufener\-Ansicht \- Sampling](../profiling/caller-callee-view-dotnet-memory-sampling-data.md)   
 [Aufrufer\-\/Aufgerufener\-Ansicht](../profiling/caller-callee-view-instrumentation-data.md)   
 [Aufrufer\-\/Aufgerufener\-Ansicht](../profiling/caller-callee-view-sampling-data.md)