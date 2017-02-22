---
title: "Funktionsansicht – Profiler-Konfliktdaten | Microsoft Docs"
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
  - "Funktionsansicht"
ms.assetid: 208773b0-1a54-4b7a-ad37-2b6fd4f731d4
caps.latest.revision: 10
caps.handback.revision: 10
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# Funktionsansicht – Profiler-Konfliktdaten
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Die Funktionsberichtsansicht der Konfliktdatenlisten führt die Funktionen auf, deren Ausführung während der Profilerstellung blockiert wurde.  
  
 In der folgenden Tabelle werden die Werte in einer Funktionsansicht erläutert, die in einer Profilerstellungs\-Datendatei mit der Parallelitätsmethode gesammelt wurden.  
  
|Spalte|**Beschreibung**|  
|------------|----------------------|  
|**Exklusive blockierte Zeit**|Die Zeit, während der die Ausführung von Code durch diese Funktion im Funktionstext blockiert wurde.  Blockierte Zeit in Funktionen, die von der Funktion aufgerufen wurden, ist nicht eingeschlossen.|  
|**Exklusive blockierte Zeit %**|Der Prozentsatz der gesamten blockierten Zeit während der Profilerstellung, die auf die exklusive blockierte Zeit dieser Funktion entfällt.|  
|**Exklusive Konflikte**|Angaben darüber, wie oft bei dieser Funktion die Ausführung von Code im Funktionstext blockiert war.  Konflikte in Funktionen, die von der Funktion aufgerufen wurden, sind nicht eingeschlossen.|  
|**Exklusive Konflikte %**|Der Prozentsatz aller Konflikte während der Profilerstellung, die exklusive Konflikte dieser Funktion waren.|  
|**Function Address**|Die Adresse der Funktion.|  
|**Function Name**|Der vollqualifizierte Name der Funktion.|  
|**Inklusive blockierte Zeit**|Die Zeit, in der diese Funktion oder eine von dieser Funktion aufgerufene Funktion nicht ausgeführt werden konnte.|  
|**Inklusive blockierte Zeit %**|Der Prozentsatz der gesamten blockierten Zeit während der Profilerstellung, die inklusive blockierte Zeit dieser Funktion oder dieses Moduls war.|  
|**Inklusive Konflikte**|Angaben darüber, wie oft die Ausführung dieser Funktion oder einer von dieser Funktion aufgerufenen Funktion blockiert war.|  
|**Inklusive Konflikte %**|Der Prozentsatz aller Konflikte während der Profilerstellung, die inklusive Konflikte dieser Funktion oder dieses Moduls waren.|  
|**Funktionszeilennummer**|Die Zeilennummer des Anfangs dieser Funktion in der Quelldatei.|  
|**Modulname**|Der Name des Moduls, das die Funktion enthält.|  
|**Modulpfad**|Der Pfad des Moduls, das die Funktion enthält.|  
|**Prozess\-ID**|Die Prozess\-ID \(PID\) des Prozesses, in dem die Funktion ausgeführt wurde.|  
|**Prozessname**|Der Prozessname.|  
|**Quelldatei**|Die Quelldatei, die die Definition der Funktion enthält.|  
  
## Siehe auch  
 [Gewusst wie: Anpassen von Spalten in Berichtsansichten](../profiling/how-to-customize-report-view-columns.md)   
 [Funktionsansicht](../profiling/functions-view.md)   
 [Funktionsansicht \- Instrumentation](../profiling/functions-view-dotnet-memory-instrumentation-data.md)   
 [Funktionsansicht \- Sampling](../profiling/functions-view-dotnet-memory-sampling-data.md)   
 [Funktionsansicht](../profiling/functions-view-instrumentation-data.md)   
 [Funktionsansicht](../profiling/functions-view-sampling-data.md)