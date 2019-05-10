---
title: Benutzeroberflächenverarbeitungszeit | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.cv.threads.timeline.uiprocessing
helpviewer_keywords:
- Concurrency Visualizer, UI Processing Time
ms.assetid: 0ddb05a3-8c6b-448b-8488-2751c1e5abcc
caps.latest.revision: 10
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 4bbed9d8c4725b6bd497377d4a9dee22f2f8573d
ms.sourcegitcommit: a83c60bb00bf95e6bea037f0e1b9696c64deda3c
ms.translationtype: MTE95
ms.contentlocale: de-DE
ms.lasthandoff: 02/19/2019
ms.locfileid: "54783443"
---
# <a name="ui-processing-time"></a>Benutzeroberflächenverarbeitungszeit
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Diese Segmente in der Zeitachse werden den Blockierungszeiten zugeordnet, die als Benutzeroberflächenverarbeitungszeit kategorisiert sind. Das bedeutet, dass ein Thread Windows-Meldungen verteilt oder andere Vorgänge an der Benutzeroberfläche ausführt. Dabei wurde ein Thread in einer API blockiert, die die Parallelitätsschnellansicht als Benutzeroberflächenverarbeitung erfasst. APIs wie `GetMessage()` und `MsgWaitForMultipleObjects()` gehören zu dieser Gruppe.  
  
 Wenn keine vordefinierte blockierende API erkannt wird, prüfen Sie die Aufruflisten und Profilberichte, um die Ursachen für die Verzögerung zu finden.  
  
 Die Kategorie „Benutzeroberflächenverarbeitung“ ist wichtig, wenn Sie die Reaktionsfähigkeit von GUI-Anwendungen nachvollziehen möchten, und wird für Anwendungen benötigt, die von der Reaktionsfähigkeit der Benutzeroberfläche abhängig sind. Wenn beispielsweise ein Benutzeroberflächenthread in einer Anwendung eine Zeit von 100 % bei der Benutzeroberflächenverarbeitung erreicht, deutet dies auf eine hohe Reaktionsfähigkeit hin. Wenn allerdings der Benutzeroberflächenthread viel Zeit in anderen Kategorien verbringt, suchen Sie nach den Grundursachen, und ziehen Sie Optionen für die Reduzierung von Kategorien auf diesem Thread in Betracht, die sich nicht auf die Benutzeroberfläche beziehen.  
  
## <a name="see-also"></a>Siehe auch  
 [Threads View (Threadansicht)](../profiling/threads-view-parallel-performance.md)
