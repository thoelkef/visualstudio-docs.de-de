---
title: Standbyzeit | Microsoft-Dokumentation
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.cv.threads.timeline.sleep
helpviewer_keywords:
- Concurrency Visualizer, Sleep Time
ms.assetid: 3ddb96f9-9bda-4a68-ad4d-ef488a0a68dc
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 0b9a3894097c553d8505fd61f15fbdec8c188e79
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/19/2018
---
# <a name="sleep-time"></a>Standbyzeit
Diese Segmente in der Zeitachse werden der Blockierungszeit zugeordnet, die als Standby kategorisiert ist. Die Standbykategorie impliziert, dass ein Thread seinen logischen Kern freiwillig aufgegeben hat und jetzt keine Funktionen ausführt. Während dieser Zeit wurde ein Thread in einer API blockiert, die die Parallelitätsschnellansicht als Standby erfasst. APIs wie `Sleep()` und `SwitchToThread()` gehören zu dieser Gruppe.  
  
## <a name="see-also"></a>Siehe auch  
 [Threads View (Threadansicht)](../profiling/threads-view-parallel-performance.md)