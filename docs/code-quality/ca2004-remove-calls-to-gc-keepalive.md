---
title: "CA2004: Aufrufe an GC.KeepAlive entfernen | Microsoft Docs"
ms.custom: ""
ms.date: "12/02/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "RemoveCallsToGCKeepAlive"
  - "CA2004"
helpviewer_keywords: 
  - "RemoveCallsToGCKeepAlive"
  - "CA2004"
ms.assetid: bc543b5b-23eb-4b45-abc2-9325cd254ac2
caps.latest.revision: 15
caps.handback.revision: 15
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# CA2004: Aufrufe an GC.KeepAlive entfernen
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|RemoveCallsToGCKeepAlive|  
|CheckId|CA2004|  
|Kategorie \(Category\)|Microsoft.Reliability|  
|Unterbrechende Änderung|Nicht unterbrechend|  
  
## Ursache  
 Klassen verwenden `SafeHandle`, enthalten jedoch trotzdem Aufrufe von `GC.KeepAlive`.  
  
## Regelbeschreibung  
 Wenn Sie zur Verwendung von `SafeHandle` wechseln, entfernen Sie alle Aufrufe von `GC.KeepAlive` \(Objekt\).  In diesem Fall sollten Klassen `GC.KeepAlive` nicht aufrufen müssen,  `` vorausgesetzt, sie weisen keinen Finalizer auf, sondern verwenden zum Beenden des Betriebssystemhandles `SafeHandle`.  Die Leistungseinbußen, die entstehen, wenn ein Aufruf von `GC.KeepAlive` nicht entfernt wird, sind zwar unwesentlich, wenn aber von der Annahme ausgegangen wird, ein Aufruf von `GC.KeepAlive` könnte erforderlich oder ausreichend sein, um ein möglicherweise gar nicht mehr bestehendes Lebensdauerproblem zu lösen, wird die Verwaltung des Codes erschwert.  
  
## Behandeln von Verstößen  
 Entfernen Sie Aufrufe von `GC.KeepAlive`.  
  
## Wann sollten Warnungen unterdrückt werden?  
 Sie können diese Warnung nur unterdrücken, wenn es technisch falsch ist, in einer Klasse zur Verwendung von `SafeHandle` zu wechseln.