---
title: Ausführungszeit (Threadansicht) | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.cv.threads.timeline.execution
helpviewer_keywords:
- Concurrency Visualizer, Execution Time (Threads View)
ms.assetid: 80c100f8-2502-4613-bfef-4f4f2e09cc8d
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: ac0cf2a60fd194176b7cd9091f4e7dc7a758006f
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 03/18/2020
ms.locfileid: "62969913"
---
# <a name="execution-time-threads-view"></a>Ausführungszeit (Threadansicht)
Diese Segmente auf der Zeitachse der Threadansicht stellen die Ausführungszeit dar, wenn der Thread aktiv an einem logischen Kern im System arbeitet.

 Änderungen am Threadstatus werden durch Kernel-Kontextwechselereignisse erkannt. Beispielstapel werden im Millisekundentakt durch die Ereignisablaufverfolgung für Windows (ETW) erfasst. In einem sehr kurzen grünen Segment ist es möglich, dass kein Beispiel erfasst wird. Daher zeigen einige kurze Ausführungssegmente möglicherweise keine Aufrufliste an.

 Wenn Sie auf ein Ausführungssegment klicken, zeigt die Nebenläufigkeitsschnellansicht den Beispielstapel an, der sich am nächsten zur Position des Klicks befindet. Der Speicherort des Beispielstapels wird durch einen schwarzen Pfeil oder ein Caretzeichen über der Zeitachse angezeigt. Der Beispielstapel erscheint dann auf der Registerkarte **Aktuell**.

 Um ein herkömmliches Samplingprofil für alle Ausführungssegmente in der aktuellen Ansicht anzuzeigen, klicken Sie auf **Ausführung** im sichtbaren Zeitachsenprofil.

## <a name="see-also"></a>Weitere Informationen
- [Ausführungsprofilbericht](../profiling/execution-profile-report.md)
- [Threads View (Threadansicht)](../profiling/threads-view-parallel-performance.md)