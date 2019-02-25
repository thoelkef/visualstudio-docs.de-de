---
title: Standbyzeit | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.cv.threads.timeline.sleep
helpviewer_keywords:
- Concurrency Visualizer, Sleep Time
ms.assetid: 3ddb96f9-9bda-4a68-ad4d-ef488a0a68dc
caps.latest.revision: 11
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 8a79bbca9f6275f115105cc2ba6b001ac0ca7d44
ms.sourcegitcommit: a83c60bb00bf95e6bea037f0e1b9696c64deda3c
ms.translationtype: MTE95
ms.contentlocale: de-DE
ms.lasthandoff: 02/19/2019
ms.locfileid: "54774619"
---
# <a name="sleep-time"></a>Standbyzeit
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Diese Segmente in der Zeitachse werden der Blockierungszeit zugeordnet, die als Standby kategorisiert ist. Die Standbykategorie impliziert, dass ein Thread seinen logischen Kern freiwillig aufgegeben hat und jetzt keine Funktionen ausführt. Während dieser Zeit wurde ein Thread in einer API blockiert, die die Parallelitätsschnellansicht als Standby erfasst. APIs wie `Sleep()` und `SwitchToThread()` gehören zu dieser Gruppe.  
  
## <a name="see-also"></a>Siehe auch  
 [Threads View (Threadansicht)](../profiling/threads-view-parallel-performance.md)
