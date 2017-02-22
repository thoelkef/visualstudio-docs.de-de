---
title: "Speicherverwaltungszeit | Microsoft Docs"
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
  - "vs.cv.threads.timeline.paging"
helpviewer_keywords: 
  - "Nebenläufigkeitsschnellansicht, Pagingzeit"
ms.assetid: 67af3509-3a7d-435d-bc37-5262448da915
caps.latest.revision: 9
caps.handback.revision: 9
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# Speicherverwaltungszeit
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Diese Segmente auf der Zeitachse sind Blockierungszeiten zugeordnet, die als Speicherverwaltung kategorisiert werden.  Das bedeutet, dass ein Thread von einem Ereignis blockiert wird, das einem Speicherverwaltungsvorgang \(beispielsweise der Auslagerung\) zugeordnet ist.  Während dieser Zeit wurde ein Thread in einer API oder durch einen Kernelzustand blockiert, den die Parallelitätsschnellansicht als Speicherverwaltung ansieht.  Dazu gehören Ereignisse wie Paging und Speicherbelegung.  
  
 Überprüfen Sie die zugeordneten Aufruflisten und Profilberichte, um die Gründe für Blockierungen besser zu verstehen, die als Speicherverwaltung kategorisiert werden.  
  
## Siehe auch  
 [Threadansicht](../profiling/threads-view-parallel-performance.md)