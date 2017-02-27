---
title: "CA1719: Parameternamen sollten nicht mit Membernamen &#252;bereinstimmen | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "ParameterNamesShouldNotMatchMemberNames"
  - "CA1719"
helpviewer_keywords: 
  - "CA1719"
  - "ParameterNamesShouldNotMatchMemberNames"
ms.assetid: c6fea690-1659-4ee7-a1c5-125ad6754525
caps.latest.revision: 18
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
caps.handback.revision: 18
---
# CA1719: Parameternamen sollten nicht mit Membernamen &#252;bereinstimmen
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|ParameterNamesShouldNotMatchMemberNames|  
|CheckId|CA1719|  
|Kategorie \(Category\)|Microsoft.Naming|  
|Unterbrechende Änderung|Breaking|  
  
## Ursache  
 Der Name eines extern sichtbaren Members stimmt bei einem Vergleich, bei dem nicht zwischen Groß\- und Kleinschreibung unterschieden wird, mit dem Namen eines seiner Parameter überein.  
  
## Regelbeschreibung  
 Ein Parametername sollte die Bedeutung eines Parameters vermitteln, und ein Membername sollte die Bedeutung eines Members vermitteln.  Diese stimmen in der Regel nicht überein.  Wenn ein Parameter mit dem Namen des zugehörigen Members benannt wird, ist dies nicht intuitiv, und es erschwert die Verwendung der Bibliothek.  
  
## Behandeln von Verstößen  
 Wählen Sie einen Parameternamen aus, der nicht mit dem Membernamen übereinstimmt.  
  
## Wann sollten Warnungen unterdrückt werden?  
 In Zusammenhang mit Neuentwicklungen kommt es zu keinem Szenario, in dem Sie eine Warnung dieser Regel unterdrücken müssen.  Bei Versandbibliotheken müssen Sie u. U. eine Warnung dieser Regel unterdrücken.  
  
## Verwandte Regeln  
 [CA1709: Bei Bezeichnern sollte die Groß\-\/Kleinschreibung beachtet werden](../code-quality/ca1709-identifiers-should-be-cased-correctly.md)  
  
 [CA1708: Bezeichner sollten sich nicht nur durch die Groß\-\/Kleinschreibung unterscheiden](../code-quality/ca1708-identifiers-should-differ-by-more-than-case.md)  
  
 [CA1707: Bezeichner sollten keine Unterstriche enthalten](../code-quality/ca1707-identifiers-should-not-contain-underscores.md)