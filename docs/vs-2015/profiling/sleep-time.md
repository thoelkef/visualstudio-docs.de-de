---
title: Standbyzeit | Microsoft-Dokumentation
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
- vs.cv.threads.timeline.sleep
helpviewer_keywords:
- Concurrency Visualizer, Sleep Time
ms.assetid: 3ddb96f9-9bda-4a68-ad4d-ef488a0a68dc
caps.latest.revision: 11
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 6f9b86ea0fa1b7880893e4d7300efbe51a029ce7
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/16/2018
ms.locfileid: "51801796"
---
# <a name="sleep-time"></a>Standbyzeit
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Diese Segmente in der Zeitachse werden der Blockierungszeit zugeordnet, die als Standby kategorisiert ist. Die Standbykategorie impliziert, dass ein Thread seinen logischen Kern freiwillig aufgegeben hat und jetzt keine Funktionen ausführt. Während dieser Zeit wurde ein Thread in einer API blockiert, die die Parallelitätsschnellansicht als Standby erfasst. APIs wie `Sleep()` und `SwitchToThread()` gehören zu dieser Gruppe.  
  
## <a name="see-also"></a>Siehe auch  
 [Threads View (Threadansicht)](../profiling/threads-view-parallel-performance.md)



