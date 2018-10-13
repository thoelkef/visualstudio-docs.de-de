---
title: 'DA0022: Hohes Maß an Garbage Collections der Generation 2 | Microsoft-Dokumentation'
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
- vs.performance.DA0022
- vs.performance.rules.DA0022
- vs.performance.22
ms.assetid: f871a547-0e6f-4b11-b2d7-174d30fc2ed8
caps.latest.revision: 13
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 270f2b90894c1dc7ede8f45c34c1e4c542fae56a
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/12/2018
ms.locfileid: "49200394"
---
# <a name="da0022-high-rate-of-gen-2-garbage-collections"></a>DA0022: Hohes Maß an Garbage Collections der Generation 2
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Regel-Id | DA0022 |  
| Kategorie |. NET Framework-Verwendung |  
| Profilerstellungsmethode | Alle |  
| Nachricht | Es ist ein relativ hohes Maß an Garbage Collections der Generation 2 ausgeführt. Ist ein Großteil der Programmdatenstrukturen entwurfsbedingt zugeordnet und für einen längeren Zeitraum gespeichert, stellt dies üblicherweise kein Problem dar. Ist dieses Verhalten jedoch nicht beabsichtigt, werden von der Anwendung unter Umständen Objekte festgehalten. Wenn Sie nicht sicher sind, können Sie sammeln, .NET-Speicherbelegungsdaten und Lebensdauerinformationen um das Muster der speicherbelegung zu verstehen, die Anwendung verwendet. |  
| Regeltyp | Warnung |  
  
 Wenn Sie Profile mithilfe der Sampling-, .NET-Arbeitsspeicher- oder Ressourcenkonfliktmethode Profile erstellen, müssen mindestens 10 Samplings erfasst werden, damit diese Regel ausgelöst wird.  
  
## <a name="cause"></a>Ursache  
 Die bei der Profilerstellung erfassten Systemleistungsdaten deuten darauf hin, dass bei der Garbage Collection der Generation 2 (im Vergleich zu den Garbage Collections der Generationen 0 und 1) ein großer Teil des Arbeitsspeichers für .NET Framework-Objekte freigegeben wurde.  
  
## <a name="rule-description"></a>Regelbeschreibung  
 Die Microsoft .NET-CLR (Common Language Runtime) verfügt über einen automatischen Speicherverwaltungsmechanismus, durch den der Speicher von Objekten, die von der Anwendung nicht mehr verwendet werden, mithilfe eines Garbage Collectors freigegeben wird. Der Garbage Collector ist generationsorientiert, da angenommen wird, dass viele Speicherbelegungen kurzlebig sind. Lokale Variablen müssen beispielsweise kurzlebig sein. Neu erstellte Objekte beginnen in Generation 0 (gen 0) und werden zu Generation 1, wenn sie nach einer Ausführung der Garbage Collection noch vorhanden sind, und schließlich zu Generation 2, wenn sie von der Anwendung auch weiterhin verwendet werden.  
  
 Objekte in der Generation 0 werden häufig und i. d. R. äußerst effizient gesammelt. Objekte in der Generation 1 werden nicht so häufig und weniger effizient gesammelt. Und langlebige Objekte in der Generation 2 werden schließlich noch seltener gesammelt. Die Collection der Generation 2, bei der es sich um eine vollständige Ausführung der Garbage Collection handelt, ist zudem der aufwändigste Vorgang.  
  
 Diese Regel wird ausgelöst, wenn anteilsmäßig zu viele Garbage Collections der Generation 2 aufgetreten sind. Bei gut konzipierten .NET Framework-Anwendungen findet die Garbage Collection der Generation 1 mehr als fünfmal so häufig statt wie die Garbage Collection der Generation 2. (Der Faktor "10" ist wohl ideal.)  
  
## <a name="how-to-investigate-a-warning"></a>Vorgehensweise bei der Überprüfung einer Warnung  
 Doppelklicken Sie auf die Meldung im Fenster „Fehlerliste“, um zur Ansicht [Markierungen](../profiling/marks-view.md) der Profilerstellungsdaten zu navigieren. Suchen Sie die Spalten **.NET CLR-Speicher\\Auflistungsanzahl der Generation 0** und **.NET CLR-Speicher\\Auflistungsanzahl der Generation 1**. Überprüfen Sie, ob die Garbage Collection in bestimmten Phasen der Programmausführung besonders häufig auftritt. Vergleichen Sie diese Werte mit den Werten der Spalte **GC-Zeitdauer in Prozent**, um zu überprüfen, ob das Muster für verwaltete Speicherbelegungen einen übermäßig hohen Speicherverwaltungsaufwand verursacht.  
  
 Ein hoher Anteil an Garbage Collections der Generation 2 muss nicht unbedingt ein Problem darstellen. Dies kann auch durch den Entwurf bedingt sein. Diese Regel kann durch eine Anwendung ausgelöst werden, von der große Datenstrukturen zugeordnet werden, die während der Ausführung lange aktiv bleiben müssen. Wenn für eine solche Anwendung nicht genügend Arbeitsspeicher zur Verfügung steht, müssen unter Umständen häufig Garbage Collections ausgeführt werden. Wenn durch die weniger aufwändigen Garbage Collections der Generationen 0 und 1 nur ein kleiner Teil des verwalteten Arbeitsspeichers freigegeben werden kann, werden Garbage Collections der Generation 2 in kürzeren Abständen geplant.  
  
 Die Markierungsansicht enthält zusätzliche Spalten vom Typ „.NET CLR-Speicher“, die zum Identifizieren von Problemen mit der Garbage Collection verwendet werden können. Die Spalte **GC-Zeitdauer in Prozent** gibt Aufschluss über den Umfang des Mehraufwands für die Speicherverwaltung. Wenn von der Anwendung üblicherweise eine relativ geringe Anzahl großer, aber permanenter Objekte verwendet wird, dürfen häufig ausgeführte Garbage Collections der Generation 2 nicht übermäßig viel CPU-Zeit benötigen. Steht für die Anwendung nicht genügend Arbeitsspeicher zur Verfügung, da mehr physischer Speicher (RAM) benötigt wird, werden unter Umständen auch ähnliche Regeln ausgelöst, von denen die Werte der Spalte **Arbeitsspeicher\Seiten/s** ausgewertet werden.  
  
 Wiederholen Sie die Profilerstellung für die Anwendung mithilfe eines .NET-Speicherbelegungsprofils, und wählen Sie die Profilerstellungsoption „Objektlebensdauer“ aus, damit Sie das Muster für die verwaltete Speicherauslastung der Anwendung nachvollziehen können.  
  
 Informationen zur Verbesserung der Garbage Collection-Leistung finden Sie unter [Garbage Collector-Grundlagen und Tipps zur Leistung](http://go.microsoft.com/fwlink/?LinkId=148226) auf der Microsoft-Website. Informationen zum Mehraufwand der automatischen Garbage Collection finden Sie unter [Large Object Heap Uncovered (Informationen zum Heap für große Objekte)](http://go.microsoft.com/fwlink/?LinkId=177836).



