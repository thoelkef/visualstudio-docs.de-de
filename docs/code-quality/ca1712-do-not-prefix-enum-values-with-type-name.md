---
title: "CA1712: Keine Typnamen als Pr&#228;fixe f&#252;r Enumerationswerte verwenden | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CA1712"
  - "DoNotPrefixEnumValuesWithTypeName"
helpviewer_keywords: 
  - "CA1712"
  - "DoNotPrefixEnumValuesWithTypeName"
ms.assetid: df0e3a12-67bf-48f1-a10b-2ef60484a5c7
caps.latest.revision: 15
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
caps.handback.revision: 15
---
# CA1712: Keine Typnamen als Pr&#228;fixe f&#252;r Enumerationswerte verwenden
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|DoNotPrefixEnumValuesWithTypeName|  
|CheckId|CA1712|  
|Kategorie \(Category\)|Microsoft.Naming|  
|Unterbrechende Änderung|Breaking|  
  
## Ursache  
 Eine Enumeration enthält einen Member, dessen Name mit dem Typnamen der Enumeration beginnt.  
  
## Regelbeschreibung  
 Den Namen von Enumationsmembern wird der Typname nicht als Präfix vorangestellt, weil die Typinformationen von den Entwicklungswerkzeugen bereitgestellt werden sollen.  
  
 Durch Benennungskonventionen erhalten Bibliotheken, die auf die Common Language Runtime abzielen, ein einheitliches Erscheinungsbild.  Dadurch wird der Lernaufwand für neue Softwarebibliotheken verringert. Zudem wird das Kundenvertrauen dahingehend gestärkt, dass die Bibliothek von einem erfahrenen Entwickler für verwalteten Code erstellt wurde.  
  
## Behandeln von Verstößen  
 Um einen Verstoß gegen diese Regel zu beheben, entfernen Sie das Typnamenpräfix aus dem Enumerationsmember.  
  
## Wann sollten Warnungen unterdrückt werden?  
 Unterdrücken Sie keine Warnung dieser Regel.  
  
## Beispiel  
 Das folgende Beispiel zeigt eine falsch benannte Enumeration und anschließend die korrigierte Version.  
  
 [!code-cs[FxCop.Naming.EnumValues#1](../code-quality/codesnippet/CSharp/ca1712-do-not-prefix-enum-values-with-type-name_1.cs)]
 [!code-cpp[FxCop.Naming.EnumValues#1](../code-quality/codesnippet/CPP/ca1712-do-not-prefix-enum-values-with-type-name_1.cpp)]
 [!code-vb[FxCop.Naming.EnumValues#1](../code-quality/codesnippet/VisualBasic/ca1712-do-not-prefix-enum-values-with-type-name_1.vb)]  
  
## Verwandte Regeln  
 [CA1711: Bezeichner sollten kein falsches Suffix aufweisen](../code-quality/ca1711-identifiers-should-not-have-incorrect-suffix.md)  
  
 [CA1027: Enumerationen mit FlagsAttribute markieren](../code-quality/ca1027-mark-enums-with-flagsattribute.md)  
  
 [CA2217: Enumerationen nicht mit FlagsAttribute markieren](../code-quality/ca2217-do-not-mark-enums-with-flagsattribute.md)  
  
## Siehe auch  
 <xref:System.Enum?displayProperty=fullName>