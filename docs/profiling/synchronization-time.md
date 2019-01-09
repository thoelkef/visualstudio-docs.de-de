---
title: Synchronisierungszeit | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.cv.threads.timeline.synchronization
helpviewer_keywords:
- Concurrency Visualizer, Synchronization Time
ms.assetid: affa04cc-8bba-4848-9301-b19846d3c2cb
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 8d4c6542c2e72428c06825a1d44ba7d0b04b7648
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 01/02/2019
ms.locfileid: "53903824"
---
# <a name="synchronization-time"></a>Synchronisierungszeit
Diese Segmente in der Zeitachse werden der Blockierungszeit zugeordnet, die als Synchronisierung kategorisiert sind. Wenn ein Thread bei der Synchronisierung als „blockiert“ markiert wird, wird eine der folgenden Optionen impliziert:  
  
- Die Ausführung des Threads hat möglicherweise einen Aufruf einer bekannten API zur Threadsynchronisierung wie `EnterCriticalSection()` oder `WaitForSingleObject()` ausgelöst.  
  
- Der mit der API übereinstimmende Algorithmus kann nicht allumfassend sein. Aus diesem Grund können einige APIs, die anderen Kategorien zugeordnet sein können, als Synchronisierung angezeigt werden, weil ein Frame in der Aufrufliste letztendlich einen zugrunde liegenden Blockierungsgrundtyp erreicht hat, der dieser Kategorie zugeordnet war.  
  
  Überprüfen Sie die Liste der blockierten Aufrufe und die Profilberichte sorgfältig, um die Ursache für die Blockierung des Threads nachzuvollziehen.  
  
## <a name="see-also"></a>Siehe auch  
 [Threadansicht](../profiling/threads-view-parallel-performance.md)