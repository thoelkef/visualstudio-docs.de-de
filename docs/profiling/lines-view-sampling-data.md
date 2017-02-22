---
title: "Zeilenansicht - Profiler-Samplingdaten | Microsoft Docs"
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
  - "Zeilenansicht"
ms.assetid: 46497249-c797-42c5-a02c-3e4bb3b4ee60
caps.latest.revision: 11
caps.handback.revision: 11
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# Zeilenansicht - Profiler-Samplingdaten
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Die Zeilenansicht für Samplingdaten führt Leistungsdaten für die Anweisungen auf, die ausgeführt wurden, als die Samplings während der Profilerstellung gesammelt wurden.  
  
> [!NOTE]
>  Verbesserte Sicherheitsfeatures in Windows 8 und Windows Server 2012 erforderten tiefgreifende Änderungen bei der Datenerfassung des Visual Studio\-Profilers auf diesen Plattformen.  Außerdem benötigen Windows Store\-Apps neue Erfassungsmethoden.  Siehe [Profilerstellung für Windows 8\- und Windows Server 2012\-Anwendungen](../profiling/performance-tools-on-windows-8-and-windows-server-2012-applications.md).  
  
 In einer Quelldatei kann eine Anweisung mehrere Zeilen umfassen, und eine einzelne Zeile kann mehr als eine Anweisung enthalten.  Eine Anweisung wird mit Folgendem identifiziert:  
  
-   Den Namen der Quelldatei, die diese Funktionsanweisung enthält.  
  
-   Die Funktion, die die Anweisung enthält.  
  
-   Die Quellzeile, in der die Anweisung beginnt.  
  
-   Das Zeichen in der Quellzeile, mit dem die Anweisung beginnt.  
  
-   Die Quellzeile, in der die Anweisung endet.  
  
-   Das Zeichen in der Quellzeile, mit dem die Anweisung endet.  
  
 Die Zeilennamenspalte stellt eine sortierbare Verkettung der Bezeichnerdaten bereit.  
  
 Laut Definition ruft eine Anweisung keine anderen Funktionen auf.  Daher sind nur exklusive Werte aufgeführt.  
  
|Spalte|**Beschreibung**|  
|------------|----------------------|  
|**Prozess\-ID**|Die Prozess\-ID \(PID\) der Profilerstellung.|  
|**Prozessname**|Der Prozessname.|  
|**Modulname**|Der Name des Moduls, das die Funktionszeile enthält.|  
|**Modulpfad**|Der Pfad des Moduls, das die Funktionszeile enthält.|  
|**Quelldatei**|Die Quelldatei, die diese Funktionszeile enthält.|  
|**Function Name**|Der Name der Funktion.|  
|**Funktionszeilennummer**|Die Zeilennummer des Anfangs dieser Funktion in der Quelldatei.|  
|**Function Address**|Die Startadresse der Funktion.|  
|**Source Line Begin**|Die Nummer der Anfangszeile in der Quelldatei, an der dieses Beispiel gesammelt wurde.|  
|**Source Line End**|Die letzte Zeilennummer in der Quelldatei, an der dieses Beispiel gesammelt wurde.|  
|**Source Character Begin**|Der Offset des Startzeichens in der Quelldateizeile, an dem dieses Beispiel gesammelt wurde.|  
|**Source Character End**|Der Offset des Endzeichens in der Quelldateizeile, an dem dieses Beispiel gesammelt wurde.|  
|**Zeilenname**|Ein Profiler\-generierter Bezeichner der Zeile mit der folgenden Syntax:`Source File`**;\[**`Line Number Start`**,**`Character Start`**\]\-\>;\[**`Line Number End`**,**`Character End`**\]**|  
|**Exclusive Samples**|Die Gesamtzahl der Samplings, die während der Ausführung der Funktionszeile erfasst wurden.|  
|**Exklusive Samplings in %**|Der Prozentsatz aller Samplings während der Profilerstellung, die gesammelt wurden, als die Funktionszeile ausgeführt wurde.|  
  
## Siehe auch  
 [Zeilenansicht \- Sampling](../profiling/lines-view-dotnet-memory-sampling-data.md)