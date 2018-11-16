---
title: GPU-Aktivitätsdiagramm | Microsoft-Dokumentation
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
- vs.cv.cpu.graph.gpu
ms.assetid: d7c769af-95fb-49a3-b5ab-deafecee46fa
caps.latest.revision: 14
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 38ba74ac314710b1202f13373685ddbdda0df0f6
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/16/2018
ms.locfileid: "51791123"
---
# <a name="gpu-activity-graph"></a>GPU-Aktivitätsdiagramm
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Das GPU-Aktivitätsdiagramm in der Parallelitätsschnellansicht zeigt die Ebene der DirectX-Aktivität auf dem System durch die Anzahl der DirectX-Engines an, die mit der Zeit verwendet werden.  Im Diagramm wird nicht angezeigt, welche bestimmte Engines verwendet wurden.  Eine Engine wird als „verwendet“ betrachtet, wenn sie GPU-Aufgaben verarbeitet.  
  
## <a name="gpu-activity-graph-colors"></a>Farben im GPU-Aktivitätsdiagramm  
 Grün zeigt den Verbrauch von DirectX-Engines durch den aktuellen Prozess an.  
  
 Hellgrau zeigt den Verbrauch von DirectX-Engines durch andere Prozesse im System an. Um den Verbrauch von DirectX-Engines durch andere Prozesse zu reduzieren, verringern Sie die Anzahl von anderen im System ausgeführten Prozessen.  
  
 Weiß zeigt die Verfügbarkeit der nicht verwendeten DirectX-Engines im System an. Diese Engines sind für Ihren Prozess verfügbar, wenn Sie weitere Möglichkeiten finden, um sie auszunutzen. Einige Engines können nur für bestimmte Arten von Aufgaben verwendet werden.  
  
## <a name="see-also"></a>Siehe auch  
 [Auslastungsansicht](../profiling/utilization-view.md)



