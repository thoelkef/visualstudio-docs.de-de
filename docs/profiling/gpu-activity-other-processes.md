---
title: "GPU-Aktivit&#228;t (andere Prozesse) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.cv.threads.timeline.gpuother"
  - "vs.cv.threads.timeline.gpuactivity"
ms.assetid: 8a68df65-eb63-452f-9285-fb4ffc92f2b2
caps.latest.revision: 6
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 6
---
# GPU-Aktivit&#228;t (andere Prozesse)
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Die **GPU\-Aktivität von einem anderen Prozess** Segmente in der Threadansicht der Parallelitätsschnellansicht stellen Zeiten dar als das Verarbeiten von Anforderungen, GPU im Namen anderer Prozesse im System war.  Diese Anforderungen werden dem GPU\-Computer als \(DMA\)\- Pakete des direkten Speicherzugriffs gesendet.  Die Länge eines Segments stellt die Dauer der Zeit dar, die das Paket von GPUs das verarbeitet wurde.  
  
 Wenn Sie diese Art des Segments auswählen, zeigt der Bericht zur Registerkarte **Aktuell** Informationen zum Paket an, das verarbeitet wurde.  Die Informationen umfassen die Zeit, die das Paket auf die Hardwarewarteschlange warten, die dem DirectX\-Modul, den Prozess, den das Paket nach und der Uhrzeit zugeordnet wird, die erforderlich war, um das Paket zu verarbeiten.