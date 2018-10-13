---
title: 'DA0005: Häufige GC2-Auflistungen | Microsoft-Dokumentation'
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
- vs.performance.DA0005
- vs.performance.rules.DAManyGC2Collections
- vs.performance.5
- vs.performance.rules.DA0005
ms.assetid: 8d3f267c-8a74-4cf4-91a5-0b06a76dc2bd
caps.latest.revision: 16
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: ccbd030fe6f6ec48e37da22be896bd9fb3a5c8ab
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/12/2018
ms.locfileid: "49237717"
---
# <a name="da0005-frequent-gc2-collections"></a>DA0005: Häufige GC2-Auflistung
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

RuleId | DA0005 |  
| Kategorie |. NET Framework-Verwendung |  
| Profilerstellungsmethode |. NET-Speicher |  
| Nachricht | Viele Ihrer Objekte gesammelt werden, in die Garbagecollection der Generation 2. |  
| Nachrichtentyp | Warnung |  
  
## <a name="cause"></a>Ursache  
 Bei der Garbage Collection der Generation 2 wird eine hohe Anzahl von .NET-Speicherobjekten freigegeben.  
  
## <a name="rule-description"></a>Regelbeschreibung  
 Die Microsoft .NET-CLR (Common Language Runtime) verfügt über einen automatischen Speicherverwaltungsmechanismus, durch den der Speicher von Objekten, die von der Anwendung nicht mehr verwendet werden, mithilfe eines Garbage Collectors freigegeben wird. Der Garbage Collector ist generationsorientiert, da angenommen wird, dass viele Speicherbelegungen kurzlebig sind. Lokale Variablen müssen beispielsweise kurzlebig sein. Neu erstellte Objekte beginnen in Generation 0 (gen 0) und werden zu Generation 1, wenn sie nach einer Ausführung der Garbage Collection noch vorhanden sind, und schließlich zu Generation 2, wenn sie von der Anwendung auch weiterhin verwendet werden.  
  
 Objekte in der Generation 0 werden häufig und i. d. R. äußerst effizient gesammelt. Objekte in der Generation 1 werden nicht so häufig und weniger effizient gesammelt. Und langlebige Objekte in der Generation 2 werden schließlich noch seltener gesammelt. Die Collection der Generation 2, bei der es sich um eine vollständige Ausführung der Garbage Collection handelt, ist zudem der aufwändigste Vorgang.  
  
 Diese Regel wird ausgelöst, wenn anteilsmäßig zu viele Garbage Collections der zweiten Generation aufgetreten sind. Sind nach der Collection der ersten Generation zu viele relativ kurzlebige Objekte vorhanden, die dann aber im Rahmen einer vollständigen Collection der zweiten Generation gesammelt werden können, wird der Aufwand für die Speicherverwaltung unter Umständen zu groß. Weitere Informationen finden Sie im Beitrag [Mid-life crisis (Mid­life-Cri­sis)](http://go.microsoft.com/fwlink/?LinkId=177835) unter „Rico Mariani's Performance Tidbits“ (Schmankerln zum Thema Leistung von Rico Mariani) auf der MSDN-Website.  
  
## <a name="how-to-investigate-a-warning"></a>Vorgehensweise bei der Überprüfung einer Warnung  
 In den [.NET-Arbeitsspeicherdatenansichten](../profiling/dotnet-memory-data-views.md) finden Sie Informationen zum Speicherbelegungsmuster der Anwendung. Verwenden der [Objektlebensdaueransicht](../profiling/object-lifetime-view.md) um zu bestimmen, welche des Programms Datenobjekte in Generation 2 und von dort aus freigegeben werden. Ermitteln Sie mithilfe der [Zuordnungsansicht](../profiling/dotnet-memory-allocations-view.md) den Ausführungspfad, der zu diesen Speicherbelegungen geführt hat.  
  
 Informationen zur Verbesserung der Garbage Collection-Leistung finden Sie unter [Garbage Collector-Grundlagen und Tipps zur Leistung](http://go.microsoft.com/fwlink/?LinkId=148226) auf der Microsoft-Website. Informationen zum Mehraufwand der automatischen Garbage Collection finden Sie unter [Large Object Heap Uncovered (Informationen zum Heap für große Objekte)](http://go.microsoft.com/fwlink/?LinkId=177836).



