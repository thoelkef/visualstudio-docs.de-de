---
title: 'CA1714: Flags-Enumerationen sollten Plural Namen aufweisen. Microsoft-Dokumentation'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- FlagsEnumsShouldHavePluralNames
- CA1714
helpviewer_keywords:
- CA1714
- FlagsEnumsShouldHavePluralNames
ms.assetid: 95ef5b43-7681-49e9-a5a3-ac0357cf1be7
caps.latest.revision: 16
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: ca3709411f50d0b65f33bb8eed6457cfd1325ff6
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/19/2019
ms.locfileid: "72669141"
---
# <a name="ca1714-flags-enums-should-have-plural-names"></a>CA1714: Flags-Enumerationen sollten Pluralnamen aufweisen
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|FlagsEnumsShouldHavePluralNames|
|CheckId|CA1714|
|Kategorie|Microsoft.Naming|
|Unterbrechende Änderung|Breaking|

## <a name="cause"></a>Ursache
 Eine öffentliche Enumeration verfügt über die <xref:System.FlagsAttribute?displayProperty=fullName>, und Ihr Name endet nicht mit "".

## <a name="rule-description"></a>Regelbeschreibung
 Typen, die mit <xref:System.FlagsAttribute> gekennzeichnet sind, haben Namen, die den Plural aufweisen, da das Attribut angibt, dass mehr als ein Wert angegeben werden kann. Beispielsweise kann eine Enumeration, die die Wochentage definiert, für die Verwendung in einer Anwendung bestimmt werden, in der Sie mehrere Tage angeben können. Diese Enumeration sollte den <xref:System.FlagsAttribute> aufweisen und als "Days" bezeichnet werden. Eine ähnliche Enumeration, die zulässt, dass nur ein einzelner Tag angegeben wird, verfügt nicht über das-Attribut und könnte als "Day" bezeichnet werden.

 Durch Benennungskonventionen erhalten Bibliotheken, die auf die Common Language Runtime abzielen, ein einheitliches Erscheinungsbild. Dadurch wird der Lernaufwand für neue Softwarebibliotheken verringert. Zudem wird das Kundenvertrauen dahingehend gestärkt, dass die Bibliothek von einem erfahrenen Entwickler für verwalteten Code erstellt wurde.

## <a name="how-to-fix-violations"></a>Behandeln von Verstößen
 Geben Sie den Namen der Enumeration als Plural Wort ein, oder entfernen Sie das <xref:System.FlagsAttribute>-Attribut, wenn mehrere Enumerationswerte nicht gleichzeitig angegeben werden sollen.

## <a name="when-to-suppress-warnings"></a>Wann sollten Warnungen unterdrückt werden?
 Es ist sicher, eine Verletzung zu unterdrücken, wenn der Name ein Plural Wort ist, aber nicht auf ' ' endet. Wenn z. b. die zuvor beschriebene Enumeration mit mehreren Tagen den Namen "daysofanweek" hatte, würde dies gegen die Logik der Regel verstoßen, aber nicht an ihre Absicht. Solche Verstöße sollten Suppressd sein.

## <a name="related-rules"></a>Verwandte Regeln
 [CA1027: Enumerationen mit FlagsAttribute markieren](../code-quality/ca1027-mark-enums-with-flagsattribute.md)

 [CA2217: Enumerationen nicht mit FlagsAttribute markieren](../code-quality/ca2217-do-not-mark-enums-with-flagsattribute.md)

## <a name="see-also"></a>Siehe auch
 <xref:System.FlagsAttribute?displayProperty=fullName>-Aufzählungs [Entwurf](https://msdn.microsoft.com/library/dd53c952-9d9a-4736-86ff-9540e815d545)
