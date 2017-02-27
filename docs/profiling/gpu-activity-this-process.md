---
title: "GPU-Aktivit&#228;t (dieser Prozess) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.cv.threads.timeline.gpuexecution"
  - "vs.cv.threads.timeline.gpuactivity"
ms.assetid: 0956edbf-9bcd-4afe-9287-fda628648ca0
caps.latest.revision: 5
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 5
---
# GPU-Aktivit&#228;t (dieser Prozess)
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Die **GPU\-Aktivität dieses Prozesses** Segmente in der Threadansicht in der Parallelitätsschnellansicht stellen Zeiten dar als das Verarbeiten von Anforderungen, GPU im Namen des Stromprozesses war.  Diese Anforderungen werden dem GPU\-Computer als \(DMA\)\- Pakete des direkten Speicherzugriffs gesendet.  Die Länge eines Segments stellt die Zeit dar, dass das DMA\-Paket GPU ein im Namen des aktuellen Prozesses verarbeitete.  
  
 Wenn Sie das GPU\-Aktivitätssegment auswählen, zeigt der Bericht zur Registerkarte **Aktuell** Informationen zum DMA\-Paket an, das verarbeitet wurde.  Diese Informationen umfassen die Zeit, die das Paket auf die Hardwarewarteschlange warten, die dem DirectX\-Modul, den Prozess, den das Paket nach und der Uhrzeit zugeordnet wird, die erforderlich war, um das Paket zu verarbeiten.  Ein Prozess anderen als den aktuellen Prozess gesendet physisch das DMA\-Paket dem GPU\-Computer.  Die Parallelitätsschnellansicht kann wenn eine andere Prozess übertragene Arbeit dem GPU\-Computer im Namen des aktuellen Prozesses erkennen.