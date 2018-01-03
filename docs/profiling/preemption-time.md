---
title: "Zeit für die vorzeitige Entfernung | Microsoft-Dokumentation"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: vs.cv.threads.timeline.preemption
helpviewer_keywords: Concurrency Visualizer, Preemption Time
ms.assetid: 6b78f91e-a006-440c-83fb-e7368040951d
caps.latest.revision: "6"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 0ee0f1be5d687c145bc2c8af448b30ec364df2f7
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 12/22/2017
---
# <a name="preemption-time"></a>Zeit für die vorzeitige Entfernung
Diese Segmente in der Zeitachse werden der Blockierungszeit zugeordnet, die als Speicherverwaltungszeit kategorisiert ist. Diese Kategorie impliziert, dass ein Thread aus einem der folgenden Gründe deaktiviert wird:  
  
-   Der Planer hat ihn durch einen Thread mit höherer Priorität ersetzt  
  
-   Das Ausführungsquantum des Threads ist abgelaufen, und andere Threads konnten ausgeführt werden  
  
 Gleichzeitig wurde ein Thread aufgrund einer Kernelwarteursache blockiert, die die Parallelitätsschnellansicht als vorzeitige Entfernung erfasst. Die vorzeitige Entfernung der Segmente beginnt, wenn ein Thread aus einem logischen Kern übertragen wird, und endet, wenn der Thread mit der Ausführung fortfährt.  
  
 Die QuickInfo für ein vorzeitig entferntes Segment zeigt den Namen des Prozesses oder Threads an, durch die die vorzeitige Entfernung ausgelöst wurde. Dies impliziert allerdings nicht, dass der Prozess oder der Thread, der den Vorgang übernommen hat, auch wirklich während der vorzeitigen Entfernung ausgeführt wurde.  
  
## <a name="see-also"></a>Siehe auch  
 [Threads View (Threadansicht)](../profiling/threads-view-parallel-performance.md)