---
title: 'CA1714: Flags-Enumerationen sollten Pluralnamen aufweisen | Microsoft-Dokumentation'
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-devops-test
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- FlagsEnumsShouldHavePluralNames
- CA1714
helpviewer_keywords:
- CA1714
- FlagsEnumsShouldHavePluralNames
ms.assetid: 95ef5b43-7681-49e9-a5a3-ac0357cf1be7
caps.latest.revision: 16
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: c778267df8a54c474e956a5e41388a7f971823f4
ms.sourcegitcommit: 99d097d82ee4f9eff6f588e5ebb6b17d8f724b04
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/24/2018
ms.locfileid: "47524996"
---
# <a name="ca1714-flags-enums-should-have-plural-names"></a>CA1714: Flags-Enumerationen sollten Pluralnamen aufweisen
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Die neueste Version dieses Themas finden Sie unter [CA1714: Flags-Enumerationen sollten Pluralnamen aufweisen](https://docs.microsoft.com/visualstudio/code-quality/ca1714-flags-enums-should-have-plural-names).

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

## <a name="when-to-suppress-warnings"></a>Wann sollten Warnungen unterdrückt werden?
 Es ist sicher, um einen Verstoß zu unterdrücken, wenn der Name ist der Pluralform jedoch nicht endet die ". Wenn mehrere-Tage-Enumeration, die beschrieben wurde zuvor "DaysOfTheWeek" lauten würde, würde dies z. B. die Logik der Regel aber nicht die Absicht verletzen. Solche Verstöße zu erkennen sollten unterdrückt werden.

## <a name="related-rules"></a>Verwandte Regeln
 [CA1027: Enumerationen mit FlagsAttribute markieren](../code-quality/ca1027-mark-enums-with-flagsattribute.md)

 [CA2217: Enumerationen nicht mit FlagsAttribute markieren](../code-quality/ca2217-do-not-mark-enums-with-flagsattribute.md)

## <a name="see-also"></a>Siehe auch
 <xref:System.FlagsAttribute?displayProperty=fullName> [Enum-Entwurf](http://msdn.microsoft.com/library/dd53c952-9d9a-4736-86ff-9540e815d545)



