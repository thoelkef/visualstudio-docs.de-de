---
title: GPU-Aktivitätsdiagramm | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.cv.cpu.graph.gpu
ms.assetid: d7c769af-95fb-49a3-b5ab-deafecee46fa
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: c274bc5c98a856e5d2f921f2967d8ee474f06274
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 01/02/2019
ms.locfileid: "53833312"
---
# <a name="gpu-activity-graph"></a>GPU-Aktivitätsdiagramm
Das GPU-Aktivitätsdiagramm in der Parallelitätsschnellansicht zeigt die Ebene der DirectX-Aktivität auf dem System durch die Anzahl der DirectX-Engines an, die mit der Zeit verwendet werden.  Im Diagramm wird nicht angezeigt, welche bestimmte Engines verwendet wurden.  Eine Engine wird als „verwendet“ betrachtet, wenn sie GPU-Aufgaben verarbeitet.  
  
## <a name="gpu-activity-graph-colors"></a>Farben im GPU-Aktivitätsdiagramm  
 Grün zeigt den Verbrauch von DirectX-Engines durch den aktuellen Prozess an.  
  
 Hellgrau zeigt den Verbrauch von DirectX-Engines durch andere Prozesse im System an. Um den Verbrauch von DirectX-Engines durch andere Prozesse zu reduzieren, verringern Sie die Anzahl von anderen im System ausgeführten Prozessen.  
  
 Weiß zeigt die Verfügbarkeit der nicht verwendeten DirectX-Engines im System an. Diese Engines sind für Ihren Prozess verfügbar, wenn Sie weitere Möglichkeiten finden, um sie auszunutzen. Einige Engines können nur für bestimmte Arten von Aufgaben verwendet werden.  
  
## <a name="see-also"></a>Siehe auch  
 [Auslastungsansicht](../profiling/utilization-view.md)