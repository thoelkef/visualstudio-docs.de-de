---
title: GPU-Aktivitätsdiagramm | Microsoft-Dokumentation
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
- vs.cv.cpu.graph.gpu
ms.assetid: d7c769af-95fb-49a3-b5ab-deafecee46fa
caps.latest.revision: 14
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: d5a0ef828b221219c3abae0e46ec40d21b6b045c
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/22/2018
ms.locfileid: "47522458"
---
# <a name="gpu-activity-graph"></a>GPU-Aktivitätsdiagramm
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Die neueste Version dieses Themas finden Sie unter [GPU-Aktivitätsdiagramm](https://docs.microsoft.com/visualstudio/profiling/gpu-activity-graph).  
  
Das GPU-Aktivitätsdiagramm in der Parallelitätsschnellansicht zeigt die Ebene der DirectX-Aktivität auf dem System durch die Anzahl der DirectX-Engines an, die mit der Zeit verwendet werden.  Im Diagramm wird nicht angezeigt, welche bestimmte Engines verwendet wurden.  Eine Engine wird als „verwendet“ betrachtet, wenn sie GPU-Aufgaben verarbeitet.  
  
## <a name="gpu-activity-graph-colors"></a>Farben im GPU-Aktivitätsdiagramm  
 Grün zeigt den Verbrauch von DirectX-Engines durch den aktuellen Prozess an.  
  
 Hellgrau zeigt den Verbrauch von DirectX-Engines durch andere Prozesse im System an. Um den Verbrauch von DirectX-Engines durch andere Prozesse zu reduzieren, verringern Sie die Anzahl von anderen im System ausgeführten Prozessen.  
  
 Weiß zeigt die Verfügbarkeit der nicht verwendeten DirectX-Engines im System an. Diese Engines sind für Ihren Prozess verfügbar, wenn Sie weitere Möglichkeiten finden, um sie auszunutzen. Einige Engines können nur für bestimmte Arten von Aufgaben verwendet werden.  
  
## <a name="see-also"></a>Siehe auch  
 [Auslastungsansicht](../profiling/utilization-view.md)



