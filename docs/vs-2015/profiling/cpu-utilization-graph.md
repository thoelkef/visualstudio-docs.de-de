---
title: CPU-Auslastungsdiagramm | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.cv.cpu.graph
helpviewer_keywords:
- CPU Utilization GraphConcurrency Visualizer, CPU Utilization Graph
ms.assetid: 5332fd38-622d-47a3-874f-8c2fd7a30f95
caps.latest.revision: 19
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: cebba40ee1c438e7be8ea97dcfc7050491511039
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MTE95
ms.contentlocale: de-DE
ms.lasthandoff: 01/23/2019
ms.locfileid: "54780733"
---
# <a name="cpu-utilization-graph"></a>CPU-Auslastungsdiagramm
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Das CPU-Auslastungsdiagramm veranschaulicht den Grad der Auslastung in einer App im Zeitverlauf. Die x-Achse stellt die Dauer der Ablaufverfolgung dar, die y-Achse die Anzahl der logischen Kerne im System. Im Diagramm ist nicht ersichtlich, welcher bestimmte Kern zu einem bestimmten Zeitpunkt aktiv ist. Wenn beispielsweise zwei Kerne mit einer Kapazität von 50 % während eines bestimmten Zeitraums ausgeführt werden, zeigt diese Ansicht einen logischen Kern, der verwendet wird.  
  
## <a name="cpu-utilization-graph-colors"></a>Farben des CPU-Auslastungsdiagramms  
  
-   Grün zeigt die Auslastung der logischen Kerne im System durch den aktuellen Prozess an.  
  
-   Hellgrau zeigt die Auslastung der logischen Kerne durch andere Prozesse im System an. Ein hoher Anteil von Hellgrau im CPU-Diagramm gibt an, dass das System stark von anderen Prozessen ausgelastet wird und dass Ihr Prozess daher wahrscheinlich durch diese unterbrochen wird. Zur Verringerung der Auslastung logischer Kerne durch andere Prozesse reduzieren Sie die Anzahl der im System ausgeführten Prozesse.  
  
-   Dunkelgrau gibt die Auslastung der logischen Kerne durch den Systemprozess an. Dies können Sie nicht direkt steuern. Allerdings sollten Sie wissen, wann es dazu kommt, da die Verfügbarkeit logischer Kerne für den Prozess beeinträchtigt werden kann.  
  
-   Weiß gibt die Verfügbarkeit nicht verwendeter logischer Kerne im System an. Solche Kerne sind für den Prozess verfügbar, wenn Sie mehr Möglichkeiten für eine parallele Nutzung finden.  
  
## <a name="see-also"></a>Siehe auch  
 [Auslastungsansicht](../profiling/utilization-view.md)   
 [Durchschnittliche CPU-Auslastung](../profiling/average-cpu-utilization.md)
