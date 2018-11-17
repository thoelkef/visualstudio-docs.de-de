---
title: GPU-Aktivität (Paging) | Microsoft-Dokumentation
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
- vs.cv.threads.timeline.gpuactivity
- vs.cv.threads.timeline.gpupaging
ms.assetid: 95284ac5-3492-4f7b-a79f-7d2840a07679
caps.latest.revision: 11
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: cba0335a7090bc8f7308d5a64e8fedebedd99a6e
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/16/2018
ms.locfileid: "51789927"
---
# <a name="gpu-activity-paging"></a>GPU-Aktivität (Paging)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Die Segmente der **GPU-Aktivität (Paging)** in der Threads-Registerkarte stellen Zeiten dar, in denen die GPU Paging-Anforderungen verarbeitet an  Die Länge eines Segments stellt den Zeitraum dar, in dem die GPU ein DMA-Paging-Paket (direkter Speicherzugriff) verarbeitet hat. In der Regel werden Paging-Pakete mit der Übertragung von Arbeitsspeicher zwischen CPU und GPU zugeordnet.  
  
 Wenn Sie ein Segment des GPU-Paging auswählen, zeigt der Bericht in der Registerkarte **Aktuelle** Informationen über das verarbeitete DMA-Paket an. Dies umfasst die Zeitspanne, in der das Paket in der Hardware-Warteschlange gewartet hat, die mit der DirectX-Engine – der Prozess, der das DMA-Paket gesendet hat – und der Zeit, die zum Verarbeiten des Pakets benötigt wird, verbunden wird.  
  
## <a name="see-also"></a>Siehe auch  
 [Auslastungsansicht](../profiling/utilization-view.md)



