---
title: "Modulansicht – Profiler-Konfliktdaten | Microsoft Docs"
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
ms.assetid: 1a9aa122-2d8f-4a09-b503-92975aa6b648
caps.latest.revision: 12
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 12
---
# Modulansicht – Profiler-Konfliktdaten
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

In der Modulansicht der Konfliktdaten werden die Parallelitätsdaten, für die in den Profilerstellungsdaten ein Sampling ausgeführt wurde, nach Modulen gruppiert angezeigt.  Jedes Modul ist der Stamm einer hierarchischen Struktur.  Die Funktionen des Moduls, in denen Konfliktereignisse aufgetreten sind, werden unter dem Modulknoten aufgeführt.  
  
 Wenn die Funktion eigenen Code ausgeführt hat, als ein Konfliktereignis aufgetreten ist, die Funktion sich also ganz oben in der Aufrufliste befunden hat, werden die zu dem Zeitpunkt ausgeführten Quellzeilen und Anweisungsadressen unter dem Funktionsknoten aufgeführt.  Da die Daten für eine Quellzeile oder einen Anweisungszeiger erfasst werden, wenn die Zeile oder die Anweisung ausgeführt wird, sind die inklusiven und exklusiven Werte der Zeilendaten und der Anweisungsdaten immer gleich.  
  
 In der folgenden Tabelle werden die Werte der Spalten in der Modulansicht der Konfliktdaten beschrieben.  
  
|Spalte|**Beschreibung**|  
|------------|----------------------|  
|**Exklusive blockierte Zeit**|-   Bei einer Funktion die Zeit, in der diese Funktion für die Ausführung von Code im Funktionstext blockiert war.  Blockierte Zeit in Funktionen, die von der Funktion aufgerufen wurden, ist nicht eingeschlossen.<br />-   Bei einem Modul die Summe der exklusiven blockierten Zeit der Funktionen in dem Modul.<br />-   Bei einer Zeile oder einer Anweisung die Zeit, in der diese Zeile oder Anweisung für die Ausführung blockiert war.|  
|**Exklusive blockierte Zeit %**|-   Bei einer Funktion oder einem Modul der Prozentsatz der gesamten blockierten Zeit während der Profilerstellung, die der exklusiven blockierten Zeit der Funktion oder des Moduls entspricht.<br />-   Bei einer Zeile oder einer Anweisung der Prozentsatz der gesamten blockierten Zeit während der Profilerstellung, in der diese Zeile oder Anweisung nicht ausgeführt werden konnte.|  
|**Exklusive Konflikte**|-   Bei einer Funktion Angaben darüber, wie oft bei dieser Funktion die Ausführung von Code im Funktionstext blockiert war.  Konflikte in Funktionen, die von der Funktion aufgerufen wurden, sind nicht eingeschlossen.<br />-   Bei einem Modul die Summe der exklusiven Konflikte der Funktionen in dem Modul.<br />-   Bei einer Zeile oder einer Anweisung Angaben darüber, wie oft diese Zeile oder Anweisung für die Ausführung blockiert war.|  
|**Exklusive Konflikte %**|-   Bei einer Funktion oder einem Modul der Prozentsatz aller Konflikte während der Profilerstellung, die exklusiven Konflikten dieser Funktion oder dieses Moduls entsprechen.<br />-   Bei einer Zeile oder einer Anweisung der Prozentsatz aller Konflikte während der Profilerstellung, die Konflikten entsprechen, bei denen die Ausführung der Zeile oder Anweisung blockiert war.|  
|**Inklusive blockierte Zeit**|-   Bei einer Funktion die Zeit, in der diese Funktion oder eine von dieser Funktion aufgerufene Funktion nicht ausgeführt werden konnte.<br />-   Bei einem Modul die Summe der blockierten Zeit, in der sich mindestens eine Funktion dieses Moduls im Stapel befunden hat.<br />-   Bei einer Zeile oder einer Anweisung die Zeit, in der diese Zeile oder Anweisung für die Ausführung blockiert war.|  
|**Inklusive blockierte Zeit %**|-   Bei einer Funktion oder einem Modul der Prozentsatz der gesamten blockierten Zeit während der Profilerstellung, die der inklusiven blockierten Zeit der Funktion oder des Moduls entspricht.<br />-   Bei einer Zeile oder einer Anweisung der Prozentsatz der gesamten blockierten Zeit während der Profilerstellung, in der diese Zeile oder Anweisung ausgeführt wurde.|  
|**Inklusive Konflikte**|-   Bei einer Funktion Angaben darüber, wie oft die Ausführung dieser Funktion oder einer von dieser Funktion aufgerufenen Funktion blockiert war.<br />-   Bei einem Modul die Anzahl der Konflikte, bei denen mindestens eine Funktion dieses Moduls sich im Stapel befunden hat.<br />-   Bei einer Zeile oder einer Anweisung Angaben darüber, wie oft diese Zeile oder Anweisung für die Ausführung blockiert war.|  
|**Inklusive Konflikte %**|-   Bei einer Funktion oder einem Modul der Prozentsatz aller Konflikte während der Profilerstellung, die inklusiven Konflikten dieser Funktion oder dieses Moduls entsprechen.<br />-   Bei einer Zeile oder einer Anweisung der Prozentsatz der gesamten blockierten Zeit während der Profilerstellung, in der diese Zeile oder Anweisung ausgeführt wurde.|  
|**Funktionszeilennummer**|Die Zeilennummer des Anfangs dieser Funktion in der Quelldatei.|  
|**Modulname**|Der Name des Moduls mit der Funktion, der Zeile oder dem Anweisungszeiger.|  
|**Modulpfad**|Der Pfad des Moduls mit dem Modul, der Funktion, der Zeile oder dem Anweisungszeiger.|  
|**Name**|Der Name des Moduls oder der Funktion.|  
|**Prozess\-ID**|Die Prozess\-ID \(PID\) der Profilerstellung.|  
|**Prozessname**|Der Prozessname.|  
|**Quelldatei**|Die Quelldatei, die die Definition der Funktion enthält.|  
  
## Siehe auch  
 [Gewusst wie: Anpassen von Spalten in Berichtsansichten](../profiling/how-to-customize-report-view-columns.md)   
 [Modulansicht](../profiling/modules-view.md)   
 [Modulansicht \- Instrumentation](../profiling/modules-view-dotnet-memory-instrumentation-data.md)   
 [Modulansicht \- Sampling](../profiling/modules-view-dotnet-memory-sampling-data.md)   
 [Modulansicht](../profiling/modules-view-instrumentation-data.md)   
 [Modulansicht](../profiling/modules-view-sampling-data.md)