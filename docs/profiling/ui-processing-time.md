---
title: Benutzeroberflächenverarbeitungszeit | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.cv.threads.timeline.uiprocessing
helpviewer_keywords:
- Concurrency Visualizer, UI Processing Time
ms.assetid: 0ddb05a3-8c6b-448b-8488-2751c1e5abcc
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 391b4582d03e32e738f0eade823326e72a662a43
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 03/18/2020
ms.locfileid: "63004448"
---
# <a name="ui-processing-time"></a>Benutzeroberflächenverarbeitungszeit
Diese Segmente in der Zeitachse werden den Blockierungszeiten zugeordnet, die als Benutzeroberflächenverarbeitungszeit kategorisiert sind. Das bedeutet, dass ein Thread Windows-Meldungen verteilt oder andere Vorgänge an der Benutzeroberfläche ausführt. Dabei wurde ein Thread in einer API blockiert, die die Parallelitätsschnellansicht als Benutzeroberflächenverarbeitung erfasst. APIs wie `GetMessage()` und `MsgWaitForMultipleObjects()` gehören zu dieser Gruppe.

 Wenn keine vordefinierte blockierende API erkannt wird, prüfen Sie die Aufruflisten und Profilberichte, um die Ursachen für die Verzögerung zu finden.

 Die Kategorie „Benutzeroberflächenverarbeitung“ ist hilfreich, wenn Sie die Reaktionsfähigkeit von GUI-Anwendungen nachvollziehen möchten, und wird für Anwendungen benötigt, die von der Reaktionsfähigkeit der Benutzeroberfläche abhängig sind. Wenn beispielsweise ein Benutzeroberflächenthread in einer Anwendung eine Zeit von 100 % bei der Benutzeroberflächenverarbeitung erreicht, deutet dies auf Reaktionsfähigkeit hin. Wenn allerdings der Benutzeroberflächenthread viel Zeit in anderen Kategorien verbringt, suchen Sie nach den Grundursachen, und ziehen Sie Optionen für die Reduzierung von Kategorien auf diesem Thread in Betracht, die sich nicht auf die Benutzeroberfläche beziehen.

## <a name="see-also"></a>Weitere Informationen
- [Threads View (Threadansicht)](../profiling/threads-view-parallel-performance.md)