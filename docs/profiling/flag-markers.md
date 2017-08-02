---
title: Flag-Marker | Microsoft-Dokumentation
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- vs.cv.markers.flag
ms.assetid: f3ec919e-63e5-484b-adbf-8f0e79342e75
caps.latest.revision: 9
author: mikejo5000
ms.author: mikejo
manager: ghogen
translation.priority.ht:
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- ru-ru
- zh-cn
- zh-tw
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
ms.translationtype: Human Translation
ms.sourcegitcommit: 47057e9611b824c17077b9127f8d2f8b192d6eb8
ms.openlocfilehash: 0095311f5188260bf1207e4094c1ceb87b1bbb86
ms.contentlocale: de-de
ms.lasthandoff: 05/13/2017

---
# <a name="flag-markers"></a>Flag-Marker
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
  
 ![Warnungsmarker für Parallelitätsschnellansicht](~/profiling/media/cvmarkeralert.png "CVMarkerAlert")  
Eine Warnung  
  
## <a name="aggregation-flags"></a>Aggregationsflags  
 Manchmal treten Flags so nah nebeneinander in der Parallelitätsschnellansicht auf, dass sie nicht einzeln gezeichnet werden können. In diesem Fall wird ein graues *Aggregationsflag* angezeigt, das die zugrundeliegenden Flags darstellt. Wenn Sie mit dem Mauszeiger über eines dieser Symbole fahren, zeigt eine QuickInfo die Anzahl der zugrunde liegenden Flags an, die dargestellt werden. Zoomen Sie herein, um die Flags anzuzeigen. Wenn Sie bis zur maximalen Stufe vergrößern und weiterhin ein Aggregationsflag angezeigt wird, können Sie die zugrundeliegenden Flags im [Markerbericht](../profiling/markers-report.md) anzeigen.  
  
 Aggregationsflags werden in unterschiedlichen Größen gezeichnet. Die Größe hängt von der Wichtigkeit des wichtigsten Flags in der Aggregation ab. Die folgende Abbildung zeigt die Aggregationsflags in aufsteigender Reihenfolge nach ihrer Wichtigkeit.  
  
 ![Aggregationsflags zeigen vier Wichtigkeitsstufen an](~/profiling/media/cvmarkeraggregate.png "CVMarkerAggregate")  
Aggregationsflags nach Wichtigkeit  
  
## <a name="see-also"></a>Siehe auch  
 [Parallelitätsschnellansichtsmarker](../profiling/concurrency-visualizer-markers.md)   
 [Parallelitätsschnellansichts-SDK](../profiling/concurrency-visualizer-sdk.md)
