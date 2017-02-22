---
title: "Zeit f&#252;r die vorzeitige Entfernung | Microsoft Docs"
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
  - "vs.cv.threads.timeline.preemption"
helpviewer_keywords: 
  - "Parallelitätsschnellansicht, Zeit für die vorzeitige Entfernung"
ms.assetid: 6b78f91e-a006-440c-83fb-e7368040951d
caps.latest.revision: 6
caps.handback.revision: 6
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# Zeit f&#252;r die vorzeitige Entfernung
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Diese Segmente in der Zeitachse sind der Blockierungszeit zugeordnet, die als vorzeitige Entfernung kategorisiert ist.  Diese Kategorie bedeutet, dass ein Thread aus einem der folgenden Gründe beendet wird:  
  
-   Der Scheduler hat ihn durch einen Thread mit höherer Priorität ersetzt.  
  
-   Das Ausführungsquantum des Threads ist abgelaufen, und andere Threads waren für die Ausführung bereit.  
  
 Während dieser Zeit wurde ein Thread von einem Kernelwartevorgang blockiert. Der Grund hierfür war, dass die Parallelitätsschnellansicht als vorzeitige Entfernung zählt.  Segmente mit vorzeitiger Entfernung starten, wenn ein Thread aus einem logischen Kern geschoben wird, und enden, wenn dieser Thread die Ausführung fortsetzt.  
  
 Die QuickInfo für ein vorzeitig entferntes Segment zeigt den Namen des Prozesses oder Threads an, der die vorzeitige Entfernung verursacht hat.  Dies bedeutet nicht jedoch, dass der übernehmende Prozess oder Thread während des Zeitraums mit der vorzeitigen Entfernung ausgeführt wurde.  
  
## Siehe auch  
 [Threadansicht](../profiling/threads-view-parallel-performance.md)