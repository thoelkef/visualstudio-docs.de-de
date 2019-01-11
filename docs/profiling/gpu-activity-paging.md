---
title: GPU-Aktivität (Paging) | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.cv.threads.timeline.gpuactivity
- vs.cv.threads.timeline.gpupaging
ms.assetid: 95284ac5-3492-4f7b-a79f-7d2840a07679
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 919f99ad24764017e823dbceda51bec4461401e4
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 01/02/2019
ms.locfileid: "53942722"
---
# <a name="gpu-activity-paging"></a>GPU-Aktivität (Paging)
Die Segmente der **GPU-Aktivität (Paging)** in der Registerkarte **Threads** stellen Zeiten dar, zu denen die GPU Paging-Anforderungen verarbeitet hat.  Die Länge eines Segments stellt den Zeitraum dar, in dem die GPU ein DMA-Paging-Paket (direkter Speicherzugriff) verarbeitet hat. In der Regel werden Paging-Pakete mit der Übertragung von Arbeitsspeicher zwischen CPU und GPU zugeordnet.  
  
 Wenn Sie ein Segment des GPU-Paging auswählen, zeigt der Bericht in der Registerkarte **Aktuelle** Informationen über das verarbeitete DMA-Paket an. Dies umfasst die Zeitspanne, in der das Paket in der Hardware-Warteschlange gewartet hat, die mit der DirectX-Engine – der Prozess, der das DMA-Paket gesendet hat – und der Zeit, die zum Verarbeiten des Pakets benötigt wird, verbunden wird.  
  
## <a name="see-also"></a>Siehe auch  
 [Auslastungsansicht](../profiling/utilization-view.md)