---
title: Ausführungszeit (Threadansicht) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- vs.cv.threads.timeline.execution
helpviewer_keywords:
- Concurrency Visualizer, Execution Time (Threads View)
ms.assetid: 80c100f8-2502-4613-bfef-4f4f2e09cc8d
caps.latest.revision: 15
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 14e873196767c295ea3f333bbf8ef5217dc79d44
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/12/2018
ms.locfileid: "49251200"
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



