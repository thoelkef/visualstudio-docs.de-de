---
title: 'CA1714: Flags-Enumerationen sollten Pluralnamen aufweisen'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-code-analysis
ms.topic: reference
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
ms.openlocfilehash: 76b946e5fc5216d11eee98ceb8cc7eeb13ff186b
ms.sourcegitcommit: 568bb0b944d16cfe1af624879fa3d3594d020187
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/13/2018
ms.locfileid: "45545647"
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
 Typen, die mit markierten Felder <xref:System.FlagsAttribute> haben Namen, die in der Pluralform vorliegen, da das Attribut gibt an, dass mehr als ein Wert angegeben werden kann. Beispielsweise könnte eine Enumeration, die Tage der Woche definiert, gedacht ist für die Verwendung in einer Anwendung in dem Sie mehrere Tage angeben können. Diese Enumeration müssen den <xref:System.FlagsAttribute> 'Days' aufgerufen werden kann. Eine ähnliche-Enumeration, die nur einen einzelnen Tag angegeben werden kann. das Attribut keine, und möglicherweise 'Day' aufgerufen.

 Durch Benennungskonventionen erhalten Bibliotheken, die auf die Common Language Runtime abzielen, ein einheitliches Erscheinungsbild. Dadurch wird der Lernaufwand für neue Softwarebibliotheken verringert. Zudem wird das Kundenvertrauen dahingehend gestärkt, dass die Bibliothek von einem erfahrenen Entwickler für verwalteten Code erstellt wurde.

## <a name="how-to-fix-violations"></a>Behandeln von Verstößen
 Der Name der Enumeration eine Pluralform, oder entfernen Sie die <xref:System.FlagsAttribute> Attribut, wenn mehrere Enumerationswerte sollten nicht gleichzeitig angegeben werden.

## <a name="when-to-suppress-warnings"></a>Wenn Sie Warnungen unterdrücken
 Es ist sicher, um einen Verstoß zu unterdrücken, wenn der Name ist der Pluralform jedoch nicht endet die ". Wenn mehrere-Tage-Enumeration, die beschrieben wurde zuvor "DaysOfTheWeek" lauten würde, würde dies z. B. die Logik der Regel aber nicht die Absicht verletzen. Solche Verstöße zu erkennen unterdrückt werden sollen.

## <a name="related-rules"></a>Verwandte Regeln
 [CA1027: Enumerationen mit FlagsAttribute markieren](../code-quality/ca1027-mark-enums-with-flagsattribute.md)

 [CA2217: Enumerationen nicht mit FlagsAttribute markieren](../code-quality/ca2217-do-not-mark-enums-with-flagsattribute.md)

## <a name="see-also"></a>Siehe auch

- <xref:System.FlagsAttribute?displayProperty=fullName>
- [Enum-Entwurf](/dotnet/standard/design-guidelines/enum)