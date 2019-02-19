---
title: Ausführungsprofilbericht | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.cv.threads.report.execution
helpviewer_keywords:
- Concurrency Visualizer, Execution Profile Report
ms.assetid: c8128472-a8ed-46f4-b1c8-a25358d6f2c1
caps.latest.revision: 14
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: a0d95d4593939b878194d2aeef79bdd0a8ad946a
ms.sourcegitcommit: a83c60bb00bf95e6bea037f0e1b9696c64deda3c
ms.translationtype: MTE95
ms.contentlocale: de-DE
ms.lasthandoff: 02/19/2019
ms.locfileid: "54756516"
---
# <a name="execution-profile-report"></a>Ausführungsprofilbericht
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Der Ausführungsprofilbericht ist ein herkömmliches Samplingprofil. Samplings werden etwa jede Millisekunde während der Zeiträume genommen, in denen ein Thread auf einem logischen Kern ausgeführt wird. Die Parallelitätsschnellansicht erstellt durch Sortieren des akkumulierten Satzes von Samplingstapeln eine typische Aufrufstruktur. Die Daten in dieser Tabelle sind vom aktuellem Zeitraum und ausgeblendeten Threads, sowie von den möglicherweise angewendeten Filtern abhängig:  
  
- Wenn „Nur eigenen Code“ ausgewählt ist, werden nur Stapelrahmen mit Benutzercode, sowie die Ebene direkt unter dem Benutzercode angezeigt.  
  
- Wenn der Wert „Rauschunterdrückung“ festgelegt ist, werden sortierte Stapel mit einer geringeren als der angegebenen Frequenz aus dem Bericht gefiltert.  
  
  Die folgende Tabelle zeigt die Spalten im Bericht.  
  
|Spalte|Beschreibung|  
|------------|-----------------|  
|name|Der Name der Funktion für die einzelnen Ebenen der Aufrufliste.|  
|Inklusive Samplings|Die Gesamtzahl von Samplings, die für alle Stapel erfasst werden, die diese Ebene der Aufruflistenstruktur bilden. Die inklusive Anzahl ist die Summe der exklusiven Samplings für diese Funktion und der inklusiven Anzahl für alle untergeordneten Knoten.|  
|Exklusive Stichproben|Die Gesamtzahl erfasster Samplings, für die diese Funktion die niedrigste Ebene der Aufrufliste bildet.|  
|% inklusive|Der Prozentsatz der gesamten Samplings, die in der Spalte für inklusive Samplings angezeigt werden. Prozentsätze werden auf zwei Dezimalstellen gerundet.|  
|% exklusive|Der Prozentsatz der gesamten Samplings, die in der Spalte für exklusive Samplings angezeigt werden. Prozentsätze werden auf zwei Dezimalstellen gerundet.|  
|Details|Der vollqualifizierte Name der Funktion. Darin eingeschlossen ist die Zeilenanzahl, sofern verfügbar.|  
  
 Diese Berichtstabelle kann in der Ansicht [Ausführungszeit (Threadansicht)](../profiling/execution-time-threads-view.md) angezeigt werden.  
  
## <a name="see-also"></a>Siehe auch  
 [Threads View (Threadansicht)](../profiling/threads-view-parallel-performance.md)
