---
title: "CA1703: Ressourcenzeichenfolgen sollten korrekt geschrieben werden | Microsoft Docs"
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
  - "ResourceStringsShouldBeSpelledCorrectly"
  - "CA1703"
helpviewer_keywords: 
  - "CA1703"
  - "ResourceStringsShouldBeSpelledCorrectly"
ms.assetid: 693f4970-f512-40cb-ae3b-a0f3a5c6d6f1
caps.latest.revision: 16
caps.handback.revision: 16
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# CA1703: Ressourcenzeichenfolgen sollten korrekt geschrieben werden
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|ResourceStringsShouldBeSpelledCorrectly|  
|CheckId|CA1703|  
|Kategorie \(Category\)|Microsoft.Naming|  
|Unterbrechende Änderung|Nicht unterbrechend|  
  
## Ursache  
 Eine Ressourcenzeichenfolge enthält mindestens ein Wort, das von der Rechtschreibprüfung aus der Microsoft\-Bibliothek nicht erkannt wird.  
  
## Regelbeschreibung  
 Durch diese Regel werden die Wörter der Ressourcenzeichenfolge analysiert \(zusammengesetzte Begriffe in Einzeltoken aufgeteilt\) und die Rechtschreibung der einzelnen Wörter\/Token überprüft.  Informationen über den Analysealgorithmus finden Sie unter [CA1704: Bezeichner sollten korrekt geschrieben werden](../code-quality/ca1704-identifiers-should-be-spelled-correctly.md).  
  
 Standardmäßig wird die englische Version \(EN\) der Rechtschreibprüfung verwendet.  
  
## Behandeln von Verstößen  
 Um einen Verstoß gegen diese Regel zu beheben, verwenden Sie vollständige, fehlerfreie Wörter oder fügen die Wörter einem benutzerdefinierten Wörterbuch hinzu.  Informationen zum Verwenden von benutzerdefinierten Wörterbüchern finden Sie unter [CA1704: Bezeichner sollten korrekt geschrieben werden](../code-quality/ca1704-identifiers-should-be-spelled-correctly.md).  
  
## Wann sollten Warnungen unterdrückt werden?  
 Unterdrücken Sie keine Warnung dieser Regel.  Durch fehlerfrei geschriebene Begriffe wird die Lernzeit für neue Softwarebibliotheken verkürzt.  
  
## Verwandte Regeln  
 [CA1701: Bei zusammengesetzten Begriffen in Ressourcenzeichenfolgen sollte die Groß\-\/Kleinschreibung beachtet werden](../code-quality/ca1701-resource-string-compound-words-should-be-cased-correctly.md)  
  
 [CA1704: Bezeichner sollten korrekt geschrieben werden](../code-quality/ca1704-identifiers-should-be-spelled-correctly.md)  
  
 [CA2204: Literale sollten eine korrekte Rechtschreibung aufweisen](../code-quality/ca2204-literals-should-be-spelled-correctly.md)