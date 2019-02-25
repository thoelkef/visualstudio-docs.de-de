---
title: Speicherverwaltungszeit | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.cv.threads.timeline.paging
helpviewer_keywords:
- Concurrency Visualizer, Paging Time
ms.assetid: 67af3509-3a7d-435d-bc37-5262448da915
caps.latest.revision: 14
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 48cbdd523f4527af84c52366a439a18330e1828c
ms.sourcegitcommit: a83c60bb00bf95e6bea037f0e1b9696c64deda3c
ms.translationtype: MTE95
ms.contentlocale: de-DE
ms.lasthandoff: 02/19/2019
ms.locfileid: "54752060"
---
# <a name="memory-management-time"></a>Speicherverwaltungszeit
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Diese Segmente in der Zeitachse werden der Blockierung von Zeiten zugeordnet, die als Speicherverwaltungszeit kategorisiert sind. Das bedeutet, dass ein Thread durch ein Ereignis blockiert wird, das mit einem Speicherverwaltungsvorgang wie Paging in Verbindung steht. Während dieser Zeit wurde ein Thread in einem API- oder Kernelzustand blockiert, die die Parallelitätsschnellansicht als Speicherverwaltung erfasst. Diese schließen Ereignisse wie Paging und Speicherreservierung ein.  
  
 Überprüfen Sie die zugehörigen Aufruflisten und Profilberichte, um die Gründe für die Blöcke besser zu verstehen, die als Speicherverwaltung eingestuft werden.  
  
## <a name="see-also"></a>Siehe auch  
 [Threads View (Threadansicht)](../profiling/threads-view-parallel-performance.md)
