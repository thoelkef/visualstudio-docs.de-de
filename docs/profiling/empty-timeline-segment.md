---
title: "Leeres Zeitachsensegment | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.cv.threads.timeline.empty"
helpviewer_keywords: 
  - "Concurrency Visualizer, leeres Zeitachsensegment"
ms.assetid: f37b301f-3edc-4e56-8084-feec2dc5a9b1
caps.latest.revision: 11
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 11
---
# Leeres Zeitachsensegment
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

In der Parallelitätsschnellansicht verfügt der Grund, dass ein Abschnitt der Zeitachse leer ist \(einen weißen Hintergrund\) hängt von der Art des Kanals.  
  
-   Für einen CPU\-Threadchannel Dies bedeutet, dass der Thread während dieser Zeit nicht vorhanden war.  Wenn Sie am Thread interessieren, können Sie den Abschnitt finden, indem Sie horizontal das Zoomsteuerelement verwenden oder einen Bildlauf durchführen.  
  
-   Für einen Ein\-\/Ausgabekanal bedeutet, dass kein Festplattenspeicher einzutauschen im Namen des Zielprozesses zum betreffenden Zeitpunkt aufgetreten ist.  
  
-   Für einen DirectX\-Channel bedeutet, dass keine GPU\-Arbeit im Namen des Zielprozesses während dieses Teils der Zeitachse ausgeführt wurde.  
  
-   Für einen Markerchannel bedeutet, dass keine Markierungen generiert wurden.  
  
## Siehe auch  
 [Threadansicht](../profiling/threads-view-parallel-performance.md)   
 [Zoomsteuerelement \(Threadansicht\)](../profiling/zoom-control-threads-view.md)