---
title: "Modulansicht - Profiler-Samplingdaten | Microsoft Docs"
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
  - "Sampling-Profilerstellungsmethode, Modulansicht"
ms.assetid: 816f5633-65d7-41e5-aee1-033628d4e2df
caps.latest.revision: 13
caps.handback.revision: 13
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# Modulansicht - Profiler-Samplingdaten
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

In der Modulansicht der Samplingdaten werden die Leistungsdaten, für die in den Profilerstellungsdaten ein Sampling ausgeführt wurde, nach Modulen gruppiert angezeigt.  Jedes Modul ist der Stamm einer hierarchischen Struktur.  Die Funktionen des Moduls, für die ein Sampling ausgeführt wurde, werden unter dem Modulknoten aufgeführt.  
  
> [!NOTE]
>  Verbesserte Sicherheitsfeatures in Windows 8 und Windows Server 2012 erforderten tiefgreifende Änderungen bei der Datenerfassung des Visual Studio\-Profilers auf diesen Plattformen.  Außerdem benötigen Windows Store\-Apps neue Erfassungsmethoden.  Siehe [Profilerstellung für Windows 8\- und Windows Server 2012\-Anwendungen](../profiling/performance-tools-on-windows-8-and-windows-server-2012-applications.md).  
  
 Wenn die Funktion ausgeführt wurde, als Samplings gesammelt wurden, die Funktion sich also ganz oben in der Aufrufliste befunden hat, werden die zu dem Zeitpunkt ausgeführten Quellzeilen und Anweisungsadressen unter dem Funktionsknoten aufgeführt.  Da die Daten für eine Quellzeile oder einen Anweisungszeiger erfasst werden, wenn die Zeile oder die Anweisung ausgeführt wird, sind die inklusiven und exklusiven Werte der Zeilendaten und der Anweisungsdaten immer gleich.  
  
|Spalte|**Beschreibung**|  
|------------|----------------------|  
|**Name**|Der Name des Moduls, der Funktion, der Zeilennummer oder der Adresse des Anweisungszeigers.|  
|**Prozess\-ID**|Die Prozess\-ID \(PID\) der Profilerstellung.|  
|**Prozessname**|Der Prozessname.|  
|**Modulname**|Der Name des Moduls mit der Funktion, der Zeile oder dem Anweisungszeiger.|  
|**Modulpfad**|Der Pfad des Moduls mit dem Modul, der Funktion, der Zeile oder dem Anweisungszeiger.|  
|**Quelldatei**|Die Quelldatei, die die Definition der Funktion enthält.|  
|**Funktionszeilennummer**|Die Zeilennummer des Anfangs dieser Funktion in der Quelldatei.|  
|**Inclusive Samples**|-   Bei einer Funktion die Anzahl der Samplings, in der diese Funktion oder eine von dieser Funktion aufgerufene Funktion ausgeführt wurde \(d. h., die Anzahl von Samplings in der Aufrufliste, in denen diese Funktion enthalten war\).<br />-   Bei einem Modul die Anzahl der Samplings, bei denen mindestens eine Funktion dieses Moduls ausgeführt wurde.<br />-   Bei einer Zeile oder einer Anweisung die Anzahl der Samplings, in denen diese Zeile oder Anweisung ausgeführt wurde.|  
|**Inklusive Samplings in %**|-   Bei einer Funktion oder einem Modul der Prozentsatz aller Samplings während der Profilerstellung, die inklusiven Samplings dieser Funktion oder dieses Moduls entsprechen.<br />-   Bei einer Zeile oder einer Anweisung der Prozentsatz der Samplings während der Profilerstellung, in der diese Zeile oder Anweisung ausgeführt wurde.|  
|**Exclusive Samples**|-   Bei einer Funktion die Anzahl der Samplings in der Aufrufliste, in denen diese Funktion direkt ausgeführt wurde \(d. h., die Anzahl von Samplings, in denen sich die Funktion an erster Stelle in der Aufrufliste befand\).<br />-   Bei einem Modul die Summe der exklusiven Samplings der Funktionen im Modul.<br />-   Bei einer Zeile oder einer Anweisung die Anzahl der Samplings, in denen diese Zeile oder Anweisung ausgeführt wurde.|  
|**Exklusive Samplings in %**|-   Bei einer Funktion oder einem Modul der Prozentsatz aller Samplings während der Profilerstellung, die exklusiven Samplings dieser Funktion oder dieses Moduls entsprechen.<br />-   Bei einer Zeile oder einer Anweisung der Prozentsatz der Samplings während der Profilerstellung, in der diese Zeile oder Anweisung ausgeführt wurde.|  
  
## Siehe auch  
 [Modulansicht \- Sampling](../profiling/modules-view-dotnet-memory-sampling-data.md)   
 [Modulansicht \- Instrumentation](../profiling/modules-view-dotnet-memory-instrumentation-data.md)   
 [Modulansicht](../profiling/modules-view-instrumentation-data.md)