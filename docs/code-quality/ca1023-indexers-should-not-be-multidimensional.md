---
title: "CA1023: Indexer sollten nicht mehrdimensional sein | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IndexersShouldNotBeMultidimensional"
  - "CA1023"
helpviewer_keywords: 
  - "CA1023"
  - "IndexersShouldNotBeMultidimensional"
ms.assetid: ae499879-97f6-434e-a61d-1fedd231d2fb
caps.latest.revision: 14
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
caps.handback.revision: 14
---
# CA1023: Indexer sollten nicht mehrdimensional sein
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|IndexersShouldNotBeMultidimensional|  
|CheckId|CA1023|  
|Kategorie \(Category\)|Microsoft.Design|  
|Unterbrechende Änderung|Breaking|  
  
## Ursache  
 Ein öffentlicher oder geschützter Typ enthält einen öffentlichen oder geschützten Indexer, der mehrere Indizes verwendet.  
  
## Regelbeschreibung  
 Indexer, d. h. indizierte Eigenschaften, sollten einen einzelnen Index verwenden.  Wegen mehrdimensionaler Indexer kann die Verwendbarkeit der Bibliothek deutlich abnehmen.  Wenn der Entwurf mehrere Indizes erfordert, sollten Sie erneut prüfen, ob es sich bei dem Typ um einen logischen Datenspeicher handelt.  Wenn dies nicht der Fall ist, verwenden Sie eine Methode.  
  
## Behandeln von Verstößen  
 Um einen Verstoß gegen diese Regel zu beheben, ändern Sie den Entwurf, sodass nur ein Ganzzahl\- oder Zeichenfolgenindex verwendet wird, oder verwenden Sie anstelle des Indexers eine Methode.  
  
## Wann sollten Warnungen unterdrückt werden?  
 Unterdrücken Sie eine Warnung dieser Regel erst, nachdem Sie den Bedarf für einen nicht dem Standard entsprechenden Indexer sorgfältig geprüft haben.  
  
## Beispiel  
 Das folgende Beispiel zeigt einen Typ \(`DayOfWeek03`\) mit einem mehrdimensionalen Indexer, der gegen die Regel verstößt.  Der Indexer fungiert als eine Art Konvertierung und sollte daher eher als Methode zur Verfügung gestellt werden.  Der Typ wird in `RedesignedDayOfWeek03` so umgestaltet, dass er der Regel entspricht.  
  
 [!code-vb[FxCop.Design.OneDimensionForIndexer#1](../code-quality/codesnippet/VisualBasic/ca1023-indexers-should-not-be-multidimensional_1.vb)]
 [!code-cpp[FxCop.Design.OneDimensionForIndexer#1](../code-quality/codesnippet/CPP/ca1023-indexers-should-not-be-multidimensional_1.cpp)]
 [!code-cs[FxCop.Design.OneDimensionForIndexer#1](../code-quality/codesnippet/CSharp/ca1023-indexers-should-not-be-multidimensional_1.cs)]  
  
## Verwandte Regeln  
 [CA1043: Ganzzahliges Argument oder Zeichenfolgenargument für Indexer verwenden](../code-quality/ca1043-use-integral-or-string-argument-for-indexers.md)  
  
 [CA1024: Nach Möglichkeit Eigenschaften verwenden](../code-quality/ca1024-use-properties-where-appropriate.md)