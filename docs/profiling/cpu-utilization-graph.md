---
title: "CPU-Auslastungsdiagramm | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.cv.cpu.graph"
helpviewer_keywords: 
  - "Parallelitätsschnellansicht für CPU-Auslastungsdiagramm, CPU-Auslastungsdiagramm"
ms.assetid: 5332fd38-622d-47a3-874f-8c2fd7a30f95
caps.latest.revision: 14
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 14
---
# CPU-Auslastungsdiagramm
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Das CPU\-Auslastungsdiagramm veranschaulicht den Grad der Auslastung in einer App im Zeitverlauf an.  Die x\-Achse stellt die Dauer der Ablaufverfolgung dar, die y\-Achse die Anzahl der logischen Kerne im System.  Im Diagramm ist nicht ersichtlich, welcher bestimmte Kern zu einem bestimmten Zeitpunkt aktiv ist.  Wenn beispielsweise zwei Kerne jeder Ausführung bei einer 50\-Prozent\-Kapazität während eines bestimmten Zeitraums sind, dann zeigt dieser Ansicht ein logischer Kern, der verwendet wird.  
  
## CPU\-Auslastungs\-Diagrammfarben  
  
-   Grün gibt die Auslastung der logischen Kerne im System durch den aktuellen Prozess angezeigt.  
  
-   Hellgrau gibt die Auslastung der logischen Kerne durch andere Prozesse im System an.  Ein hoher Anteil von Hellgrauem im CPU\-Diagramm gibt an, dass das System stark von anderen Prozessen ausgelastet wird und dass Ihr Prozess wahrscheinlich daher, durch diese unterbrochen werden.  Zur Verringerung der Auslastung logischer Kerne durch andere Prozesse reduzieren Sie die Anzahl der im System ausgeführten Prozesse.  
  
-   Dunkelgrau gibt die Auslastung der logischen Kerne durch den Systemprozess an.  Dies können Sie nicht direkt steuern, jedoch ist hilfreich, zu wissen, wann davon auftritt, da die Verfügbarkeit logischer Kerne für den Prozess auswirken kann.  
  
-   Weiß gibt die Verfügbarkeit nicht verwendeter logischer Kerne im System an.  Solche Kerne sind für den Prozess verfügbar, wenn Sie mehr Möglichkeiten für Parallelität finden.  
  
## Siehe auch  
 [Auslastungsansicht](../profiling/utilization-view.md)   
 [Durchschnittliche CPU\-Auslastung](../profiling/average-cpu-utilization.md)