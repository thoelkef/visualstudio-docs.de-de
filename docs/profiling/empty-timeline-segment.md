---
title: Leeres Zeitachsensegment | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.cv.threads.timeline.empty
helpviewer_keywords:
- Concurrency Visualizer, empty timeline segment
ms.assetid: f37b301f-3edc-4e56-8084-feec2dc5a9b1
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: a96cdc7ae4edc7ea7193d5b95dfc73fa1747c1fb
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 03/18/2020
ms.locfileid: "62970108"
---
# <a name="empty-timeline-segment"></a>Leeres Zeitachsensegment
In der Nebenläufigkeitsschnellansicht hängt der Grund dafür, dass ein Abschnitt der Zeitachse leer ist (einen weißen Hintergrund aufweist) von der Art des Kanals ab.

- Bei einem CPU-Threadkanal ist der Grund der, dass der Thread in diesem Teil der Zeitachse nicht vorhanden war. Wenn Sie nach Informationen zu dem Thread suchen, finden Sie den Ausführungsabschnitt mithilfe des Zoomsteuerelements oder indem Sie horizontal scrollen.

- Bei einem E/A-Kanal ist der Grund der, dass zu diesem Zeitpunkt für den Zielprozess kein Datenträgerzugriff durchgeführt wurde.

- Bei einem DirectX-Kanal ist der Grund der, dass in diesem Teil der Zeitachse für den Zielprozess keine GPU-Arbeiten durchgeführt wurden.

- Bei einem Markerkanal ist der Grund der, dass keine Marker generiert wurden.

## <a name="see-also"></a>Weitere Informationen
- [Threads View (Threadansicht)](../profiling/threads-view-parallel-performance.md)
- [Zoomsteuerelement (Threadansicht)](../profiling/zoom-control-threads-view.md)