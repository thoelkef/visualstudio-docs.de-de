---
title: Benutzeroberflächenverarbeitungszeit | Microsoft-Dokumentation
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
- vs.cv.threads.timeline.uiprocessing
helpviewer_keywords:
- Concurrency Visualizer, UI Processing Time
ms.assetid: 0ddb05a3-8c6b-448b-8488-2751c1e5abcc
caps.latest.revision: 10
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 7e35f5f37b0eced2822cb4b019732210bec94495
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/22/2018
ms.locfileid: "47522023"
---
# <a name="ui-processing-time"></a>Benutzeroberflächenverarbeitungszeit
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Die neueste Version dieses Themas finden Sie unter [Benutzeroberflächenverarbeitungszeit](https://docs.microsoft.com/visualstudio/profiling/ui-processing-time).  
  
Diese Segmente in der Zeitachse werden den Blockierungszeiten zugeordnet, die als Benutzeroberflächenverarbeitungszeit kategorisiert sind. Das bedeutet, dass ein Thread Windows-Meldungen verteilt oder andere Vorgänge an der Benutzeroberfläche ausführt. Dabei wurde ein Thread in einer API blockiert, die die Parallelitätsschnellansicht als Benutzeroberflächenverarbeitung erfasst. APIs wie `GetMessage()` und `MsgWaitForMultipleObjects()` gehören zu dieser Gruppe.  
  
 Wenn keine vordefinierte blockierende API erkannt wird, prüfen Sie die Aufruflisten und Profilberichte, um die Ursachen für die Verzögerung zu finden.  
  
 Die Kategorie „Benutzeroberflächenverarbeitung“ ist wichtig, wenn Sie die Reaktionsfähigkeit von GUI-Anwendungen nachvollziehen möchten, und wird für Anwendungen benötigt, die von der Reaktionsfähigkeit der Benutzeroberfläche abhängig sind. Wenn beispielsweise ein Benutzeroberflächenthread in einer Anwendung eine Zeit von 100 % bei der Benutzeroberflächenverarbeitung erreicht, deutet dies auf eine hohe Reaktionsfähigkeit hin. Wenn allerdings der Benutzeroberflächenthread viel Zeit in anderen Kategorien verbringt, suchen Sie nach den Grundursachen, und ziehen Sie Optionen für die Reduzierung von Kategorien auf diesem Thread in Betracht, die sich nicht auf die Benutzeroberfläche beziehen.  
  
## <a name="see-also"></a>Siehe auch  
 [Threads View (Threadansicht)](../profiling/threads-view-parallel-performance.md)



