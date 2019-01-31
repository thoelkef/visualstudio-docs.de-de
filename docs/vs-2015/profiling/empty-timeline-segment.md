---
title: Leeres Zeitachsensegment | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.cv.threads.timeline.empty
helpviewer_keywords:
- Concurrency Visualizer, empty timeline segment
ms.assetid: f37b301f-3edc-4e56-8084-feec2dc5a9b1
caps.latest.revision: 16
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 4ac39a776cb7e6c2c9cbce648c0b3ca3ebc86783
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MTE95
ms.contentlocale: de-DE
ms.lasthandoff: 01/23/2019
ms.locfileid: "54770744"
---
# <a name="empty-timeline-segment"></a>Leeres Zeitachsensegment
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

In der Nebenläufigkeitsschnellansicht hängt der Grund dafür, dass ein Abschnitt der Zeitachse leer ist (einen weißen Hintergrund aufweist) von der Art des Kanals ab.  
  
-   Bei einem CPU-Threadkanal ist der Grund der, dass der Thread in diesem Teil der Zeitachse nicht vorhanden war. Wenn Sie nach Informationen zu dem Thread suchen, finden Sie den Ausführungsabschnitt mithilfe des Zoomsteuerelements oder indem Sie horizontal scrollen.  
  
-   Bei einem E/A-Kanal ist der Grund der, dass zu diesem Zeitpunkt für den Zielprozess kein Datenträgerzugriff durchgeführt wurde.  
  
-   Bei einem DirectX-Kanal ist der Grund der, dass in diesem Teil der Zeitachse für den Zielprozess keine GPU-Arbeiten durchgeführt wurden.  
  
-   Bei einem Markerkanal ist der Grund der, dass keine Marker generiert wurden.  
  
## <a name="see-also"></a>Siehe auch  
 [Threads View (Threadansicht)](../profiling/threads-view-parallel-performance.md)   
 [Zoom Control (Threads View) (Zoomsteuerelement (Threadansicht))](../profiling/zoom-control-threads-view.md)
