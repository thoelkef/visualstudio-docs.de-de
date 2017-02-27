---
title: "E/A-Zeit (Threadansicht) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.cv.threads.timeline.io"
helpviewer_keywords: 
  - "Parallelitätsschnellansicht, E/A-Zeit (Threadansicht)"
ms.assetid: 0c4ec14d-d8dd-49c1-999c-dcbf4e8e1dc8
caps.latest.revision: 5
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 5
---
# E/A-Zeit (Threadansicht)
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Diese Segmente in der Zeitachse sind Blockierungszeiten zugeordnet, die als E\/A kategorisiert werden.  Dies bedeutet, dass ein Thread wartet, bis ein E\/A\-Vorgang beendet wurde.  Der Thread wurde möglicherweise in einer API oder durch einen E\/A\-Kernelwartevorgang blockiert, den die Parallelitätsschnellansicht als E\/A ansieht.  Zu dieser Gruppe gehören APIs wie `CreateFile()`, `ReadFile()` und `WSARecv()`.  
  
## Siehe auch  
 [Threadansicht](../profiling/threads-view-parallel-performance.md)