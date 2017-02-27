---
title: "Standbyzeit | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.cv.threads.timeline.sleep"
helpviewer_keywords: 
  - "Parallelitätsschnellansicht, Standbyzeit"
ms.assetid: 3ddb96f9-9bda-4a68-ad4d-ef488a0a68dc
caps.latest.revision: 6
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 6
---
# Standbyzeit
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Diese Segmente in der Zeitachse sind der Blockierungszeit zugeordnet, die als Standbymodus kategorisiert ist.  Die Standbymodus\-Kategorie bedeutet, dass ein Thread seinen logischen Kern freiwillig aufgegeben hat und keine Aktionen ausführt.  Während dieser Zeitspanne wurde ein Thread in einer API blockiert, deren Zustand von der Parallelitätsschnellansicht als Standbymodus angesehen wird.  Zu dieser Gruppe gehören APIs wie `Sleep()` und `SwitchToThread()`.  
  
## Siehe auch  
 [Threadansicht](../profiling/threads-view-parallel-performance.md)