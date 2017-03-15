---
title: "Modulansicht - .NET-Speichersamplingdaten im Profiler | Microsoft Docs"
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
ms.assetid: 9c05b51a-8382-44cf-a8f7-3fabdd2e8f1b
caps.latest.revision: 12
caps.handback.revision: 12
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# Modulansicht - .NET-Speichersamplingdaten im Profiler
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

In der Modulansicht der .NET\-Speicherbelegungsdaten, die mit der Samplingmethode gesammelt wurden, werden die Arbeitsspeicherdaten nach den Modulen gruppiert, die bei der Profilerstellungsausführung ausgeführt wurden.  Jedes Modul ist der Stamm einer hierarchischen Struktur.  Die Funktionen des Moduls werden unter dem Modulknoten aufgeführt.  
  
 Die Quelldatei\-Zeilennummern von Anweisungen, die Speicher belegen, sind unter dem Funktionsknoten aufgeführt, und die Adressen der Anweisungen, die die Zuordnung vornehmen, sind unter dem Zeilenknoten aufgeführt.  Inklusive und exklusive Werte sind für Zeilendaten und Anweisungsdaten immer gleich.  
  
|Spalte|**Beschreibung**|  
|------------|----------------------|  
|**Name**|Der Name des Moduls, die Funktion, Zeilennummer oder Befehlsadresse.|  
|**Prozess\-ID**|Die Prozess\-ID \(PID\) der Profilerstellung.|  
|**Prozessname**|Der Prozessname.|  
|**Modulname**|Der Name des Moduls, das die Funktion enthält.|  
|**Modulpfad**|Der Pfad des Moduls.|  
|**Quelldatei**|Die Quelldatei, die die Definition der Funktion enthält.|  
|**Funktionszeilennummer**|Die Zeilennummer des Anfangs dieser Funktion in der Quelldatei.|  
|**Inclusive Allocations**|-   Bei einer Funktion die Gesamtzahl von Objekten, die von der Funktion erstellt wurden.  Die Zahl umfasst auch Objekte, die in den von der Funktion aufgerufenen Funktionen erstellt wurden.<br />-   Bei einem Modul die Anzahl von Objekten bei einer Profilerstellungsausführung, die zugeordnet wurden, als mindestens eine Funktion des Moduls ausgeführt wurde.  Die Zahl umfasst auch Objekte, die in von den Modulfunktionen aufgerufenen Funktionen erstellt wurden.<br />-   Bei einer Zeile oder Anweisung die Gesamtzahl der Objekte, die von der Zeile oder der Anweisung zugeordnet wurden.|  
|**Inklusive Zuordnungen in %**|Der Prozentsatz aller Objekte, die während der Profilerstellungsausführung zugeordnet wurden und inklusive Zuordnungen des Moduls, der Funktion, der Zeile oder der Anweisung waren.|  
|**Exclusive Allocations**|-   Bei der aktuellen Funktion die Anzahl der Objekte, die während der Ausführung von Code im Funktionsrumpf \(d. h., während sich die Funktion auf der obersten Ebene der Aufrufliste befand\) erstellt wurden.  Die Zahl umfasst keine Objekte, die in den von dieser Funktion aufgerufenen Funktionen erstellt wurden.<br />-   Bei einem Modul die Summe der exklusiven Zuordnungen der Funktionen im Modul.<br />-   Bei einer Zeile oder Anweisung die Gesamtzahl der Objekte, die von der Zeile oder der Anweisung erstellt wurden.|  
|**Exklusive Zuordnungen in %**|Der Prozentsatz aller Objekte, die während der Profilerstellungsausführung zugeordnet wurden und exklusive Zuordnungen des Moduls, der Funktion, der Zeile oder der Anweisung waren.|  
|**Inklusive Bytes**|-   Bei einer Funktion die Gesamtzahl von Bytes, die von der Funktion zugeordnet wurden.  Die Zahl umfasst auch Bytes, die in von der Funktion aufgerufenen Funktionen zugeordnet wurden.<br />-   Bei einem Modul die Anzahl von zugeordneten Bytes während einer Profilerstellung, die bei der Ausführung von mindestens einer Funktion des Moduls zugeordnet wurden.  Die Zahl umfasst auch Objekte, die in allen von den Modulfunktionen aufgerufenen Funktionen erstellt wurden.<br />-   Bei einer Zeile oder Anweisung die Gesamtzahl der Objekte, die von der Zeile oder der Anweisung erstellt wurden.|  
|**Inklusive Bytes in %**|Der Prozentsatz aller während der Profilerstellungsausführung zugeordneten Bytes, die inklusive Bytes des Moduls, der Funktion, der Zeile oder der Anweisung waren.|  
|**Exklusive Bytes**|-   Bei einer Funktion die Gesamtzahl von Bytes, die von der Funktion zugeordnet wurden.  Die Zahl umfasst nicht die Bytes, die in den von der Funktion aufgerufenen Funktionen zugeordnet wurden.<br />-   Bei einem Modul die Summe der exklusiven Bytes, die von den Funktionen im Modul zugeordnet wurden.<br />-   Bei einer Zeile oder Anweisung die Gesamtzahl der Objekte, die von der Zeile oder der Anweisung zugeordnet wurden.|  
|**Exklusive Bytes in %**|Der Prozentsatz aller während der Profilerstellung zugeordneten Bytes, die exklusive Bytes des Moduls, der Funktion, der Zeile oder der Anweisung waren.|  
  
## Siehe auch  
 [Gewusst wie: Anpassen von Spalten in Berichtsansichten](../profiling/how-to-customize-report-view-columns.md)   
 [Modulansicht \- Instrumentation](../profiling/modules-view-dotnet-memory-instrumentation-data.md)   
 [Modulansicht](../profiling/modules-view-sampling-data.md)   
 [Modulansicht](../profiling/modules-view-instrumentation-data.md)