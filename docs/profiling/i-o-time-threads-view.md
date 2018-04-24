---
title: E/A-Zeit (Threadansicht) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.cv.threads.timeline.io
helpviewer_keywords:
- Concurrency Visualizer, I/O time (Threads View)
ms.assetid: 0c4ec14d-d8dd-49c1-999c-dcbf4e8e1dc8
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: e50301149f844e0063deeb970e5bfb5bd46a55c1
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/19/2018
---
# <a name="io-time-threads-view"></a>E/A-Zeit (Threadansicht)
Diese Segmente in der Zeitachse werden der Blockierung von Zeiten zugeordnet, die als E/A kategorisiert sind. Das bedeutet, dass ein Thread darauf wartet, dass ein E/A-Vorgang abgeschlossen wird. Der Thread wurde möglicherweise in einer API oder von einer E/A-bezogenen Kernelwarteursache blockiert, die von der Parallelitätsschnellansicht als E/A erfasst wird. APIs wie `CreateFile()`, `ReadFile()` und `WSARecv()` gehören zu dieser Gruppe.  
  
## <a name="see-also"></a>Siehe auch  
 [Threads View (Threadansicht)](../profiling/threads-view-parallel-performance.md)