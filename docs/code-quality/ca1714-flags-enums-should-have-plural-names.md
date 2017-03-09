---
title: "CA1714: Flags-Enumerationen sollten Pluralnamen aufweisen | Microsoft Docs"
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
  - "FlagsEnumsShouldHavePluralNames"
  - "CA1714"
helpviewer_keywords: 
  - "CA1714"
  - "FlagsEnumsShouldHavePluralNames"
ms.assetid: 95ef5b43-7681-49e9-a5a3-ac0357cf1be7
caps.latest.revision: 14
caps.handback.revision: 14
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# CA1714: Flags-Enumerationen sollten Pluralnamen aufweisen
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|FlagsEnumsShouldHavePluralNames|  
|CheckId|CA1714|  
|Kategorie \(Category\)|Microsoft.Naming|  
|Unterbrechende Änderung|Breaking|  
  
## Ursache  
 Eine öffentliche Enumeration verfügt über <xref:System.FlagsAttribute?displayProperty=fullName>, und der Name endet nicht in der Pluralform.  
  
## Regelbeschreibung  
 Die Namen von mit <xref:System.FlagsAttribute> markierten Typen stehen im Plural, da das Attribut angibt, dass mehr als ein Wert festgelegt werden kann.  Beispiel: Eine Enumeration, mit der die Wochentage angegeben werden, ist für die Verwendung in einer Anwendung konzipiert, in der mehrere Tage gleichzeitig festgelegt werden können.  Diese Enumeration sollte über <xref:System.FlagsAttribute> verfügen und könnte 'Days' genannt werden.  Eine ähnliche Enumeration, die jeweils nur die Angabe eines Tages zulässt, verfügt nicht über dieses Attribut und könnte 'Day' heißen.  
  
 Durch Benennungskonventionen erhalten Bibliotheken, die auf die Common Language Runtime abzielen, ein einheitliches Erscheinungsbild.  Dadurch wird der Lernaufwand für neue Softwarebibliotheken verringert. Zudem wird das Kundenvertrauen dahingehend gestärkt, dass die Bibliothek von einem erfahrenen Entwickler für verwalteten Code erstellt wurde.  
  
## Behandeln von Verstößen  
 Benennen Sie die Enumeration mit der Pluralform, oder entfernen Sie das <xref:System.FlagsAttribute>\-Attribut, wenn es nicht möglich sein soll, mehrere Enumerationswerte gleichzeitig anzugeben.  
  
## Wann sollten Warnungen unterdrückt werden?  
 Ein Verstoß gegen diese Regel kann gefahrlos unterdrückt werden, wenn der Name im Plural angegeben ist, jedoch keine typische Pluralendung aufweist.  Wenn die zuvor beschriebene Wochentage\-Enumeration beispielsweise die Bezeichnung 'DaysOfTheWeek' hätte, würde zwar gegen die Regellogik verstoßen, nicht aber gegen ihre Absicht.  Solche Verstöße sollten unterdrückt werden.  
  
## Verwandte Regeln  
 [CA1027: Enumerationen mit FlagsAttribute markieren](../code-quality/ca1027-mark-enums-with-flagsattribute.md)  
  
 [CA2217: Enumerationen nicht mit FlagsAttribute markieren](../code-quality/ca2217-do-not-mark-enums-with-flagsattribute.md)  
  
## Siehe auch  
 <xref:System.FlagsAttribute?displayProperty=fullName>   
 [Enum\-Entwurf](../Topic/Enum%20Design.md)