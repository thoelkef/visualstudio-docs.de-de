---
title: "DA0011: Speicherintensive CompareTo-Funktionen | Microsoft Docs"
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
  - "vs.performance.DA0011"
  - "vs.performance.rules.DAExpensiveCompareTo"
  - "vs.performance.11"
  - "vs.performance.rules.DA0011"
ms.assetid: 239a381d-0d97-4367-8668-746c93f5af2c
caps.latest.revision: 9
caps.handback.revision: 9
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# DA0011: Speicherintensive CompareTo-Funktionen
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|Regel\-ID|DA0011|  
|Kategorie \(Category\)|.NET Framework\-Verwendung|  
|Profilerstellungsmethoden|Sampling<br /><br /> .NET\-Arbeitsspeicher|  
|Meldung|CompareTo\-Funktionen dürfen nicht speicherintensiv sein und keinen Speicher belegen.  Reduzieren Sie, sofern möglich, die Komplexität der CompareTo\-Funktionen.|  
|Regeltyp|Warnung|  
  
## Ursache  
 Die CompareTo\-Methode des Typs ist aufwändig oder belegt Speicher.  
  
## Regelbeschreibung  
 CompareTo\-Methoden sollten effizient sein und keinen Speicher belegen.  
  
## Behandeln von Verstößen  
 Reduzieren Sie die Komplexität der CompareTo\-Methode.