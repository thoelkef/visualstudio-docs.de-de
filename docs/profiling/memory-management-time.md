---
title: Speicherverwaltungszeit | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.cv.threads.timeline.paging
helpviewer_keywords:
- Concurrency Visualizer, Paging Time
ms.assetid: 67af3509-3a7d-435d-bc37-5262448da915
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 6741aa96941e9265ab414ea7d73bb614ace6f9b8
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 01/02/2019
ms.locfileid: "53913957"
---
# <a name="memory-management-time"></a>Speicherverwaltungszeit
Diese Segmente in der Zeitachse werden der Blockierung von Zeiten zugeordnet, die als Speicherverwaltungszeit kategorisiert sind. In einem solchen Szenario wird ein Thread durch ein Ereignis blockiert, das mit einem Speicherverwaltungsvorgang wie Paging in Verbindung steht. Während dieser Zeit wurde ein Thread in einem API- oder Kernelzustand blockiert, die die Parallelitätsschnellansicht als Speicherverwaltung erfasst. Diese schließen Ereignisse wie Paging und Speicherreservierung ein.  
  
 Überprüfen Sie die zugehörigen Aufruflisten und Profilberichte, um die Gründe für die Blöcke besser zu verstehen, die als Speicherverwaltung eingestuft werden.  
  
## <a name="see-also"></a>Siehe auch  
 [Threads View (Threadansicht)](../profiling/threads-view-parallel-performance.md)