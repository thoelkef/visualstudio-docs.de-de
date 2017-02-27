---
title: "Objektlebensdaueransicht | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.performance.view.objectlifetime"
helpviewer_keywords: 
  - "Lebensdauer, Objekte"
  - "Objektlebensdauer (Ansicht)"
  - "Leistungsberichte, Objektlebensdauer (Ansicht)"
  - "Berichte für Profilerstellungstools, Lebensdaueransicht"
  - "Profilerstellungstools, Lebensdaueransicht"
ms.assetid: d0501fdd-4b3a-4e74-b6ac-51d950a2e15b
caps.latest.revision: 24
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 24
---
# Objektlebensdaueransicht
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Die Objektlebensdaueransicht ist verfügbar, wenn **Lebensdauerinformationen für .NET\-Objekt auflisten** auf den Eigenschaftenseiten der Leistungssitzung aktiviert wurde.  
  
 Der Garbage Collector von [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] verwaltet die Belegung und Freigabe von Arbeitsspeicher für die Anwendung.  Zur Optimierung der Leistung des Garbage Collectors wird der verwaltete Heap in drei Generationen unterteilt: 0, 1 und 2.  Vom Garbage Collector der Laufzeit werden neue Objekte in Generation 0 gespeichert.  Objekte, die nach den Garbage Collections noch vorhanden sind, werden höher gestuft und in den Generationen 1 und 2 gespeichert.  
  
 Der Garbage Collector gibt Arbeitsspeicher frei, indem er eine ganze Generation von Objekten freigibt.  Für die von der profilierten Anwendung erstellten Objekte werden in der Objektlebensdaueransicht die Zahl und die Größe der Objekte sowie die Generation angezeigt, in der die Objekte freigegeben werden.  
  
## Allgemein  
  
|Spalte|**Beschreibung**|  
|------------|----------------------|  
|**Klassenname**|Der Klassenname des reservierten Typs.|  
|**Prozess\-ID**|Die Prozess\-ID der Profilerstellungsausführung.|  
|**Prozessname**|Der Prozessname.|  
|**Modulname**|Der Name des Moduls, das die Funktion enthält.|  
|**Modulpfad**|Der Pfad des Moduls, das die Funktion enthält.|  
  
## Instanzdaten  
 Instanzdaten geben die Anzahl von Objekten des Typs an, die während der Profilerstellungsausführung erstellt wurden, und die Generation, in der die Objekte vom Garbage Collector freigegeben wurden.  
  
|Spalte|**Beschreibung**|  
|------------|----------------------|  
|**Instanzen**|Die Anzahl der Speicherbelegungen für Objekte dieses Typs.|  
|**Instanzen insgesamt in %**|Der Prozentsatz der Gesamtzahl der Speicherbelegungen während der Profilerstellungsausführung.|  
|**Erfasste Instanzen in Gen 0**|Die Anzahl von Instanzen des Typs, die in Generation 0 des Garbage Collection\-Algorithmus freigegeben wurden.|  
|**Erfasste Instanzen in Gen 1**|Die Anzahl von Instanzen des Typs, die in Generation 1 des Garbage Collection\-Algorithmus freigegeben wurden.|  
|**Erfasste Instanzen in Gen 2**|Die Anzahl von Instanzen des Typs, die in Generation 2 des Garbage Collection\-Algorithmus freigegeben wurden.|  
|**Am Ende aktive Instanzen**|Die Anzahl von Instanzen des Typs, die bis zum Ende der Profilerstellungsausführung nicht freigegeben wurden.|  
  
## Größen\-\(Byte\-\)daten  
 Größen\-\(Byte\-\)daten geben die Größe der Objekte des Typs, die während der Profilerstellungsausführung erstellt wurden, sowie den Arbeitsspeicher an, der in jeder Generierung freigegeben wurde, in der Objekte freigegeben wurden.  
  
|Spalte|**Beschreibung**|  
|------------|----------------------|  
|**Zugewiesene Bytes \(gesamt\)**|Die Gesamtzahl von Bytes für alle Instanzen des Typs.|  
|**Bytes insgesamt in %**|Der Prozentsatz des insgesamt belegten Speichers in Bytes, der während der Profilerstellungsausführung durch Instanzen dieses Typs belegt wurde.|  
|**Erfasste Bytes in Gen 0**|Die Größe der Instanzen des Typs, die in Generation 0 des Garbage Collection\-Algorithmus freigegeben wurden.|  
|**Erfasste Bytes in Gen 1**|Die Größe der Instanzen des Typs, die in Generation 1 des Garbage Collection\-Algorithmus freigegeben wurden.|  
|**Erfasste Bytes in Gen 2**|Die Größe der Instanzen des Typs, die in Generation 2 des Garbage Collection\-Algorithmus freigegeben wurden.|  
  
## Heapdaten für große Objekte  
 Die .NET\-Speicherbelegungsfunktion verwaltet sehr große Objekte in einem vom normalen verwalteten Heap getrennten Speicherort.  Die Heapdaten für große Objekte geben die Zahl und Größe von Objekten des Typs an, die an diesem Speicherort verwaltet wurden.  
  
|Spalte|**Beschreibung**|  
|------------|----------------------|  
|**Erfasste Objektheap\-Instanzen**|Die Anzahl von Instanzen dieses Typs, die im großen Objektheap gefunden und bei der Profilerstellungsausführung erfasst wurden.|  
|**Erfasste Objektheap\-Bytes**|Die Größe \(in Bytes\) der Instanzen dieses Typs, die im großen Objektheap gefunden und bei der Profilerstellungsausführung erfasst wurden.|  
  
## Siehe auch  
 [.NET\-Arbeitsspeicherdatenansichten](../profiling/dotnet-memory-data-views.md)