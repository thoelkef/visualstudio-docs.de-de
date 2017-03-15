---
title: "CA1715: Bezeichner sollten ein korrektes Pr&#228;fix aufweisen | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CA1715"
  - "IdentifiersShouldHaveCorrectPrefix"
helpviewer_keywords: 
  - "IdentifiersShouldHaveCorrectPrefix"
  - "CA1715"
ms.assetid: cf45f8df-6855-4cb6-a4e2-7cfed714cf2f
caps.latest.revision: 30
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
caps.handback.revision: 30
---
# CA1715: Bezeichner sollten ein korrektes Pr&#228;fix aufweisen
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|IdentifiersShouldHaveCorrectPrefix|  
|CheckId|CA1715|  
|Kategorie \(Category\)|Microsoft.Naming|  
|Unterbrechende Änderung|Unterbrechend – Wenn für Schnittstellen ausgelöst.<br /><br /> Nicht unterbrechend – Wenn für generische Typparameter ausgelöst.|  
  
## Ursache  
 Der Name einer extern sichtbaren Schnittstelle beginnt nicht mit dem Großbuchstaben 'I'.  
  
 \- oder \-  
  
 Der Name eines generischen Typparameters für einen extern sichtbaren Typ oder eine extern sichtbare Methode beginnt nicht mit dem Großbuchstaben "T".  
  
## Regelbeschreibung  
 Gemäß der Konvention beginnen die Namen bestimmter Programmierelemente mit einem bestimmten Präfix.  
  
 Schnittstellennamen sollten mit einem großen "I" und einem weiteren Großbuchstaben beginnen.  Diese Regel meldet Verstöße für Schnittstellennamen wie "MyInterface" und "IsolatedInterface".  
  
 Generische Typparameternamen sollten mit einem großen 'T' beginnen und optional von einem weiteren Großbuchstaben gefolgt werden.  Diese Regel meldet Verstöße für Namen generischer Typparameter wie "V" und "Type".  
  
 Durch Benennungskonventionen erhalten Bibliotheken, die auf die Common Language Runtime abzielen, ein einheitliches Erscheinungsbild.  Dadurch wird der Lernaufwand für neue Softwarebibliotheken verringert. Zudem wird das Kundenvertrauen dahingehend gestärkt, dass die Bibliothek von einem erfahrenen Entwickler für verwalteten Code erstellt wurde.  
  
## Behandeln von Verstößen  
 Benennen Sie den Bezeichner um, sodass er das korrekte Präfix aufweist.  
  
## Wann sollten Warnungen unterdrückt werden?  
 Unterdrücken Sie keine Warnung dieser Regel.  
  
## Beispiel  
 **Im folgenden Beispiel wird eine falsch benannte Schnittstelle dargestellt.**  
  
 [!code-cpp[FxCop.Naming.IdentifiersShouldHaveCorrectPrefix#1](../code-quality/codesnippet/CPP/ca1715-identifiers-should-have-correct-prefix_1.cpp)]
 [!code-vb[FxCop.Naming.IdentifiersShouldHaveCorrectPrefix#1](../code-quality/codesnippet/VisualBasic/ca1715-identifiers-should-have-correct-prefix_1.vb)]
 [!code-cs[FxCop.Naming.IdentifiersShouldHaveCorrectPrefix#1](../code-quality/codesnippet/CSharp/ca1715-identifiers-should-have-correct-prefix_1.cs)]  
  
## Beispiel  
 **Im folgenden Beispiel wird der vorherige Verstoß durch Hinzufügen des Präfixes 'I' zur Schnittstelle korrigiert.**  
  
 [!code-cs[FxCop.Naming.IdentifiersShouldHaveCorrectPrefix2#1](../code-quality/codesnippet/CSharp/ca1715-identifiers-should-have-correct-prefix_2.cs)]
 [!code-cpp[FxCop.Naming.IdentifiersShouldHaveCorrectPrefix2#1](../code-quality/codesnippet/CPP/ca1715-identifiers-should-have-correct-prefix_2.cpp)]
 [!code-vb[FxCop.Naming.IdentifiersShouldHaveCorrectPrefix2#1](../code-quality/codesnippet/VisualBasic/ca1715-identifiers-should-have-correct-prefix_2.vb)]  
  
## Beispiel  
 **Im folgenden Beispiel wird ein falsch benannter generischer Typparameter dargestellt.**  
  
 [!code-cpp[FxCop.Naming.IdentifiersShouldHaveCorrectPrefix3#1](../code-quality/codesnippet/CPP/ca1715-identifiers-should-have-correct-prefix_3.cpp)]
 [!code-vb[FxCop.Naming.IdentifiersShouldHaveCorrectPrefix3#1](../code-quality/codesnippet/VisualBasic/ca1715-identifiers-should-have-correct-prefix_3.vb)]
 [!code-cs[FxCop.Naming.IdentifiersShouldHaveCorrectPrefix3#1](../code-quality/codesnippet/CSharp/ca1715-identifiers-should-have-correct-prefix_3.cs)]  
  
## Beispiel  
 **Im folgenden Beispiel wird der vorherige Verstoß durch Hinzufügen des Präfixes 'T' zum generischen Typparameter korrigiert.**  
  
 [!code-cpp[FxCop.Naming.IdentifiersShouldHaveCorrectPrefix4#1](../code-quality/codesnippet/CPP/ca1715-identifiers-should-have-correct-prefix_4.cpp)]
 [!code-cs[FxCop.Naming.IdentifiersShouldHaveCorrectPrefix4#1](../code-quality/codesnippet/CSharp/ca1715-identifiers-should-have-correct-prefix_4.cs)]
 [!code-vb[FxCop.Naming.IdentifiersShouldHaveCorrectPrefix4#1](../code-quality/codesnippet/VisualBasic/ca1715-identifiers-should-have-correct-prefix_4.vb)]  
  
## Verwandte Regeln  
 [CA1722: Bezeichner sollten kein falsches Präfix aufweisen](../code-quality/ca1722-identifiers-should-not-have-incorrect-prefix.md)