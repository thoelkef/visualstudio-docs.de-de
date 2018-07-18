---
title: Benutzeroberflächenverarbeitungszeit | Microsoft-Dokumentation
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.cv.threads.timeline.uiprocessing
helpviewer_keywords:
- Concurrency Visualizer, UI Processing Time
ms.assetid: 0ddb05a3-8c6b-448b-8488-2751c1e5abcc
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: ad48cd912bfdc117496bc9f876a1a2174e76dc04
ms.sourcegitcommit: 4cd4aef53e7035d23e7d1d0f66f51ac8480622a1
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 06/05/2018
ms.locfileid: "34477534"
---
# <a name="ui-processing-time"></a>Benutzeroberflächenverarbeitungszeit
Diese Segmente in der Zeitachse werden den Blockierungszeiten zugeordnet, die als Benutzeroberflächenverarbeitungszeit kategorisiert sind. Das bedeutet, dass ein Thread Windows-Meldungen verteilt oder andere Vorgänge an der Benutzeroberfläche ausführt. Dabei wurde ein Thread in einer API blockiert, die die Parallelitätsschnellansicht als Benutzeroberflächenverarbeitung erfasst. APIs wie `GetMessage()` und `MsgWaitForMultipleObjects()` gehören zu dieser Gruppe.  
  
 Wenn keine vordefinierte blockierende API erkannt wird, prüfen Sie die Aufruflisten und Profilberichte, um die Ursachen für die Verzögerung zu finden.  
  
 Die Kategorie „Benutzeroberflächenverarbeitung“ ist hilfreich, wenn Sie die Reaktionsfähigkeit von GUI-Anwendungen nachvollziehen möchten, und wird für Anwendungen benötigt, die von der Reaktionsfähigkeit der Benutzeroberfläche abhängig sind. Wenn beispielsweise ein Benutzeroberflächenthread in einer Anwendung eine Zeit von 100 % bei der Benutzeroberflächenverarbeitung erreicht, deutet dies auf Reaktionsfähigkeit hin. Wenn allerdings der Benutzeroberflächenthread viel Zeit in anderen Kategorien verbringt, suchen Sie nach den Grundursachen, und ziehen Sie Optionen für die Reduzierung von Kategorien auf diesem Thread in Betracht, die sich nicht auf die Benutzeroberfläche beziehen.  
  
## <a name="see-also"></a>Siehe auch  
 [Threads View (Threadansicht)](../profiling/threads-view-parallel-performance.md)