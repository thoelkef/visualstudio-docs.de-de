---
title: "Kernansicht | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.performance.view.cores"
helpviewer_keywords: 
  - "Concurrency Visualizer, Kernansicht"
ms.assetid: e47af672-9785-4899-bd45-4d9dda3c396f
caps.latest.revision: 16
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 16
---
# Kernansicht
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Die Kernansicht zeigt, wie die Threadausführung den logischen Prozessorkernen zugeordnet wurde.  Wenn Sie Serveranwendungen schreiben, können Sie in dieser Ansicht die Cacheleistung helfen, optimieren, indem Threadaffinität oder Threadpoolverwaltung.  Sie können Sie auch leichter, um Fälle zu prüfen, in denen die Verwendung möglicherweise der Threadaffinität das Problem der kernübergreifenden Migration verschlechtert.  Die Kernansicht besteht aus zwei Teilen, ein Diagramm und einer Legende.  
  
 Das Diagramm zeigt logische Kerne auf der Y\-Achse und die Zeit auf der X\-Achse an.  Jeder Thread im Diagramm hat eine eindeutige Farbe, sodass Sie die Bewegung Kerne über die Zeit verfolgen können.  Sie können die Threads in diesem Diagramm filtern, indem Sie sie im Bereich "Legende" auswählen.  
  
 Im Bereich "Legende" hat einen Eintrag für jede Farbe im Diagramm.  Jeder Eintrag werden Threadfarbe und die \-Name, die Anzahl kernübergreifender Kontextwechsel, die Gesamtzahl der Kontextwechsel und der Anteil der Kontextwechsel über an, die durch Kerne verlaufen.  Die Legende ist nach Anzahl der kernübergreifenden Kontextwechsel in absteigender Reihenfolge sortiert.  Es werden nur die Threads, die während des angezeigten Zeitraum ausgeführt haben.  Die Liste wird aktualisiert, wenn Sie vergrößern oder schwenken.  
  
## Siehe auch  
 [Parallelitätsschnellansicht](../profiling/concurrency-visualizer.md)   
 [Auslastungsansicht](../profiling/utilization-view.md)   
 [Threadansicht](../profiling/threads-view-parallel-performance.md)