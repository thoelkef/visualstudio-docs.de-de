---
title: Speicherverwaltungszeit | Microsoft-Dokumentation
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: vs.cv.threads.timeline.paging
helpviewer_keywords: Concurrency Visualizer, Paging Time
ms.assetid: 67af3509-3a7d-435d-bc37-5262448da915
caps.latest.revision: "9"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: c04bdfd537a57bc4578b122d45b6b86eedc6e603
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 10/31/2017
---
# <a name="memory-management-time"></a>Speicherverwaltungszeit
Diese Segmente in der Zeitachse werden der Blockierung von Zeiten zugeordnet, die als Speicherverwaltungszeit kategorisiert sind. Das bedeutet, dass ein Thread durch ein Ereignis blockiert wird, das mit einem Speicherverwaltungsvorgang wie Paging in Verbindung steht. Während dieser Zeit wurde ein Thread in einem API- oder Kernelzustand blockiert, die die Parallelitätsschnellansicht als Speicherverwaltung erfasst. Diese schließen Ereignisse wie Paging und Speicherreservierung ein.  
  
 Überprüfen Sie die zugehörigen Aufruflisten und Profilberichte, um die Gründe für die Blöcke besser zu verstehen, die als Speicherverwaltung eingestuft werden.  
  
## <a name="see-also"></a>Siehe auch  
 [Threads View (Threadansicht)](../profiling/threads-view-parallel-performance.md)