---
title: "CA1722: Bezeichner sollten kein falsches Pr&#228;fix aufweisen | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IdentifiersShouldNotHaveIncorrectPrefix"
  - "CA1722"
helpviewer_keywords: 
  - "CA1722"
  - "IdentifiersShouldNotHaveIncorrectPrefix"
ms.assetid: c3313c51-d004-4f9a-a0d1-6c4c4a1fb1e6
caps.latest.revision: 16
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
caps.handback.revision: 16
---
# CA1722: Bezeichner sollten kein falsches Pr&#228;fix aufweisen
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|IdentifiersShouldNotHaveIncorrectPrefix|  
|CheckId|CA1722|  
|Kategorie \(Category\)|Microsoft.Naming|  
|Unterbrechende Änderung|Breaking|  
  
## Ursache  
 Ein Bezeichner hat ein falsches Präfix.  
  
## Regelbeschreibung  
 Gemäß der Konvention verfügen nur bestimmte Programmierelemente über Namen, die mit einem bestimmten Präfix anfangen.  
  
 Typnamen haben kein bestimmtes Präfix und sollten nicht mit dem Präfix "C" beginnen.  Diese Regel meldet Verstöße durch Typnamen wie "CMyClass". Typnamen wie "Cache" werden nicht als Regelverstoß gewertet.  
  
 Durch Benennungskonventionen erhalten Bibliotheken, die auf die Common Language Runtime abzielen, ein einheitliches Erscheinungsbild.  Dadurch wird der Lernaufwand für neue Softwarebibliotheken verringert. Zudem wird das Kundenvertrauen dahingehend gestärkt, dass die Bibliothek von einem erfahrenen Entwickler für verwalteten Code erstellt wurde.  
  
## Behandeln von Verstößen  
 Entfernen Sie das Präfix aus dem Bezeichner.  
  
## Wann sollten Warnungen unterdrückt werden?  
 Unterdrücken Sie keine Warnung dieser Regel.  
  
## Verwandte Regeln  
 [CA1715: Bezeichner sollten ein korrektes Präfix aufweisen](../code-quality/ca1715-identifiers-should-have-correct-prefix.md)