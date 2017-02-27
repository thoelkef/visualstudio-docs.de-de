---
title: "Synchronisierungszeit | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.cv.threads.timeline.synchronization"
helpviewer_keywords: 
  - "Parallelitätsschnellansicht, Synchronisierungszeit"
ms.assetid: affa04cc-8bba-4848-9301-b19846d3c2cb
caps.latest.revision: 6
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 6
---
# Synchronisierungszeit
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Diese Segmente in der Zeitachse sind Blockierungszeiten zugeordnet, die als Synchronisierung kategorisiert werden.  Wenn ein Thread bei der Synchronisierung als blockiert markiert wird, weist dies auf einen der folgenden Umstände hin:  
  
-   Die Ausführung des Threads hat möglicherweise zu einem Aufruf einer bekannten Threadsynchronisierungs\-API geführt, z. B. `EnterCriticalSection()` oder `WaitForSingleObject()`.  
  
-   Die mit dem Algorithmus übereinstimmende API, kann nicht vollständig umfassend sein, daher können einige APIs, die anderen Kategorien zugeordnet werden können, auch als Synchronisierung angezeigt werden, weil ein Frame in der Aufrufliste einen zugrunde liegenden, kernelblockierenden Primitiven erreicht hat, der dieser Kategorie zugeordnet wurde.  
  
 Um die zugrunde liegenden Ursache eines threadblockierenden Ereignisses zu ermitteln, untersuchen Sie sorgfältig die blockierenden Aufruflisten und Profilberichte.  
  
## Siehe auch  
 [Threadansicht](../profiling/threads-view-parallel-performance.md)