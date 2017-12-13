---
title: Synchronisierungszeit | Microsoft-Dokumentation
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: vs.cv.threads.timeline.synchronization
helpviewer_keywords: Concurrency Visualizer, Synchronization Time
ms.assetid: affa04cc-8bba-4848-9301-b19846d3c2cb
caps.latest.revision: "6"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: c6f792e58a2c98219d15e889846921f537d74140
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 10/31/2017
---
# <a name="synchronization-time"></a>Synchronisierungszeit
Diese Segmente in der Zeitachse werden der Blockierungszeit zugeordnet, die als Synchronisierung kategorisiert sind. Wenn ein Thread bei der Synchronisierung als „blockiert“ markiert wird, wird eine der folgenden Optionen impliziert:  
  
-   Die Ausführung des Threads hat möglicherweise einen Aufruf einer bekannten API zur Threadsynchronisierung wie `EnterCriticalSection()` oder `WaitForSingleObject()` ausgelöst.  
  
-   Der mit der API übereinstimmende Algorithmus kann nicht allumfassend sein. Aus diesem Grund können einige APIs, die anderen Kategorien zugeordnet sein können, als Synchronisierung angezeigt werden, weil ein Frame in der Aufrufliste letztendlich einen zugrunde liegenden Blockierungsgrundtyp erreicht hat, der dieser Kategorie zugeordnet war.  
  
 Überprüfen Sie die Liste der blockierten Aufrufe und die Profilberichte sorgfältig, um die Ursache für die Blockierung des Threads nachzuvollziehen.  
  
## <a name="see-also"></a>Siehe auch  
 [Threads View (Threadansicht)](../profiling/threads-view-parallel-performance.md)