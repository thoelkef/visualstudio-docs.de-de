---
title: 'DA0023: Hohe GC-CPU-Zeit | Microsoft-Dokumentation'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
f1_keywords:
- vs.performance.DA0023
- vs.performance.23
- vs.performance.rules.DA0023
ms.assetid: aba875fe-9cbc-418d-a2c4-6eb47519a5bb
caps.latest.revision: 15
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: bf5e841fdccbd6a41d0e7ee61c9f5278c6a882e3
ms.sourcegitcommit: da5ebc29544fdbdf625ab4922c9777faf2bcae4a
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/29/2020
ms.locfileid: "82586866"
---
# <a name="da0023-high-gc-cpu-time"></a>DA0023: Hohe GC-CPU-Zeit
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||  
|-|-|  
|Regel-ID|DA0023|  
|Kategorie|.NET Framework-Verwendung|  
|Profilerstellungsmethode|Alle|  
|Nachricht|Die GC-Zeitdauer in Prozent ist relativ hoch. Dies ist ein Hinweis auf einen sehr hohen Mehraufwand für die Garbage Collection, der sich möglicherweise auf die Reaktionsfähigkeit Ihrer Anwendung auswirkt. Sammeln Sie die .NET-Speicherbelegungsdaten und die Informationen zur Objektlebensdauer, um besser nachvollziehen zu können, welches Speicherbelegungsmuster von der Anwendung verwendet wird.|  
|Regeltyp|Information|  
  
 Wenn Sie Profile mithilfe der Sampling-, .NET-Arbeitsspeicher- oder Ressourcenkonfliktmethode Profile erstellen, müssen mindestens 10 Samplings erfasst werden, damit diese Regel ausgelöst wird.  
  
## <a name="cause"></a>Ursache  
 Die bei der Profilerstellung erfassten Systemleistungsdaten deuten darauf hin, dass für die Garbage Collection im Vergleich zur gesamten Anwendungsverarbeitung viel Zeit aufgewendet wird.  
  
## <a name="rule-description"></a>Regelbeschreibung  
 Die Microsoft .NET-CLR (Common Language Runtime) verfügt über einen automatischen Speicherverwaltungsmechanismus, durch den der Speicher von Objekten, die von der Anwendung nicht mehr verwendet werden, mithilfe eines Garbage Collectors freigegeben wird. Der Garbage Collector ist generationsorientiert, da angenommen wird, dass viele Speicherbelegungen kurzlebig sind. Lokale Variablen müssen beispielsweise kurzlebig sein. Neu erstellte Objekte beginnen in Generation 0 (gen 0) und werden zu Generation 1, wenn sie nach einer Ausführung der Garbage Collection noch vorhanden sind, und schließlich zu Generation 2, wenn sie von der Anwendung auch weiterhin verwendet werden.  
  
 Objekte in der Generation 0 werden häufig und i. d. R. äußerst effizient gesammelt. Objekte in der Generation 1 werden nicht so häufig und weniger effizient gesammelt. Und langlebige Objekte in der Generation 2 werden schließlich noch seltener gesammelt. Die Collection der Generation 2, bei der es sich um eine vollständige Ausführung der Garbage Collection handelt, ist zudem der aufwändigste Vorgang.  
  
 Diese Regel wird ausgelöst, wenn für die Garbage Collection im Vergleich zur gesamten Anwendungsverarbeitung viel Zeit aufgewendet wird.  
  
> [!NOTE]
> Wenn für die Garbage Collection im Vergleich zur gesamten Anwendungsverarbeitung übermäßig viel Zeit aufgewendet wird, wird anstelle dieser Regel die Warnung [DA0024: Übermäßige GC-CPU-Zeit](../profiling/da0024-excessive-gc-cpu-time.md) ausgelöst.  
  
## <a name="how-to-investigate-a-warning"></a>Vorgehensweise bei der Überprüfung einer Warnung  
 Doppelklicken Sie auf die Meldung im Fenster „Fehlerliste“, um zur Ansicht [Markierungen](../profiling/marks-view.md) der Profilerstellungsdaten zu navigieren. Suchen Sie die Spalte **.NET CLR-Speicher\\GC-Zeitdauer in Prozent**. Überprüfen Sie, ob der Mehraufwand für die Garbage Collection bei verwaltetem Speicher in bestimmten Phasen der Programmausführung besonders häufig auftritt. Vergleichen Sie die Werte der Spalte „GC-Zeitdauer in Prozent“ mit der Garbage Collection-Rate aus den Spalten **Auflistungsanzahl der Generation 0**, **Auflistungsanzahl der Generation 1** und **Auflistungsanzahl der Generation 2**.  
  
 Die Werte der Spalte „GC-Zeitdauer in Prozent“ geben an, wie viel Zeit von einer Anwendung für die Garbage Collection im Vergleich zur Gesamtverarbeitungszeit aufgewendet wird. In einigen Situationen kann der Wert für die GC-Zeitdauer in Prozent sehr hoch sein, ohne dass dies auf eine übermäßige Garbage Collection zurückzuführen ist. Weitere Informationen zur Berechnung des Werts für die GC-Zeitdauer in Prozent finden Sie im Beitrag [Difference Between Perf Data Reported by Different Tools – 4 (Unterschied zwischen Leistungsdaten unterschiedlicher Tools – 4)](https://devblogs.microsoft.com/dotnet/difference-between-perf-data-reported-by-different-tools-4/) in **Maoni's Weblog** auf MSDN. Treten Seitenfehler auf oder wird die Anwendung aufgrund von Aufgaben mit höherer Priorität auf dem Computer vorzeitig entfernt, werden diese zusätzlichen Verzögerungen bei der Berechnung des Werts für die GC-Zeitdauer in Prozent berücksichtigt.
