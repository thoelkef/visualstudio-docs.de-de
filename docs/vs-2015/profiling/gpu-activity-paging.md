---
title: GPU-Aktivität (Paging) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 2018-06-30
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
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 9c11bd0fd8f348ff90e95660e5df03a4aa591d96
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/22/2018
ms.locfileid: "47510675"
---
# <a name="gpu-activity-paging"></a>GPU-Aktivität (Paging)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Die neueste Version dieses Themas finden Sie unter [GPU-Aktivität (Paging)](https://docs.microsoft.com/visualstudio/profiling/gpu-activity-paging).  
  
Die Segmente der **GPU-Aktivität (Paging)** in der Threads-Registerkarte stellen Zeiten dar, in denen die GPU Paging-Anforderungen verarbeitet an  Die Länge eines Segments stellt den Zeitraum dar, in dem die GPU ein DMA-Paging-Paket (direkter Speicherzugriff) verarbeitet hat. In der Regel werden Paging-Pakete mit der Übertragung von Arbeitsspeicher zwischen CPU und GPU zugeordnet.  
  
 Wenn Sie ein Segment des GPU-Paging auswählen, zeigt der Bericht in der Registerkarte **Aktuelle** Informationen über das verarbeitete DMA-Paket an. Dies umfasst die Zeitspanne, in der das Paket in der Hardware-Warteschlange gewartet hat, die mit der DirectX-Engine – der Prozess, der das DMA-Paket gesendet hat – und der Zeit, die zum Verarbeiten des Pakets benötigt wird, verbunden wird.  
  
## <a name="see-also"></a>Siehe auch  
 [Auslastungsansicht](../profiling/utilization-view.md)



