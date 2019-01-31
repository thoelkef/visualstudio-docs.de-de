---
title: Ausführungszeit (Threadansicht) | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.cv.threads.timeline.execution
helpviewer_keywords:
- Concurrency Visualizer, Execution Time (Threads View)
ms.assetid: 80c100f8-2502-4613-bfef-4f4f2e09cc8d
caps.latest.revision: 15
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: b4306e030c2f48d87b12ba6338a847dc9e9aa892
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MTE95
ms.contentlocale: de-DE
ms.lasthandoff: 01/23/2019
ms.locfileid: "54766237"
---
# <a name="execution-time-threads-view"></a>Ausführungszeit (Threadansicht)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Diese Segmente auf der Zeitachse der Threadansicht stellen die Ausführungszeit dar, wenn der Thread aktiv an einem logischen Kern im System arbeitet.  
  
 Änderungen am Threadstatus werden durch Kernel-Kontextwechselereignisse erkannt. Beispielstapel werden im Millisekundentakt durch die Ereignisablaufverfolgung für Windows (ETW) erfasst. In einem sehr kurzen grünen Segment ist es möglich, dass kein Beispiel erfasst wird. Daher zeigen einige kurze Ausführungssegmente möglicherweise keine Aufrufliste an.  
  
 Wenn Sie auf ein Ausführungssegment klicken, zeigt die Nebenläufigkeitsschnellansicht den Beispielstapel an, der sich am nächsten zur Position des Klicks befindet. Der Speicherort des Beispielstapels wird durch einen schwarzen Pfeil oder ein Caretzeichen über der Zeitachse angezeigt. Der Beispielstapel erscheint dann auf der Registerkarte **Aktuell**.  
  
 Um ein herkömmliches Samplingprofil für alle Ausführungssegmente in der aktuellen Ansicht anzuzeigen, klicken Sie auf **Ausführung** im sichtbaren Zeitachsenprofil.  
  
## <a name="see-also"></a>Siehe auch  
 [Ausführungsprofilbericht](../profiling/execution-profile-report.md)   
 [Threadansicht](../profiling/threads-view-parallel-performance.md)
