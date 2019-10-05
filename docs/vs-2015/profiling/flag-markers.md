---
title: Flag-Marker | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.cv.markers.flag
ms.assetid: f3ec919e-63e5-484b-adbf-8f0e79342e75
caps.latest.revision: 14
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: e531d2d2a41cc9ceaa3b6ba39c6d77a166cfae83
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MTE95
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "68193679"
---
# <a name="flag-markers"></a>Flag-Marker
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Ein Flag-Marker stellt ein Ereignis dar, das zu einem bestimmten Zeitpunkt in einer App aufgetreten ist. Ein Flag kann verschiedene Anwendungsereignisse darstellen. Ein Flag kann z.B. die Planung eines bestimmten Arbeitselements oder eine ausgelöste Ausnahme anzeigen. Runtimes wie die Task Parallel Library können auch Flags generieren.  
  
## <a name="flag-importance"></a>Wichtigkeit der Flags  
 Je nach ihrer Wichtigkeit werden Flags in unterschiedlichen Größen angezeigt. Wie bei allen Markern kann die Wichtigkeit niedrig, normal, hoch oder kritisch sein.  Diese Abbildung zeigt die Darstellung der Marker nach ihrer Wichtigkeit geordnet:  
  
 ![Marker nach ihrer Wichtigkeit geordnet: Niedrig, Normal, Hoch und Kritisch](../profiling/media/cvmarkerimportance.png "CVMarkerImportance")  
Marker zeigen die Wichtigkeit von Flags an  
  
## <a name="flag-category"></a>Flag-Kategorie  
 Je nach Kategorie wird ein Flag in einer dieser fünf Farben angezeigt. Die Farben werden wiederverwendet, wenn mehr als fünf Kategorien vorhanden sind. Sie können die Farbe nicht auswählen. Wie bei Markern kann die Kategorie jede beliebige Ganzzahl sein. Die folgende Abbildung zeigt die Farben der ersten fünf Kategorien an.  
  
 ![Die Fünf Farben der Kategoriemarker](../profiling/media/cvmarkercategory.png "CVMarkerCategory")  
Marker zeigen Kategorien an  
  
## <a name="alerts"></a>Benachrichtigungen  
 Eine Warnung ist ein rotfarbiges Flag, das ein wichtiges Anwendungsereignis wie etwa eine Ausnahme angibt.  So sieht eine Warnung aus:  
  
 ![Warnungsmarker für die Parallelitätsschnellansicht](../profiling/media/cvmarkeralert.png "CVMarkerAlert")  
Eine Warnung  
  
## <a name="aggregation-flags"></a>Aggregationsflags  
 Manchmal treten Flags so nah nebeneinander in der Parallelitätschnellansicht auf, dass sie nicht einzeln gezeichnet werden können. In diesem Fall wird ein graues *Aggregationsflag* angezeigt, das die zugrundeliegenden Flags darstellt. Wenn Sie mit dem Mauszeiger über eines dieser Symbole fahren, zeigt eine QuickInfo die Anzahl der zugrunde liegenden Flags an, die dargestellt werden. Zoomen Sie herein, um die Flags anzuzeigen. Wenn Sie bis zur maximalen Stufe vergrößern und weiterhin ein Aggregationsflag angezeigt wird, können Sie die zugrundeliegenden Flags im [Markerbericht](../profiling/markers-report.md) anzeigen.  
  
 Aggregationsflags werden in unterschiedlichen Größen gezeichnet. Die Größe hängt von der Wichtigkeit des wichtigsten Flags in der Aggregation ab. Die folgende Abbildung zeigt die Aggregationsflags in aufsteigender Reihenfolge nach ihrer Wichtigkeit.  
  
 ![Aggregationsflags zeigen vier Wichtigkeitsstufen an](../profiling/media/cvmarkeraggregate.png "CVMarkerAggregate")  
Aggregationsflags nach Wichtigkeit  
  
## <a name="see-also"></a>Siehe auch  
 [Parallelitätsschnellansichtsmarker](../profiling/concurrency-visualizer-markers.md)   
 [SDK der Nebenläufigkeitsschnellansicht](../profiling/concurrency-visualizer-sdk.md)
