---
title: "Ausf&#252;hrungszeit (Threadansicht) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.cv.threads.timeline.execution"
helpviewer_keywords: 
  - "Nebenläufigkeitsschnellansicht, Ausführungszeit (Threadansicht)"
ms.assetid: 80c100f8-2502-4613-bfef-4f4f2e09cc8d
caps.latest.revision: 10
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 10
---
# Ausf&#252;hrungszeit (Threadansicht)
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Diese Segmente auf der Zeitachse der Threadansicht stellen die Ausführungszeit dar, wenn der Thread aktiv Aufgaben mit einem logischen Kern des Systems ausführt.  
  
 Änderungen des Threadstatus werden anhand von Kontextwechselereignissen des Kernels erkannt.  Von der Ereignisablaufverfolgung für Windows \(Event Tracing for Windows, ETW\) werden jede Millisekunde Beispielstapel aufzeichnet.  Es ist möglich, dass in einem sehr kurzen grünen Segment kein Beispiel aufgezeichnet wird.  Daher wird für einige kurze Ausführungssegmente möglicherweise keine Aufrufliste angezeigt.  
  
 Wenn Sie auf ein Ausführungssegment klicken, zeigt der Parallelitätsschnellansicht der Beispielstapel an, der den Speicherort des Klickens am nächsten ist.  Die Position dieses Beispielstapels wird durch einen schwarzen Pfeil oder ein Caretzeichen über der Zeitachse, der Beispielstapel selbst auf der Registerkarte **Aktuell** angezeigt.  
  
 Um ein herkömmliches Samplingprofil für alle Ausführungssegmente in der aktuellen Ansicht zu sehen, klicken Sie im sichtbaren Zeitachsenprofils auf **Ausführung**.  
  
## Siehe auch  
 [Ausführungsprofilbericht](../profiling/execution-profile-report.md)   
 [Threadansicht](../profiling/threads-view-parallel-performance.md)