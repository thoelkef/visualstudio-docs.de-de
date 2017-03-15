---
title: "Ausf&#252;hrungsprofilbericht | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.cv.threads.report.execution"
helpviewer_keywords: 
  - "Nebenläufigkeitsschnellansicht, Ausführungsprofilbericht"
ms.assetid: c8128472-a8ed-46f4-b1c8-a25358d6f2c1
caps.latest.revision: 9
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 9
---
# Ausf&#252;hrungsprofilbericht
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Der Ausführungsprofilbericht ist ein herkömmliches Samplingprofil.  Samplings werden etwa jede Millisekunde während der Zeiträume genommen, in denen ein Thread auf einem logischen Kern ausgeführt wird, und die Parallelitätsschnellansicht erstellt durch Sortieren des akkumulierten Satzes von Samplingstapeln eine typische Aufrufstruktur.  Die Daten in dieser Tabelle sind vom aktuellem Zeitraum und ausgeblendeten Threads sowie von den möglicherweise angewendeten Filtern abhängig:  
  
-   Wenn Nur eigenen Code ausgewählt ist, werden nur Stapelrahmen mit Benutzercode sowie die Ebene direkt unter dem Benutzercode angezeigt.  
  
-   Wenn der Rauschunterdrückungswert festgelegt ist, werden sortierte Stapel mit einer geringeren als der angegebenen Frequenz aus dem Bericht gefiltert.  
  
 Die folgende Tabelle zeigt die Spalten im Bericht.  
  
|Spalte|**Beschreibung**|  
|------------|----------------------|  
|Name|Der Name der Funktion für die einzelnen Ebenen der Aufrufliste.|  
|Inclusive Samplings|Die Gesamtzahl von Samplings, die für alle Stapel erfasst werden, die diese Ebene der Aufruflistenstruktur bilden.  Die inklusive Anzahl ist die Summe der exklusiven Samplings für diese Funktion und der inklusiven Anzahl für alle untergeordneten Knoten.|  
|Exclusive Samples|Die Gesamtzahl erfasster Samplings, für die diese Funktion die niedrigste Ebene der Aufrufliste bildet.|  
|% inklusive|Der Prozentsatz der gesamten Samplings, die in der Spalte für inklusive Samplings angezeigt werden.  Prozentsätze werden auf zwei Dezimalstellen gerundet.|  
|% exklusive|Der Prozentsatz der gesamten Samplings, die in der Spalte für exklusive Samplings angezeigt werden.  Prozentsätze werden auf zwei Dezimalstellen gerundet.|  
|Details|Der vollqualifizierte Name der Funktion.  Darin eingeschlossen ist, sofern verfügbar, die Zeilenanzahl.|  
  
 Diese Berichtstabelle kann in der Ansicht [Ausführungszeit \(Threadansicht\)](../profiling/execution-time-threads-view.md) angezeigt werden.  
  
## Siehe auch  
 [Threadansicht](../profiling/threads-view-parallel-performance.md)