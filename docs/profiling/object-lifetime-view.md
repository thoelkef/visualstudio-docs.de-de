---
title: Objektlebensdaueransicht | Microsoft-Dokumentation
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: vs.performance.view.objectlifetime
helpviewer_keywords:
- lifetime, objects
- Objects Lifetime view
- profiling tools reports, Lifetime view
- performance reports, objects lifetime view
- profiling tools, Lifetime view
ms.assetid: d0501fdd-4b3a-4e74-b6ac-51d950a2e15b
caps.latest.revision: "24"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: b60a28d7422125a745cf1b088891b2675da0bc8a
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 10/31/2017
---
# <a name="object-lifetime-view"></a>Objektlebensdaueransicht
Die Objektlebensdaueransicht ist verfügbar, wenn **Lebensdauerinformationen für .NET-Objekt erfassen** auf der Eigenschaftenseite „Leistungssitzung“ aktiviert ist.  
  
 Der Garbage Collector von [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] verwaltet die Belegung und Freigabe von Arbeitsspeicher für die Anwendung. Zur Optimierung der Leistung des Garbage Collectors wird der verwaltete Heap in drei Generationen unterteilt: 0, 1 und 2. Vom Garbage Collector der Runtime werden neue Objekte in Generation 0 gespeichert. Objekte, die nach den Garbage Collections noch vorhanden sind, werden höhergestuft und in den Generationen 1 und 2 gespeichert.  
  
 Der Garbage Collector gibt Arbeitsspeicher frei, indem er eine ganze Generation von Objekten freigibt. Für Objekte, die von der profilierten Anwendung erstellt wurden, zeigt die Ansicht der Lebensdauer eines Objekts die Anzahl, die Größe und die Generation der Objekte an, in der diese freigegeben werden.  
  
## <a name="general"></a>Allgemein  
  
|Spalte|Beschreibung|  
|------------|-----------------|  
|**Klassenname**|Der Klassenname des zugeordneten Typs.|  
|**Prozess-ID**|Die Prozess-ID der Profilerstellung.|  
|**Prozessname**|Der Prozessname.|  
|**Modulname**|Der Name des Moduls, das die Funktion enthält.|  
|**Modulpfad**|Der Pfad des Moduls, das die Funktion enthält.|  
  
## <a name="instance-data"></a>Instanzdaten  
 Die Instanzdaten geben die Anzahl von Objekten des Typs an, die während der Profilerstellung erstellt wurden, sowie die Generation, in der die Objekte vom Garbage Collector freigegeben wurden.  
  
|Spalte|Beschreibung|  
|------------|-----------------|  
|**Instanzen**|Die Anzahl der Objektzuordnungen von diesem Typ.|  
|**Instanzen gesamt in Prozent**|Der Anteil der gesamten Zuordnungen, die während der Profilerstellung vorgenommen wurden.|  
|**Erfasste Instanzen in Generation 0**|Die Anzahl der Instanzen des Typs, die in Generation 0 des Garbage Collection-Algorithmus freigegeben wurden.|  
|**Erfasste Instanzen in Generation 1**|Die Anzahl der Instanzen des Typs, die in Generation 1 des Garbage Collection-Algorithmus freigegeben wurden.|  
|**Erfasste Instanzen in Generation 2**|Die Anzahl der Instanzen des Typs, die in Generation 2 des Garbage Collection-Algorithmus freigegeben wurden.|  
|**Aktive Instanzen am Ende**|Die Anzahl der Instanzen des Typs, die nicht vor dem Ende der Profilerstellung freigegeben wurden.|  
  
## <a name="size-byte-data"></a>Größendaten (Byte)  
 Die Größendaten (Byte) geben die Größe der Objekte des Typs an, die während der Profilerstellung erstellt wurden sowie die Menge des Arbeitsspeichers, die in jeder Generation freigegeben wurde, in der die Objekte freigegeben wurden.  
  
|Spalte|Beschreibung|  
|------------|-----------------|  
|**Zugeordnete Bytes insgesamt**|Die Gesamtanzahl von Bytes für alle Instanzen des Typs.|  
|**Bytes gesamt in Prozent**|Der Anteil der gesamten zugeordneten Bytes während der Profilerstellung, die Instanzen von diesem Typ zugeordnet wurden.|  
|**Erfasste Bytes in Generation 0**|Die Größe der Instanzen des Typs, die in Generation 0 des Garbage Collection-Algorithmus freigegeben wurden.|  
|**Erfasste Bytes in Generation 1**|Die Größe der Instanzen des Typs, die in Generation 1 des Garbage Collection-Algorithmus freigegeben wurden.|  
|**Erfasste Bytes in Generation 2**|Die Größe der Instanzen des Typs, die in Generation 2 des Garbage Collection-Algorithmus freigegeben wurden.|  
  
## <a name="large-object-heap-data"></a>Heapdaten für große Objekte  
 Die .NET-Speicherbelegungsfunktion verwaltet große Objekte an einem Speicherort, der vom standardmäßig verwalteten Heap getrennt ist. Heapdaten für große Objekte geben die Anzahl und Größe von Objekten des Typs an, die an diesem Speicherort verwaltet wurden.  
  
|Spalte|Beschreibung|  
|------------|-----------------|  
|**Erfasste Heapinstanzen für große Objekte**|Die Anzahl der Instanzen von diesem Typ, die sich im Heap für große Objekte befanden und während der Profilerstellung erfasst wurden.|  
|**Erfasste Heapbytes für große Objekte**|Die Größe der Instanzen von diesem Typ in Byte, die sich im Heap für große Objekte befanden und während der Profilerstellung erfasst wurden.|  
  
## <a name="see-also"></a>Siehe auch  
 [.NET-Arbeitsspeicherdatenansichten](../profiling/dotnet-memory-data-views.md)