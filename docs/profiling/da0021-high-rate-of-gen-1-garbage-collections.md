---
title: "DA0021: Hohes Ma&#223; an Garbage Collections der Generation 1 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.performance.21"
  - "vs.performance.DA0021"
  - "vs.performance.rules.DA0021"
ms.assetid: ebf5d9b3-a1ac-4688-8f0f-39a85f4dd15f
caps.latest.revision: 9
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 9
---
# DA0021: Hohes Ma&#223; an Garbage Collections der Generation 1
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|Regel\-ID|DA0021|  
|Kategorie \(Category\)|.NET Framework\-Verwendung|  
|Profilerstellungsmethoden|Alle|  
|Meldung|Ein relativ hohes Maß an Garbage Collections der Generation 1 wurde festgestellt.  Ist ein Großteil der Programmdatenstrukturen entwurfsbedingt zugeordnet und für einen längeren Zeitraum gespeichert, stellt dies üblicherweise kein Problem dar.  Ist dieses Verhalten jedoch nicht beabsichtigt, werden von der Anwendung unter Umständen Objekte festgehalten.  Sollten Sie nicht sicher sein, sammeln Sie die .NET\-Speicherbelegungsdaten und die Informationen zur Objektlebensdauer, um das von der Anwendung verwendete Speicherbelegungsmuster nachzuvollziehen.|  
|Regeltyp|Information|  
  
 Wenn Sie mit der Sampling\-, .NET\-Arbeitsspeicher\- oder Ressourcenkonfliktmethode Profile erstellen, müssen mindestens 10 Samplings erfasst werden, damit diese Regel ausgelöst wird.  
  
## Ursache  
 Die bei der Profilerstellung erfassten Systemleistungsdaten deuten darauf hin, dass bei der Garbage Collection der Generation 1 \(im Vergleich zur Datensammlung der Generation 0\) ein großer Teil des Arbeitsspeichers für .NET Framework\-Objekte freigegeben wurde.  
  
## Regelbeschreibung  
 Die Microsoft .NET\-CLR \(Common Language Runtime\) verfügt über einen automatischen Speicherverwaltungsmechanismus, durch den der Speicher von Objekten, die von der Anwendung nicht mehr verwendet werden, mithilfe eines Garbage Collectors freigegeben wird.  Der Garbage Collector ist generationsorientiert, da angenommen wird, dass viele Speicherbelegungen kurzlebig sind.  Lokale Variablen müssen beispielsweise kurzlebig sein.  Neu erstellte Objekte beginnen in Generation 0 \(gen 0\) und werden zu Generation 1, wenn sie nach einer Ausführung der Garbage Collection noch vorhanden sind, und schließlich zu Generation 2, wenn sie von der Anwendung auch weiterhin verwendet werden.  
  
 Objekte in der Generation 0 werden häufig und i. d. R. äußerst effizient gesammelt.  Objekte in der Generation 1 werden nicht so häufig und weniger effizient gesammelt.  Und langlebige Objekte in der Generation 2 werden schließlich noch seltener gesammelt.  Die Collection der Generation 2, bei der es sich um eine vollständige Ausführung der Garbage Collection handelt, ist zudem der aufwändigste Vorgang.  
  
 Diese Regel wird ausgelöst, wenn anteilsmäßig zu viele Garbage Collections der Generation 1 aufgetreten sind.  Sind nach der Collection der Generation 0 zu viele relativ kurzlebige Objekte vorhanden, die dann aber im Rahmen einer Collection der Generation 1 gesammelt werden können, wird der Aufwand für die Speicherverwaltung unter Umständen zu groß.  Weitere Informationen finden Sie den [Lebensmittekrise](http://go.microsoft.com/fwlink/?LinkId=177835) Anteil des Leckerbissen der Leistung Rico Marianis auf der MSDN\-Website.  
  
## Vorgehensweise bei der Überprüfung einer Warnung  
 Doppelklicken Sie im Fenster Fehlerliste auf die Meldung, um zur [Markierungsansicht](../profiling/marks-view.md) der Profilerstellungsdaten zu navigieren.  Suchen Sie die Spalten **.NET CLR\-Speicher\\Auflistungsanzahl der Generation 0** und **.NET CLR\-Speicher\\Auflistungsanzahl der Generation 1**.  Ermitteln Sie, ob die Garbage Collection in bestimmten Phasen der Programmausführung besonders häufig auftritt.  Vergleichen Sie diese Werte mit den Werten der Spalte **GC\-Zeitdauer in Prozent**, um zu überprüfen, ob das Muster für verwaltete Speicherbelegungen einen übermäßig hohen Speicherverwaltungsaufwand verursacht.  
  
 Führen Sie eine erneute Profilerstellung unter Verwendung eines .NET\-Speicherbelegungsprofils aus, und fordern Sie Informationen zur Objektlebensdauer an, um das Muster für die verwaltete Speicherauslastung der Anwendung nachzuvollziehen.  
  
 Informationen darüber, wie der Garbage Collection\-Leistung, finden Sie auf [Garbage Collector\-Grundlagen und Leistungs\-Hinweise](http://go.microsoft.com/fwlink/?LinkId=148226) der Microsoft\-Website verbessert.  Informationen zum Mehraufwand der automatischen Garbage Collection, Sie finden. [Großes Objektheap zumindest teilweise nicht überdeckt](http://go.microsoft.com/fwlink/?LinkId=177836)