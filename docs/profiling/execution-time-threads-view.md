---
title: Ausführungszeit (Threadansicht) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.cv.threads.timeline.execution
helpviewer_keywords:
- Concurrency Visualizer, Execution Time (Threads View)
ms.assetid: 80c100f8-2502-4613-bfef-4f4f2e09cc8d
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: bce4b4e5c0d4a9d4f66fade6b01044ac149968a0
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/19/2018
---
# <a name="execution-time-threads-view"></a>Ausführungszeit (Threadansicht)
Diese Segmente auf der Zeitachse der Threadansicht stellen die Ausführungszeit dar, wenn der Thread aktiv an einem logischen Kern im System arbeitet.  
  
 Änderungen am Threadstatus werden durch Kernel-Kontextwechselereignisse erkannt. Beispielstapel werden im Millisekundentakt durch die Ereignisablaufverfolgung für Windows (ETW) erfasst. In einem sehr kurzen grünen Segment ist es möglich, dass kein Beispiel erfasst wird. Daher zeigen einige kurze Ausführungssegmente möglicherweise keine Aufrufliste an.  
  
 Wenn Sie auf ein Ausführungssegment klicken, zeigt die Nebenläufigkeitsschnellansicht den Beispielstapel an, der sich am nächsten zur Position des Klicks befindet. Der Speicherort des Beispielstapels wird durch einen schwarzen Pfeil oder ein Caretzeichen über der Zeitachse angezeigt. Der Beispielstapel erscheint dann auf der Registerkarte **Aktuell**.  
  
 Um ein herkömmliches Samplingprofil für alle Ausführungssegmente in der aktuellen Ansicht anzuzeigen, klicken Sie auf **Ausführung** im sichtbaren Zeitachsenprofil.  
  
## <a name="see-also"></a>Siehe auch  
 [Ausführungsprofilbericht](../profiling/execution-profile-report.md)   
 [Threadansicht](../profiling/threads-view-parallel-performance.md)