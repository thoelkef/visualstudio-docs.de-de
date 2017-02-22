---
title: "Datenwerte zur Speicherbelegung und Objektlebensdauer in den Profilerstellungstools | Microsoft Docs"
ms.custom: ""
ms.date: "12/16/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - ".NET-Arbeitsspeicher-Profilerstellungsmethode"
  - "Profilerstellungstools, .NET-Arbeitsspeichermethode"
ms.assetid: a22445b3-39a6-4919-8506-2b5b0ceaf77e
caps.latest.revision: 11
caps.handback.revision: 11
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# Datenwerte zur Speicherbelegung und Objektlebensdauer in den Profilerstellungstools
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Die Profilerstellungsmethode.NET\-Speicherbelegung der [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] \- Profilerstellungstools sammelt Informationen zur Größe und Anzahl von Objekten, die in einer Zuordnung erstellt oder bei einer Garbage Collection sowie weitere Informationen zur Funktion zerstört, als das Ereignis aufgetreten ist.  Eine *Aufrufliste* ist eine dynamische Struktur, die Informationen über die Funktionen speichert, die auf dem Prozessor ausgeführt werden.  
  
 **Voraussetzungen**  
  
-   [!INCLUDE[vsUltLong](../code-quality/includes/vsultlong_md.md)], [!INCLUDE[vsPreLong](../code-quality/includes/vsprelong_md.md)], [!INCLUDE[vsPro](../code-quality/includes/vspro_md.md)]  
  
 Der Arbeitsspeicher\-Profiler unterbricht den Computerprozessor bei jeder Zuordnung eines .NET Framework\-Objekts in einer profilierten Anwendung.  Wenn auch Objektlebensdauerdaten erfasst werden, unterbricht der Profiler den Prozessor nach jeder .NET Framework\-Garbage Collection.  Die Daten werden für jede profilierte Funktion und jeden Objekttyp aggregiert.  
  
## Zuordnungsdaten  
 Wenn ein Speicherereignis auftritt, werden die Gesamtzahlen und Größen der zugeordneten oder zerstörten Speicherobjekte erhöht.  
  
 Wenn ein Speicherbelegungsereignis auftritt, erhöht der Profiler die Samplinganzahl für jede Funktion der Aufrufliste.  Wenn die Daten erfasst werden, führt nur eine Funktion auf der Aufrufliste den Code gerade in ihrem Funktionsrumpf aus.  Die anderen Funktionen in der Liste sind übergeordnete Elemente in der Hierarchie von Funktionsaufrufen, die auf den Abschluss der Funktionen warten, die sie aufgerufen haben.  
  
-   Für das Zuordnungsereignis erhöht der Profiler die *exklusive* Samplinganzahl der Funktion, die ihre Anweisungen gerade ausführt.  Da ein exklusives Sampling auch Teil der gesamten \(*inklusiven*\) Samplings für die Funktion ist, wird die inklusive Samplinganzahl der aktuell aktiven Funktion auch erhöht.  
  
-   Der Profiler inkrementiert die inklusive Samplinganzahl aller anderen Funktionen in der Aufrufliste.  
  
## Lebensdauerdaten  
 Der Garbage Collector von .NET Framework verwaltet die Belegung und Freigabe von Arbeitsspeicher für die Anwendung.  Zur Optimierung der Leistung des Garbage Collectors wird der verwaltete Heap in drei Generationen unterteilt: 0, 1 und 2.  Vom Garbage Collector der Laufzeit werden neue Objekte in Generation 0 gespeichert.  Objekte, die nach den Garbage Collections noch vorhanden sind, werden höher gestuft und in den Generationen 1 und 2 gespeichert.  
  
 Der Garbage Collector gibt Arbeitsspeicher frei, indem er eine ganze Generation von Objekten freigibt.  Für die von der profilierten Anwendung erstellten Objekte werden in der Objektlebensdaueransicht die Zahl und die Größe der Objekte sowie die Generation angezeigt, in der die Objekte freigegeben werden.