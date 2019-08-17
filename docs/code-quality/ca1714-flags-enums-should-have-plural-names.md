---
title: 'CA1714: Flags-Enumerationen sollten Pluralnamen aufweisen.'
ms.date: 03/11/2019
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
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: d71200c6c7fbb61e7994119fde5e75f7623fa669
ms.sourcegitcommit: 209ed0fcbb8daa1685e8d6b9a97f3857a4ce1152
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/16/2019
ms.locfileid: "69547195"
---
# <a name="ca1714-flags-enums-should-have-plural-names"></a>CA1714: Flags-Enumerationen sollten Pluralnamen aufweisen.

|||
|-|-|
|TypeName|FlagsEnumsShouldHavePluralNames|
|CheckId|CA1714|
|Kategorie|Microsoft.Naming|
|Unterbrechende Änderung|Breaking|

## <a name="cause"></a>Ursache

Eine Enumeration weist das <xref:System.FlagsAttribute?displayProperty=fullName> -Element und seinen Namen nicht auf ' ' auf.

Standardmäßig prüft diese Regel nur extern sichtbare Enumerationen, dies ist jedoch [konfigurierbar](#configurability).

## <a name="rule-description"></a>Regelbeschreibung

Typen, die mit <xref:System.FlagsAttribute> markiert sind, haben Namen, die den Plural aufweisen, da das Attribut angibt, dass mehr als ein Wert angegeben werden kann. Beispielsweise kann eine Enumeration, die die Wochentage definiert, für die Verwendung in einer Anwendung bestimmt werden, in der Sie mehrere Tage angeben können. Diese Enumeration sollte den und <xref:System.FlagsAttribute> den Namen "Days" aufweisen. Eine ähnliche Enumeration, die zulässt, dass nur ein einzelner Tag angegeben wird, verfügt nicht über das-Attribut und könnte als "Day" bezeichnet werden.

Durch Benennungskonventionen erhalten Bibliotheken, die auf die Common Language Runtime abzielen, ein einheitliches Erscheinungsbild. Dadurch wird der Lernaufwand für neue Softwarebibliotheken verringert. Zudem wird das Kundenvertrauen dahingehend gestärkt, dass die Bibliothek von einem erfahrenen Entwickler für verwalteten Code erstellt wurde.

## <a name="how-to-fix-violations"></a>Behandeln von Verstößen

Geben Sie den Namen der Enumeration als Plural Wort ein, oder entfernen <xref:System.FlagsAttribute> Sie das Attribut, wenn mehrere Enumerationswerte nicht gleichzeitig angegeben werden sollen.

## <a name="when-to-suppress-warnings"></a>Wann sollten Warnungen unterdrückt werden?

Es ist sicher, eine Verletzung zu unterdrücken, wenn der Name ein Plural Wort ist, aber nicht auf ' ' endet. Wenn z. b. die zuvor beschriebene Enumeration mit mehreren Tagen den Namen "daysofanweek" hatte, würde dies gegen die Logik der Regel verstoßen, aber nicht an ihre Absicht. Solche Verstöße sollten unterdrückt werden.

## <a name="configurability"></a>Konfigurierbarkeit

Wenn Sie diese Regel von [FxCop](install-fxcop-analyzers.md) Analyzer (und nicht mit der Legacy Analyse) ausführen, können Sie basierend auf ihrer Barrierefreiheit konfigurieren, für welche Teile Ihrer Codebasis diese Regel ausgeführt werden soll. Um z. b. anzugeben, dass die Regel nur für die nicht öffentliche API-Oberfläche ausgeführt werden soll, fügen Sie das folgende Schlüssel-Wert-Paar in eine Editor config-Datei in Ihrem Projekt ein:

```ini
dotnet_code_quality.ca1714.api_surface = private, internal
```

Sie können diese Option nur für diese Regel, für alle Regeln oder für alle Regeln in dieser Kategorie (Naming) konfigurieren. Weitere Informationen finden Sie unter [Konfigurieren von FxCop-Analysen](configure-fxcop-analyzers.md).

## <a name="related-rules"></a>Verwandte Regeln

- [CA1027: Markierungen mit FlagsAttribute markieren](../code-quality/ca1027-mark-enums-with-flagsattribute.md)
- [CA2217: Auffüge Zeichen nicht mit FlagsAttribute markieren](../code-quality/ca2217-do-not-mark-enums-with-flagsattribute.md)

## <a name="see-also"></a>Siehe auch

- <xref:System.FlagsAttribute?displayProperty=fullName>
- [Aufzählungs Design](/dotnet/standard/design-guidelines/enum)