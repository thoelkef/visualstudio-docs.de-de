---
title: Bereichsmarker | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.cv.markers.span
ms.assetid: 736b7765-9c71-44d7-85e5-79787d13d91c
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 10e8dad4427f9eba3e8ad4e91a39b65f6729a87a
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 01/25/2019
ms.locfileid: "54924648"
---
# <a name="span-markers"></a>Bereichsmarker
Ein Bereichsmarker stellt eine sinnvolle Phase einer Anwendung dar. Sie können beispielsweise mit einem Bereich ein Zeitintervall darstellen, in dem ein Arbeitselement verarbeitet wird. Seine Länge stellt die Dauer der Phase der entsprechenden Anwendung dar. Diese Abbildung zeigt einen Bereich in der Parallelitätsschnellansicht an:  
  
 ![Span-Marker in der Parallelitätsschnellansicht](../profiling/media/cvmarkerspan.png "CVMarkerSpan")  
Span-Marker in der Parallelitätsschnellansicht  
  
## <a name="span-category"></a>Bereichskategorie  
 Je nach Kategorie wird ein Span-Marker in einer von fünf unterschiedlichen Farben angezeigt. Die Farben werden wiederholt, wenn mehr als fünf Kategorien vorhanden sind. Die Kategorie kann jede beliebige Ganzzahl sein. Die folgende Abbildung zeigt die fünf möglichen Farben:  
  
 ![Fünf Bereiche in verschiedenen Kategorien](../profiling/media/cvmarkerspancategory.png "CVMarkerSpanCategory")  
Die Farben der ersten fünf Bereichskategorien  
  
## <a name="span-aggregation-markers"></a>Span-Aggregationsmarker  
 Manchmal treten Span-Marker so nahe nebeneinander in der Parallelitätschnellansicht auf, dass sie nicht einzeln gezeichnet werden können. Ist dies der Fall, wird ein *Span-Aggregationsmarker* angezeigt, der die zugrunde liegenden Bereiche darstellt. Wenn Sie mit dem Mauszeiger über eines dieser Symbole fahren, zeigt eine QuickInfo die Anzahl der zugrunde liegenden Bereiche an, die dargestellt werden. Vergrößern Sie, um die Bereichs anzuzeigen. Wenn Sie bis zur maximalen Stufe vergrößern und weiterhin ein Span-Aggregationsmarker angezeigt wird, können Sie die zugrunde liegenden Bereichsmarker im [Markerbericht](../profiling/markers-report.md) anzeigen. Die folgende Abbildung zeigt einen Span-Aggregationsmarker:  
  
 ![Ein Span-Aggregationsmarker in der Parallelitätsschnellansicht](../profiling/media/cvmarkerspanaggregate.png "CVMarkerSpanAggregate")  
Span-Aggregationsmarker  
  
## <a name="see-also"></a>Siehe auch  
 [Concurrency Visualizer markers (Parallelitätsschnellansichtsmarker)](../profiling/concurrency-visualizer-markers.md)   
 [SDK der Nebenläufigkeitsschnellansicht](../profiling/concurrency-visualizer-sdk.md)