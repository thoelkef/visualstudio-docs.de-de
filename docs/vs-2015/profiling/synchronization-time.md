---
title: Synchronisierungszeit | Microsoft-Dokumentation
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
- vs.cv.threads.timeline.synchronization
helpviewer_keywords:
- Concurrency Visualizer, Synchronization Time
ms.assetid: affa04cc-8bba-4848-9301-b19846d3c2cb
caps.latest.revision: 11
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 12be885a79daa3ba5531f6da9652d6a9708b3c96
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/23/2018
ms.locfileid: "49826998"
---
# <a name="synchronization-time"></a>Synchronisierungszeit
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Diese Segmente in der Zeitachse werden der Blockierungszeit zugeordnet, die als Synchronisierung kategorisiert sind. Wenn ein Thread bei der Synchronisierung als „blockiert“ markiert wird, wird eine der folgenden Optionen impliziert:  
  
- Die Ausführung des Threads hat möglicherweise einen Aufruf einer bekannten API zur Threadsynchronisierung wie `EnterCriticalSection()` oder `WaitForSingleObject()` ausgelöst.  
  
- Der mit der API übereinstimmende Algorithmus kann nicht allumfassend sein. Aus diesem Grund können einige APIs, die anderen Kategorien zugeordnet sein können, als Synchronisierung angezeigt werden, weil ein Frame in der Aufrufliste letztendlich einen zugrunde liegenden Blockierungsgrundtyp erreicht hat, der dieser Kategorie zugeordnet war.  
  
  Überprüfen Sie die Liste der blockierten Aufrufe und die Profilberichte sorgfältig, um die Ursache für die Blockierung des Threads nachzuvollziehen.  
  
## <a name="see-also"></a>Siehe auch  
 [Threads View (Threadansicht)](../profiling/threads-view-parallel-performance.md)



