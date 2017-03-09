---
title: "CA1702: Bei zusammengesetzten Begriffen sollte die Gro&#223;-/Kleinschreibung beachtet werden | Microsoft Docs"
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
  - "CA1702"
  - "CompoundWordsShouldBeCasedCorrectly"
helpviewer_keywords: 
  - "CA1702"
  - "CompoundWordsShouldBeCasedCorrectly"
ms.assetid: 05481245-7ad8-48c3-a456-3aa44b6160a6
caps.latest.revision: 20
caps.handback.revision: 20
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# CA1702: Bei zusammengesetzten Begriffen sollte die Gro&#223;-/Kleinschreibung beachtet werden
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|CompoundWordsShouldBeCasedCorrectly|  
|CheckId|CA1702|  
|Kategorie \(Category\)|Microsoft.Naming|  
|Unterbrechende Änderung|Unterbrechend – Wenn für Assemblys ausgelöst.<br /><br /> Nicht unterbrechend – Wenn für Typparameter ausgelöst.|  
  
## Ursache  
 Der Name eines Bezeichners enthält mehrere Begriffe, und mindestens einer der Begriffe ist anscheinend ein zusammengesetztes Wort mit falscher Groß\-\/Kleinschreibung.  
  
## Regelbeschreibung  
 Der Name des Bezeichners wird basierend auf der Groß\-\/Kleinschreibung in Wörter unterteilt.  Jede zusammenhängende Kombination aus zwei Wörtern wird durch die Rechtschreibprüfung aus der Microsoft\-Bibliothek überprüft.  Falls der Bezeichner erkannt wird, erzeugt er einen Regelverstoß.  Beispiele für zusammengesetzte Wörter, die eine Verletzung verursachen, sind "CheckSum" und "MultiPart", die die Schreibung "Checksum" bzw. "Multipart" aufweisen sollten.  Aufgrund typischer Verwendungsweisen in der Vergangenheit wurden mehrere Einzelwörtern in die Regel integriert, sodass einige Begriffe, wie "Toolbar" und "Filename", gekennzeichnet werden. Diese Begriffe sollten als zwei getrennte Wörter erkennbar sein, in diesem Fall "ToolBar" und "FileName".  
  
 Durch Benennungskonventionen erhalten Bibliotheken, die auf die Common Language Runtime abzielen, ein einheitliches Erscheinungsbild.  Dadurch wird der Lernaufwand für neue Softwarebibliotheken verringert. Zudem wird das Kundenvertrauen dahingehend gestärkt, dass die Bibliothek von einem erfahrenen Entwickler für verwalteten Code erstellt wurde.  
  
## Behandeln von Verstößen  
 Ändern Sie den Namen, sodass er die ordnungsgemäße Groß\-\/Kleinschreibung aufweist.  
  
## Wann sollten Warnungen unterdrückt werden?  
 Eine Warnung dieser Regel kann gefahrlos unterdrückt werden, wenn beide Teile des zusammengesetzten Begriffs vom Rechtschreibwörterbuch ordnungsgemäß erkannt werden und ausdrücklich zwei Wörter verwendet werden sollen.  
  
## Verwandte Regeln  
 [CA1701: Bei zusammengesetzten Begriffen in Ressourcenzeichenfolgen sollte die Groß\-\/Kleinschreibung beachtet werden](../code-quality/ca1701-resource-string-compound-words-should-be-cased-correctly.md)  
  
 [CA1709: Bei Bezeichnern sollte die Groß\-\/Kleinschreibung beachtet werden](../code-quality/ca1709-identifiers-should-be-cased-correctly.md)  
  
 [CA1708: Bezeichner sollten sich nicht nur durch die Groß\-\/Kleinschreibung unterscheiden](../code-quality/ca1708-identifiers-should-differ-by-more-than-case.md)  
  
## Siehe auch  
 [Richtlinien für die Benennung](../Topic/Naming%20Guidelines.md)   
 [Großschreibung Konventionen](../Topic/Capitalization%20Conventions.md)