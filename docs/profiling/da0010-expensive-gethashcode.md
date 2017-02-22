---
title: "DA0010: Speicherintensive GetHashCode-Funktionen | Microsoft Docs"
ms.custom: ""
ms.date: "12/02/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.performance.rules.DAExpensiveGetHashCode"
  - "vs.performance.DA0010"
  - "vs.performance.rules.DA0010"
  - "vs.performance.10"
ms.assetid: 3987e21a-5b4f-45e4-8a33-6b3f0a472c08
caps.latest.revision: 11
caps.handback.revision: 11
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# DA0010: Speicherintensive GetHashCode-Funktionen
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|Regel\-ID|DA0010|  
|Kategorie \(Category\)|.NET Framework\-Verwendung|  
|Profilerstellungsmethoden|Sampling<br /><br /> .NET\-Arbeitsspeicher|  
|Meldung|GetHashCode\-Funktionen dürfen nicht speicherintensiv sein und keinen Speicher belegen.  Reduzieren Sie, sofern möglich, die Komplexität der Hashcodefunktionen.|  
|Meldungstyp|Warnung|  
  
## Ursache  
 Aufrufe der GetHashCode\-Methode des Typs machen einen großen Teil der Profilerstellungsdaten aus, oder von der Methode wird Arbeitsspeicher belegt.  
  
## Regelbeschreibung  
 Hashverfahren ist eine Technik zum schnellen Suchen eines bestimmten Elements in einer großen Auflistung.  Da Hashtabellen sehr groß sein können und sehr hohe Zugriffsraten unterstützen müssen, sollten Hashtabellen äußerst effizient sein.  Eine Folge dieser Anforderung ist, dass GetHashCode\-Methoden in .NET Framework keinen Speicher belegen sollten.  Das Zuordnen von Arbeitsspeicher erhöht die Last für den Garbage Collector und macht die Methode verfügbar für potenzielle Verzögerungen, wenn es notwendig wird, eine Garbage Collection als Ergebnis der Zuordnungsanforderung auszuführen.  
  
## Behandeln von Verstößen  
 Verringern Sie die Komplexität der Methode.