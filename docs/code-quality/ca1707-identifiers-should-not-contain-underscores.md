---
title: "CA1707: Bezeichner sollten keine Unterstriche enthalten | Microsoft Docs"
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
  - "IdentifiersShouldNotContainUnderscores"
  - "CA1707"
helpviewer_keywords: 
  - "CA1707"
  - "IdentifiersShouldNotContainUnderscores"
ms.assetid: 5fb539ef-c304-4323-90c0-b14386da9774
caps.latest.revision: 19
caps.handback.revision: 19
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# CA1707: Bezeichner sollten keine Unterstriche enthalten
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|IdentifiersShouldNotContainUnderscores|  
|CheckId|CA1707|  
|Kategorie \(Category\)|Microsoft.Naming|  
|Unterbrechende Änderung|Unterbrechend – Wenn für Assemblys ausgelöst<br /><br /> Nicht unterbrechend – Wenn für Typparameter ausgelöst|  
  
## Ursache  
 Der Name eines Bezeichners enthält einen Unterstrich \(\_\).  
  
## Regelbeschreibung  
 Bezeichnernamen dürfen keinen Unterstrich \(\_\) enthalten.  Namespaces, Typen, Member und Parameter werden von der Regel dahingehend überprüft.  
  
 Durch Benennungskonventionen erhalten Bibliotheken, die auf die Common Language Runtime abzielen, ein einheitliches Erscheinungsbild.  Dadurch wird der Lernaufwand für neue Softwarebibliotheken verringert. Zudem wird das Kundenvertrauen dahingehend gestärkt, dass die Bibliothek von einem erfahrenen Entwickler für verwalteten Code erstellt wurde.  
  
## Behandeln von Verstößen  
 Entfernen Sie alle Unterstriche aus dem Namen.  
  
## Wann sollten Warnungen unterdrückt werden?  
 Unterdrücken Sie keine Warnung dieser Regel.  
  
## Verwandte Regeln  
 [CA1709: Bei Bezeichnern sollte die Groß\-\/Kleinschreibung beachtet werden](../code-quality/ca1709-identifiers-should-be-cased-correctly.md)  
  
 [CA1708: Bezeichner sollten sich nicht nur durch die Groß\-\/Kleinschreibung unterscheiden](../code-quality/ca1708-identifiers-should-differ-by-more-than-case.md)