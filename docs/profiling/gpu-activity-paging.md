---
title: "GPU-Aktivit&#228;t (Paging) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.cv.threads.timeline.gpuactivity"
  - "vs.cv.threads.timeline.gpupaging"
ms.assetid: 95284ac5-3492-4f7b-a79f-7d2840a07679
caps.latest.revision: 6
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 6
---
# GPU-Aktivit&#228;t (Paging)
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Die **GPU\-Aktivität \(Paging\)** Segmente auf der Threadregisterkarte stellen Zeiten dar, das als Paginganforderungen GPU verarbeitete.  Die Länge eines Segments stellt die Dauer der Zeit dar, das der GPU einen direkten Speicherzugriff \(DMA\) verarbeitete, das Paket ASP.NET\-Seiten ermöglichen.  In der Regel sind Pakete einem mit der Übertragung des Arbeitsspeichers zwischen CPU und GPU zugeordnet.  
  
 Wenn Sie ein GPU\-Pagingsegment auswählen, zeigt der Bericht zur Registerkarte **Aktuell** Informationen zum DMA\-Paket an, das verarbeitet wurde.  Dies schließt die Zeitdauer ein, die in die Hardwarewarteschlange warten, die dem DirectX\-Modul, den Prozess, die das DMA\-Paket nach und der Uhrzeit zugeordnet wird, die erforderlich ist, um das Paket zu verarbeiten.  
  
## Siehe auch  
 [Auslastungsansicht](../profiling/utilization-view.md)