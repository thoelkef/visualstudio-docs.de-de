---
title: GPU-Aktivitätsdiagramm | Microsoft-Dokumentation
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.cv.cpu.graph.gpu
ms.assetid: d7c769af-95fb-49a3-b5ab-deafecee46fa
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 41b7812db05b61c351346e5f0dcfa1bf4bd7bd1f
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/19/2018
---
# <a name="gpu-activity-graph"></a>GPU-Aktivitätsdiagramm
Das GPU-Aktivitätsdiagramm in der Parallelitätsschnellansicht zeigt die Ebene der DirectX-Aktivität auf dem System durch die Anzahl der DirectX-Module an, die mit der Zeit verwendet werden.  Im Diagramm wird nicht angezeigt, welche bestimmte Module verwendet wurden.  Ein Modul wird als „verwendet“ betrachtet, wenn es GPU-Aufgaben verarbeitet.  
  
## <a name="gpu-activity-graph-colors"></a>Farben im GPU-Aktivitätsdiagramm  
 Grün zeigt den Verbrauch von DirectX-Module durch den aktuellen Prozess an.  
  
 Hellgrau zeigt den Verbrauch von DirectX-Module durch andere Prozesse im System an. Um den Verbrauch von DirectX-Module durch andere Prozesse zu reduzieren, verringern Sie die Anzahl von anderen im System ausgeführten Prozessen.  
  
 Weiß zeigt die Verfügbarkeit der nicht verwendeten DirectX-Module im System an. Diese Module sind für Ihren Prozess verfügbar, wenn Sie weitere Möglichkeiten finden, um sie auszunutzen. Einige Module können nur für bestimmte Arten von Aufgaben verwendet werden.  
  
## <a name="see-also"></a>Siehe auch  
 [Auslastungsansicht](../profiling/utilization-view.md)