---
title: E/A-Zeit (Threadansicht) | Microsoft-Dokumentation
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
- vs.cv.threads.timeline.io
helpviewer_keywords:
- Concurrency Visualizer, I/O time (Threads View)
ms.assetid: 0c4ec14d-d8dd-49c1-999c-dcbf4e8e1dc8
caps.latest.revision: 10
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: d25512da43fc32b42c2a1f79e3c8dbe992ea30ce
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/22/2018
ms.locfileid: "47523997"
---
# <a name="io-time-threads-view"></a>E/A-Zeit (Threadansicht)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Die neueste Version dieses Themas finden Sie unter [e / A-Zeit (Threadansicht)](https://docs.microsoft.com/visualstudio/profiling/i-o-time-threads-view).  
  
Diese Segmente in der Zeitachse werden der Blockierung von Zeiten zugeordnet, die als E/A kategorisiert sind. Das bedeutet, dass ein Thread darauf wartet, dass ein E/A-Vorgang abgeschlossen wird. Der Thread wurde möglicherweise in einer API oder von einer E/A-bezogenen Kernelwarteursache blockiert, die von der Parallelitätsschnellansicht als E/A erfasst wird. APIs wie `CreateFile()`, `ReadFile()` und `WSARecv()` gehören zu dieser Gruppe.  
  
## <a name="see-also"></a>Siehe auch  
 [Threads View (Threadansicht)](../profiling/threads-view-parallel-performance.md)



