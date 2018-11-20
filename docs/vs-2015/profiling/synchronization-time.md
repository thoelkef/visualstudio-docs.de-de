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
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 76775ca0270b46c17506106640ba2d68e795049b
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/16/2018
ms.locfileid: "51755384"
---
# <a name="synchronization-time"></a>Synchronisierungszeit
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Diese Segmente in der Zeitachse werden der Blockierungszeit zugeordnet, die als Synchronisierung kategorisiert sind. Wenn ein Thread bei der Synchronisierung als „blockiert“ markiert wird, wird eine der folgenden Optionen impliziert:  
  
- Die Ausführung des Threads hat möglicherweise einen Aufruf einer bekannten API zur Threadsynchronisierung wie `EnterCriticalSection()` oder `WaitForSingleObject()` ausgelöst.  
  
- Der mit der API übereinstimmende Algorithmus kann nicht allumfassend sein. Aus diesem Grund können einige APIs, die anderen Kategorien zugeordnet sein können, als Synchronisierung angezeigt werden, weil ein Frame in der Aufrufliste letztendlich einen zugrunde liegenden Blockierungsgrundtyp erreicht hat, der dieser Kategorie zugeordnet war.  
  
  Überprüfen Sie die Liste der blockierten Aufrufe und die Profilberichte sorgfältig, um die Ursache für die Blockierung des Threads nachzuvollziehen.  
  
## <a name="see-also"></a>Siehe auch  
 [Threads View (Threadansicht)](../profiling/threads-view-parallel-performance.md)



