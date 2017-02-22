---
title: "Anweisungszeigeransicht - Profiler-Konfliktdaten | Microsoft Docs"
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
  - "Anweisungszeiger (Ansicht)"
ms.assetid: f5e49c24-d4cf-4f87-977d-37e3223d1196
caps.latest.revision: 9
caps.handback.revision: 9
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# Anweisungszeigeransicht - Profiler-Konfliktdaten
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

In der Anweisungszeigeransicht der Konfliktdaten werden Daten für die Assemblyanweisungen aufgelistet, deren Ausführung bei der Profilerstellung blockiert wurde.  
  
 In der folgenden Tabelle werden die Werte der Spalten in der Anweisungszeigeransicht erläutert.  
  
|Spalte|**Beschreibung**|  
|------------|----------------------|  
|**Exklusive blockierte Zeit**|Die blockierte Zeit in dieser Funktion.|  
|**Exklusive blockierte Zeit %**|Der Prozentsatz der blockierten Zeit, während der die Anweisung ausgeführt wurde.|  
|**Exklusive Konflikte**|Die Anzahl von Konflikten, die aufgetreten sind, während die Anweisung ausgeführt wurde.|  
|**Exklusive Konflikte %**|Der Prozentsatz aller Konflikte bei der Profilerstellung, die aufgetreten sind, während die Anweisung ausgeführt wurde.|  
|**Function Address**|Die Anfangsspeicheradresse der Funktion in der geladenen Binärdatei.|  
|**Function Name**|Der Name der Funktion, die die Anweisung enthält.|  
|**Instruction Address**|Die Speicheradresse der Anweisung in der geladenen Binärdatei.|  
|**Funktionszeilennummer**|Die Zeilennummer des Anfangs dieser Funktion in der Quelldatei.|  
|**Modulname**|Der Name des Moduls, das die Anweisung enthält.|  
|**Modulpfad**|Der Pfad des Moduls, das die Anweisung enthält.|  
|**Prozess\-ID**|Die Prozess\-ID \(PID\) des profilierten Prozesses.|  
|**Prozessname**|Der Prozessname.|  
|**Source Character Begin**|Der Offset des Zeichens in der Quelldateizeile, an der diese Anweisung beginnt.|  
|**Source Character End**|Der Offset des Zeichens in der Quelldateizeile, an der diese Anweisung endet.|  
|**Quelldatei**|Die Quelldatei, die die Anweisung enthält.|  
|**Source Line Begin**|Die Zeilennummer in der Quelldatei, an der diese Anweisung beginnt.|  
|**Source Line End**|Die Zeilennummer in der Quelldatei, an der diese Anweisung endet.|  
  
## Siehe auch  
 [Gewusst wie: Anpassen von Spalten in Berichtsansichten](../profiling/how-to-customize-report-view-columns.md)   
 [Anweisungszeigeransicht](../profiling/instruction-pointers-ips-view.md)   
 [Anweisungszeigeransicht \- Sampling](../profiling/instruction-pointers-ips-view-dotnet-memory-sampling-data.md)   
 [Anweisungszeigeransicht](../profiling/instruction-pointers-ips-view-sampling-data.md)