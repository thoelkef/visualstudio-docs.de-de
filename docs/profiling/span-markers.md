---
title: Bereichsmarker | Microsoft-Dokumentation
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- vs.cv.markers.span
ms.assetid: 736b7765-9c71-44d7-85e5-79787d13d91c
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
ms.openlocfilehash: e476a1d0f3af8a0a0c9b9159d710fc7c5680a00d
ms.contentlocale: de-de
ms.lasthandoff: 05/13/2017

---
# <a name="span-markers"></a>Bereichsmarker
Ein Bereichsmarker stellt eine sinnvolle Phase einer Anwendung dar. Sie können beispielsweise mit einem Bereich ein Zeitintervall darstellen, in dem eine Arbeitsaufgabe verarbeitet wird. Seine Länge stellt die Dauer der Phase der entsprechenden Anwendung dar. Diese Abbildung zeigt einen Bereich in der Parallelitätsschnellansicht an:  
  
 ![Span-Marker in der Parallelitätsschnellansicht](../profiling/media/cvmarkerspan.png "CVMarkerSpan")  
Span-Marker in der Parallelitätsschnellansicht  
  
## <a name="span-category"></a>Bereichskategorie  
 Je nach Kategorie wird ein Span-Marker in einer von fünf unterschiedlichen Farben angezeigt. Die Farben werden wiederholt, wenn mehr als fünf Kategorien vorhanden sind. Die Kategorie kann jede beliebige Ganzzahl sein. Die folgende Abbildung zeigt die fünf möglichen Farben:  
  
 ![Fünf Bereiche in verschiedenen Kategorien](../profiling/media/cvmarkerspancategory.png "CVMarkerSpanCategory")  
Die Farben der ersten fünf Bereichskategorien  
  
## <a name="span-aggregation-markers"></a>Span-Aggregationsmarker  
 Manchmal treten Span-Marker so nahe nebeneinander in der Parallelitätschnellansicht auf, dass sie nicht einzeln gezeichnet werden können. Ist dies der Fall, wird ein *Span-Aggregationsmarker* angezeigt, der die zugrunde liegenden Bereiche darstellt. Wenn Sie mit dem Mauszeiger über eines dieser Symbole fahren, zeigt eine QuickInfo die Anzahl der zugrunde liegenden Bereiche an, die dargestellt werden. Vergrößern Sie, um die Bereichs anzuzeigen. Wenn Sie bis zur maximalen Stufe vergrößern und weiterhin ein Span-Aggregationsmarker angezeigt wird, können Sie die zugrunde liegenden Bereichsmarker im [Markerbericht](../profiling/markers-report.md) anzeigen. Die folgende Abbildung zeigt einen Span-Aggregationsmarker:  
  
 ![Span-Aggregationsmarker in der Parallelitätsschnellansicht](~/profiling/media/cvmarkerspanaggregate.png "CVMarkerSpanAggregate")  
Span-Aggregationsmarker  
  
## <a name="see-also"></a>Siehe auch  
 [Parallelitätsschnellansichtsmarker](../profiling/concurrency-visualizer-markers.md)   
 [Parallelitätsschnellansichts-SDK](../profiling/concurrency-visualizer-sdk.md)
