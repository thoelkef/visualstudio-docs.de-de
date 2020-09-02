---
title: GPU-Aktivitätsdiagramm | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.cv.cpu.graph.gpu
ms.assetid: d7c769af-95fb-49a3-b5ab-deafecee46fa
caps.latest.revision: 14
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: f4546c3be480349f3e2cb36f483fa8711bc2ac49
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "62434214"
---
# <a name="gpu-activity-graph"></a>GPU-Aktivitätsdiagramm
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Das GPU-Aktivitätsdiagramm in der Parallelitätsschnellansicht zeigt die Ebene der DirectX-Aktivität auf dem System durch die Anzahl der DirectX-Engines an, die mit der Zeit verwendet werden.  Im Diagramm wird nicht angezeigt, welche bestimmte Engines verwendet wurden.  Eine Engine wird als „verwendet“ betrachtet, wenn sie GPU-Aufgaben verarbeitet.  
  
## <a name="gpu-activity-graph-colors"></a>Farben im GPU-Aktivitätsdiagramm  
 Grün zeigt den Verbrauch von DirectX-Engines durch den aktuellen Prozess an.  
  
 Hellgrau zeigt den Verbrauch von DirectX-Engines durch andere Prozesse im System an. Um den Verbrauch von DirectX-Engines durch andere Prozesse zu reduzieren, verringern Sie die Anzahl von anderen im System ausgeführten Prozessen.  
  
 Weiß zeigt die Verfügbarkeit der nicht verwendeten DirectX-Engines im System an. Diese Engines sind für Ihren Prozess verfügbar, wenn Sie weitere Möglichkeiten finden, um sie auszunutzen. Einige Engines können nur für bestimmte Arten von Aufgaben verwendet werden.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Auslastungsansicht](../profiling/utilization-view.md)
