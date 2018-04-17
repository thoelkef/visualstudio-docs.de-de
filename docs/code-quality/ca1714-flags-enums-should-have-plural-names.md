---
title: 'CA1714: Flags-Enumerationen sollten Pluralnamen aufweisen | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-code-analysis
ms.topic: conceptual
f1_keywords:
- FlagsEnumsShouldHavePluralNames
- CA1714
helpviewer_keywords:
- CA1714
- FlagsEnumsShouldHavePluralNames
ms.assetid: 95ef5b43-7681-49e9-a5a3-ac0357cf1be7
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: d5dc35718a20743ce6ed1502dbd1d9ed3c8a626e
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/16/2018
---
# <a name="ca1714-flags-enums-should-have-plural-names"></a>CA1714: Flags-Enumerationen sollten Pluralnamen aufweisen
|||  
|-|-|  
|TypeName|FlagsEnumsShouldHavePluralNames|  
|CheckId|CA1714|  
|Kategorie|Microsoft.Naming|  
|Unterbrechende Änderung|Breaking|  
  
## <a name="cause"></a>Ursache  
 Eine öffentliche Enumeration verfügt über die <xref:System.FlagsAttribute?displayProperty=fullName> und der Name endet nicht in der ".  
  
## <a name="rule-description"></a>Regelbeschreibung  
 Mit markierten Typen <xref:System.FlagsAttribute> haben Namen, die im plural, da das Attribut gibt an, dass mehr als ein Wert angegeben werden kann. Beispielsweise kann eine Enumeration, die die Tage der Woche definiert vorgesehen werden für die Verwendung in einer Anwendung, in dem Sie mehrere Tage angeben. Diese Enumeration müssen den <xref:System.FlagsAttribute> und 'Days' aufgerufen werden. Eine ähnliche-Enumeration, die nur einen einzigen Tag angegeben werden kann keine das Attribut, und möglicherweise 'Day' aufgerufen.  
  
 Durch Benennungskonventionen erhalten Bibliotheken, die auf die Common Language Runtime abzielen, ein einheitliches Erscheinungsbild. Dadurch wird der Lernaufwand für neue Softwarebibliotheken verringert. Zudem wird das Kundenvertrauen dahingehend gestärkt, dass die Bibliothek von einem erfahrenen Entwickler für verwalteten Code erstellt wurde.  
  
## <a name="how-to-fix-violations"></a>Behandeln von Verstößen  
 Der Name der Enumeration eine Pluralform, oder entfernen Sie die <xref:System.FlagsAttribute> Attribut, wenn mehrere Enumerationswerte sollten nicht gleichzeitig angegeben werden.  
  
## <a name="when-to-suppress-warnings"></a>Wann sollten Warnungen unterdrückt werden?  
 Ist eine Verletzung zu unterdrücken, sofern der Name eine Pluralform ist jedoch nicht endet sicher des ". Wenn die Multiple-Tage-Enumeration, die beschrieben wurde zuvor "DaysOfTheWeek" heißen, würde dies beispielsweise die Logik der Regel aber nicht ihre Absicht verletzen. Solche Verstöße sollten unterdrückt werden.  
  
## <a name="related-rules"></a>Verwandte Regeln  
 [CA1027: Enumerationen mit FlagsAttribute markieren](../code-quality/ca1027-mark-enums-with-flagsattribute.md)  
  
 [CA2217: Enumerationen nicht mit FlagsAttribute markieren](../code-quality/ca2217-do-not-mark-enums-with-flagsattribute.md)  
  
## <a name="see-also"></a>Siehe auch  
 <xref:System.FlagsAttribute?displayProperty=fullName>   
 [Enum-Entwurf](/dotnet/standard/design-guidelines/enum)