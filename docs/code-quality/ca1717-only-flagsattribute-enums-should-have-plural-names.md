---
title: "CA1717: Nur FlagsAttribute-Enumerationen sollten Pluralnamen aufweisen | Microsoft Docs"
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
  - "CA1717"
  - "OnlyFlagsEnumsShouldHavePluralNames"
helpviewer_keywords: 
  - "OnlyFlagsEnumsShouldHavePluralNames"
  - "CA1717"
ms.assetid: a6855d8b-d78a-42c1-834e-61c31f5572ed
caps.latest.revision: 17
caps.handback.revision: 17
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# CA1717: Nur FlagsAttribute-Enumerationen sollten Pluralnamen aufweisen
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|OnlyFlagsEnumsShouldHavePluralNames|  
|CheckId|CA1717|  
|Kategorie \(Category\)|Microsoft.Naming|  
|Unterbrechende Änderung|Breaking|  
  
## Ursache  
 Der Name einer extern sichtbaren Enumeration endet auf einem Pluralwort, und die Enumeration ist nicht mit dem <xref:System.FlagsAttribute?displayProperty=fullName>\-Attribut markiert.  
  
## Regelbeschreibung  
 Gemäß den Benennungskonventionen gibt ein Pluralname für eine Enumeration an, dass für die Enumeration mehrere Werte gleichzeitig angegeben werden können.  Durch <xref:System.FlagsAttribute> werden Compiler angewiesen, die Enumeration als Bitfeld zu behandeln, das bitweise Operationen für die Enumeration zulässt.  
  
 Wenn jeweils nur ein Wert einer Enumeration angegeben werden kann, sollte der Enumerationsname im Singular stehen.  Beispiel: Eine Enumeration, mit der die Wochentage angegeben werden, ist für die Verwendung in einer Anwendung konzipiert, in der mehrere Tage gleichzeitig festgelegt werden können.  Diese Enumeration sollte über <xref:System.FlagsAttribute> verfügen und könnte 'Days' genannt werden.  Eine ähnliche Enumeration, die jeweils nur die Angabe eines Tages zulässt, verfügt nicht über dieses Attribut und könnte 'Day' heißen.  
  
 Durch Benennungskonventionen erhalten Bibliotheken, die auf die Common Language Runtime abzielen, ein einheitliches Erscheinungsbild.  Dadurch wird der Lernaufwand für neue Softwarebibliotheken verringert. Zudem wird das Kundenvertrauen dahingehend gestärkt, dass die Bibliothek von einem erfahrenen Entwickler für verwalteten Code erstellt wurde.  
  
## Behandeln von Verstößen  
 Ändern Sie den Namen der Enumeration in die Singularform, oder fügen Sie <xref:System.FlagsAttribute> hinzu.  
  
## Wann sollten Warnungen unterdrückt werden?  
 Eine Warnung dieser Regel kann gefahrlos unterdrückt werden, wenn der Name auf der Singularform endet.  
  
## Verwandte Regeln  
 [CA1714: Flags\-Enumerationen sollten Pluralnamen aufweisen](../code-quality/ca1714-flags-enums-should-have-plural-names.md)  
  
 [CA1027: Enumerationen mit FlagsAttribute markieren](../code-quality/ca1027-mark-enums-with-flagsattribute.md)  
  
 [CA2217: Enumerationen nicht mit FlagsAttribute markieren](../code-quality/ca2217-do-not-mark-enums-with-flagsattribute.md)  
  
## Siehe auch  
 <xref:System.FlagsAttribute?displayProperty=fullName>   
 [Enum\-Entwurf](../Topic/Enum%20Design.md)