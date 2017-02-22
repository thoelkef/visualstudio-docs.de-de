---
title: "GPU-Aktivit&#228;tsdiagramm | Microsoft Docs"
ms.custom: ""
ms.date: "12/02/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.cv.cpu.graph.gpu"
ms.assetid: d7c769af-95fb-49a3-b5ab-deafecee46fa
caps.latest.revision: 9
caps.handback.revision: 9
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# GPU-Aktivit&#228;tsdiagramm
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Das GPU\-Aktivitätsdiagramm in der Parallelitätsschnellansicht werden die Ebene der DirectX\-Aktivität im System an, wie durch die Anzahl von DirectX\-Modulen gemessen, die im Zeitverlauf angezeigt.  Im Diagramm ist nicht ersichtlich, welche bestimmten Modulen verwendet wurden.  Ein Modul wird als verwendet berücksichtigt, wenn eine GPU\-Arbeit verarbeitet.  
  
## GPU\-Aktivitäts\-Diagramm\-Farben  
 Grün gibt die Auslastung der DirectX\-Modulen durch den aktuellen Prozess angezeigt.  
  
 Hellgrau gibt die Auslastung der DirectX\-Modulen durch andere Prozesse im System an.  Zur Verringerung der Auslastung DirectX\-Modulen durch andere Prozesse reduzieren, verringern Sie die Anzahl von anderen Prozessen, die auf dem System ausgeführt werden.  
  
 Weiß gibt die Verfügbarkeit nicht verwendeter DirectX\-Modulen im System an.  Diese Module sind für den Prozess verfügbar, wenn Sie mehr Möglichkeiten finden, sie zu verwenden.  Einige Module können für bestimmte Arten von Aufgaben nur verwendet werden.  
  
## Siehe auch  
 [Auslastungsansicht](../profiling/utilization-view.md)