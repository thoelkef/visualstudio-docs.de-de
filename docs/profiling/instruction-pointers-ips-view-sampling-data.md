---
title: "Anweisungszeigeransicht - Profiler-Samplingdaten | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Anweisungszeiger (Ansicht)"
ms.assetid: c7f647bb-c5a3-4708-9f9d-33c0fd6e2e96
caps.latest.revision: 11
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 11
---
# Anweisungszeigeransicht - Profiler-Samplingdaten
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

In der Samplingdatenansicht der Anweisungszeiger werden die Leistungsdaten für die Assemblyanweisungen aufgeführt, die beim Erfassen der Samplings während der Profilerstellung direkt ausgeführt wurden.  
  
> [!NOTE]
>  Verbesserte Sicherheitsfeatures in Windows 8 und Windows Server 2012 erforderten tiefgreifende Änderungen bei der Datenerfassung des Visual Studio\-Profilers auf diesen Plattformen.  Außerdem benötigen Windows Store\-Apps neue Erfassungsmethoden.  Siehe [Profilerstellung für Windows 8\- und Windows Server 2012\-Anwendungen](../profiling/performance-tools-on-windows-8-and-windows-server-2012-applications.md).  
  
|Spalte|**Beschreibung**|  
|------------|----------------------|  
|**Prozess\-ID**|Die Prozess\-ID \(PID\) der Profilerstellung.|  
|**Prozessname**|Der Prozessname.|  
|**Modulname**|Der Name des Moduls, das die Anweisung enthält.|  
|**Modulpfad**|Der Pfad des Moduls, das die Anweisung enthält.|  
|**Quelldatei**|Die Quelldatei, die die Anweisung enthält.|  
|**Function Name**|Der Name der Funktion, die die Anweisung enthält.|  
|**Funktionszeilennummer**|Die Zeilennummer des Anfangs dieser Funktion in der Quelldatei.|  
|**Function Address**|Die Anfangsspeicheradresse der Funktion in der geladenen Binärdatei.|  
|**Source Line Begin**|Die Nummer der Anfangszeile in der Quelldatei, an der dieses Beispiel gesammelt wurde.|  
|**Source Line End**|Die letzte Zeilennummer in der Quelldatei, an der dieses Beispiel gesammelt wurde.|  
|**Source Character Begin**|Der Offset des Startzeichens in der Quelldateizeile, an dem dieses Beispiel gesammelt wurde.|  
|**Source Character End**|Der Offset des Endzeichens in der Quelldateizeile, an dem dieses Beispiel gesammelt wurde.|  
|**Instruction Address**|Die Adresse der Anweisung in der geladenen Binärdatei.|  
|**Exclusive Samples**|Die Gesamtzahl der Samplings, die während der Ausführung der Anweisung erfasst wurden.|  
|**Exklusive Samplings in %**|Der Prozentsatz aller Samplings während der Profilerstellung, die beim Ausführen der Anweisung erfasst wurden.|  
  
## Siehe auch  
 [Anweisungszeigeransicht \- Sampling](../profiling/instruction-pointers-ips-view-dotnet-memory-sampling-data.md)