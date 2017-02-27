---
title: "CA2219: Keine Ausnahmen in Ausnahmeklauseln ausl&#246;sen | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "DoNotRaiseExceptionsInExceptionClauses"
  - "CA2219"
helpviewer_keywords: 
  - "CA2219"
  - "DoNotRaiseExceptionsInExceptionClauses"
ms.assetid: 7b9b0bee-4e8e-49a4-8c40-52142b49061f
caps.latest.revision: 5
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
caps.handback.revision: 5
---
# CA2219: Keine Ausnahmen in Ausnahmeklauseln ausl&#246;sen
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|DoNotRaiseExceptionsInExceptionClauses|  
|CheckId|CA2219|  
|Kategorie \(Category\)|Microsoft.Usage|  
|Unterbrechende Änderung|Nicht unterbrechend, unterbrechend|  
  
## Ursache  
 Von `finally`, einem Filter oder einer fault\-Klausel wird eine Ausnahme ausgelöst.  
  
## Regelbeschreibung  
 Wenn eine Ausnahme in einer Ausnahmeklausel ausgelöst wird, wird das Debuggen deutlich erschwert.  
  
 Wenn eine Ausnahme in einer `finally`\- oder fault\-Klausel ausgelöst wird, wird die aktive Ausnahme, falls vorhanden, von der neuen Ausnahme verdeckt.  Dadurch ist der ursprüngliche Fehler nur schwer zu erkennen und zu debuggen.  
  
 Wenn in einer Filterklausel eine Ausnahme ausgelöst wird, wird die Ausnahme durch die Laufzeit automatisch abgefangen, wodurch der Filter mit false ausgewertet wird.  Es kann nicht unterschieden werden, ob der Filter mit false ausgewertet wird oder ob eine Ausnahme von einem Filter ausgelöst wurde.  Dadurch können Fehler in der Filterlogik nur schwer ermittelt und debuggt werden.  
  
## Behandeln von Verstößen  
 Um diesen Verstoß gegen diese Regel zu beheben, lösen Sie keine explizite Ausnahme von `finally`, einem Filter oder einer fault\-Klausel aus.  
  
## Wann sollten Warnungen unterdrückt werden?  
 Unterdrücken Sie keine Warnung dieser Regel.  Es gibt keine Szenarien, in denen eine durch eine Ausnahmeklausel ausgelöste Ausnahme einen Vorteil gegenüber dem ausführenden Code darstellt.  
  
## Verwandte Regeln  
 [CA1065: Keine Ausnahmen an unerwarteten Speicherorten auslösen](../code-quality/ca1065-do-not-raise-exceptions-in-unexpected-locations.md)  
  
## Siehe auch  
 [Entwurfswarnungen](../code-quality/design-warnings.md)