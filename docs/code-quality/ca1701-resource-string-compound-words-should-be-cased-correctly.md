---
title: "CA1701: Bei zusammengesetzten Begriffen in Ressourcenzeichenfolgen sollte die Gro&#223;-/Kleinschreibung beachtet werden | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "ResourceStringCompoundWordsShouldBeCasedCorrectly"
  - "CA1701"
helpviewer_keywords: 
  - "CA1701"
  - "ResourceStringCompoundWordsShouldBeCasedCorrectly"
ms.assetid: 4ddbe09f-24b8-4c47-9373-a06f4487ca0d
caps.latest.revision: 24
caps.handback.revision: 24
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# CA1701: Bei zusammengesetzten Begriffen in Ressourcenzeichenfolgen sollte die Gro&#223;-/Kleinschreibung beachtet werden
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|ResourceStringCompoundWordsShouldBeCasedCorrectly|  
|CheckId|CA1701|  
|Kategorie \(Category\)|Microsoft.Naming|  
|Unterbrechende Änderung|Nicht unterbrechend|  
  
## Ursache  
 Eine Ressourcenzeichenfolge enthält einen zusammengesetzten Begriff, bei dem die Groß\-\/Kleinschreibung anscheinend nicht beachtet wurde.  
  
## Regelbeschreibung  
 Jeder Begriff in der Ressourcenzeichenfolge wird anhand der Groß\-\/Kleinschreibung in einzelne Token unterteilt.  Jede zusammenhängende Kombination aus zwei Token wird durch die Rechtschreibprüfung aus der Microsoft\-Bibliothek überprüft.  Wenn der Begriff erkannt wird, erzeugt er einen Regelverstoß.  Beispiele für zusammengesetzte Wörter, die eine Verletzung verursachen, sind "CheckSum" und "MultiPart", die die Schreibung "Checksum" bzw. "Multipart" aufweisen sollten.  Aufgrund typischer Verwendungsweisen in der Vergangenheit wurden mehrere Einzelwörtern in die Regel integriert, sodass einige Begriffe, wie "Toolbar" und "Filename", gekennzeichnet werden. Diese Begriffe sollten als zwei getrennte Wörter erkennbar sein,  in diesem Beispiel also "ToolBar" und "FileName".  
  
 Durch Benennungskonventionen erhalten Bibliotheken, die auf die Common Language Runtime abzielen, ein einheitliches Erscheinungsbild.  Dadurch wird der Lernaufwand für neue Softwarebibliotheken verringert. Zudem wird das Kundenvertrauen dahingehend gestärkt, dass die Bibliothek von einem erfahrenen Entwickler für verwalteten Code erstellt wurde.  
  
## Behandeln von Verstößen  
 Ändern Sie den Begriff, sodass er die richtige Groß\-\/Kleinschreibung aufweist.  
  
## Wann sollten Warnungen unterdrückt werden?  
 Eine Warnung dieser Regel kann gefahrlos unterdrückt werden, wenn beide Teile des zusammengesetzten Begriffs vom Rechtschreibwörterbuch ordnungsgemäß erkannt werden und ausdrücklich zwei Wörter verwendet werden sollen.  
  
 Sie können einem Benutzerwörterbuch für die Rechtschreibprüfung auch zusammengesetzte Wörter hinzufügen.  Wörter im Benutzerwörterbuch verursachen keine Verletzungen.  Weitere Informationen finden Sie unter [Gewusst wie: Anpassen des Codeanalysewörterbuchs](../code-quality/how-to-customize-the-code-analysis-dictionary.md).  
  
## Verwandte Regeln  
 [CA1702: Bei zusammengesetzten Begriffen sollte die Groß\-\/Kleinschreibung beachtet werden](../code-quality/ca1702-compound-words-should-be-cased-correctly.md)  
  
 [CA1709: Bei Bezeichnern sollte die Groß\-\/Kleinschreibung beachtet werden](../code-quality/ca1709-identifiers-should-be-cased-correctly.md)  
  
 [CA1708: Bezeichner sollten sich nicht nur durch die Groß\-\/Kleinschreibung unterscheiden](../code-quality/ca1708-identifiers-should-differ-by-more-than-case.md)  
  
## Siehe auch  
 [Großschreibung Konventionen](../Topic/Capitalization%20Conventions.md)   
 [Richtlinien für die Benennung](../Topic/Naming%20Guidelines.md)