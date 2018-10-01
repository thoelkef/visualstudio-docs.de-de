---
title: Leeres Zeitachsensegment | Microsoft-Dokumentation
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- vs.cv.threads.timeline.empty
helpviewer_keywords:
- Concurrency Visualizer, empty timeline segment
ms.assetid: f37b301f-3edc-4e56-8084-feec2dc5a9b1
caps.latest.revision: 16
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 3002888730ae785d741e7274d6262d23db0faa35
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/22/2018
ms.locfileid: "47512987"
---
# <a name="empty-timeline-segment"></a>Leeres Zeitachsensegment
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Die neueste Version dieses Themas finden Sie unter [leeres Zeitachsensegment](https://docs.microsoft.com/visualstudio/profiling/empty-timeline-segment).  
  
In der Nebenläufigkeitsschnellansicht hängt der Grund dafür, dass ein Abschnitt der Zeitachse leer ist (einen weißen Hintergrund aufweist) von der Art des Kanals ab.  
  
-   Bei einem CPU-Threadkanal ist der Grund der, dass der Thread in diesem Teil der Zeitachse nicht vorhanden war. Wenn Sie nach Informationen zu dem Thread suchen, finden Sie den Ausführungsabschnitt mithilfe des Zoomsteuerelements oder indem Sie horizontal scrollen.  
  
-   Bei einem E/A-Kanal ist der Grund der, dass zu diesem Zeitpunkt für den Zielprozess kein Datenträgerzugriff durchgeführt wurde.  
  
-   Bei einem DirectX-Kanal ist der Grund der, dass in diesem Teil der Zeitachse für den Zielprozess keine GPU-Arbeiten durchgeführt wurden.  
  
-   Bei einem Markerkanal ist der Grund der, dass keine Marker generiert wurden.  
  
## <a name="see-also"></a>Siehe auch  
 [Threads View (Threadansicht)](../profiling/threads-view-parallel-performance.md)   
 [Zoom Control (Threads View) (Zoomsteuerelement (Threadansicht))](../profiling/zoom-control-threads-view.md)



