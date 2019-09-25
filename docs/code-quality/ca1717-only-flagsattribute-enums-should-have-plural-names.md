---
title: 'CA1717: Nur FlagsAttribute-Enumerationen sollten Pluralnamen aufweisen.'
ms.date: 03/11/2019
ms.topic: reference
f1_keywords:
- CA1717
- OnlyFlagsEnumsShouldHavePluralNames
helpviewer_keywords:
- OnlyFlagsEnumsShouldHavePluralNames
- CA1717
ms.assetid: a6855d8b-d78a-42c1-834e-61c31f5572ed
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: b352d8f49cb92f70b449427179229fd882dbc9ce
ms.sourcegitcommit: 0c2523d975d48926dd2b35bcd2d32a8ae14c06d8
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/24/2019
ms.locfileid: "71234064"
---
# <a name="ca1717-only-flagsattribute-enums-should-have-plural-names"></a>CA1717: Nur FlagsAttribute-Enumerationen sollten Pluralnamen aufweisen.

|||
|-|-|
|TypeName|OnlyFlagsEnumsShouldHavePluralNames|
|CheckId|CA1717|
|Kategorie|Microsoft.Naming|
|Unterbrechende Änderung|Breaking|

## <a name="cause"></a>Ursache

Der Name einer Enumeration endet in einem Plural Wort, und die Enumeration ist nicht mit dem <xref:System.FlagsAttribute?displayProperty=fullName> -Attribut gekennzeichnet.

Standardmäßig prüft diese Regel nur extern sichtbare Enumerationen, dies ist jedoch [konfigurierbar](#configurability).

## <a name="rule-description"></a>Regelbeschreibung

Benennungs Konventionen legen fest, dass ein Plural Name für eine Enumeration angibt, dass mehr als ein Wert der Enumeration gleichzeitig angegeben werden kann. Der <xref:System.FlagsAttribute> weist Compiler an, dass die Enumeration als Bitfeld behandelt werden soll, das bitweise Operationen für die Enumeration ermöglicht.

Wenn nur ein Wert einer Enumeration gleichzeitig angegeben werden kann, sollte der Name der Enumeration ein einzelnes Wort sein. Beispielsweise kann eine Enumeration, die die Wochentage definiert, für die Verwendung in einer Anwendung bestimmt werden, in der Sie mehrere Tage angeben können. Diese Enumeration sollte den und <xref:System.FlagsAttribute> den Namen "Days" aufweisen. Eine ähnliche Enumeration, die zulässt, dass nur ein einzelner Tag angegeben wird, verfügt nicht über das-Attribut und könnte als "Day" bezeichnet werden.

Durch Benennungskonventionen erhalten Bibliotheken, die auf die Common Language Runtime abzielen, ein einheitliches Erscheinungsbild. Dies reduziert die Zeit, die erforderlich ist, um eine neue Software Bibliothek kennenzulernen, und steigert das Kunden Vertrauen, dass die Bibliothek von einem Benutzer entwickelt wurde, der über Kenntnisse in der Entwicklung von verwaltetem Code verfügt.

## <a name="how-to-fix-violations"></a>Behandeln von Verstößen

Geben Sie den Namen der Enumeration als Singular Wort an, oder <xref:System.FlagsAttribute>fügen Sie hinzu.

## <a name="when-to-suppress-warnings"></a>Wann sollten Warnungen unterdrückt werden?

Es ist sicher, eine Warnung aus der Regel zu unterdrücken, wenn der Name auf ein einzelnes Wort endet.

## <a name="configurability"></a>Konfigurierbarkeit

Wenn Sie diese Regel von [FxCop](install-fxcop-analyzers.md) Analyzer (und nicht mit der Legacy Analyse) ausführen, können Sie basierend auf ihrer Barrierefreiheit konfigurieren, für welche Teile Ihrer Codebasis diese Regel ausgeführt werden soll. Um z. b. anzugeben, dass die Regel nur für die nicht öffentliche API-Oberfläche ausgeführt werden soll, fügen Sie das folgende Schlüssel-Wert-Paar in eine Editor config-Datei in Ihrem Projekt ein:

```ini
dotnet_code_quality.ca1717.api_surface = private, internal
```

Sie können diese Option nur für diese Regel, für alle Regeln oder für alle Regeln in dieser Kategorie (Naming) konfigurieren. Weitere Informationen finden Sie unter [Konfigurieren von FxCop-Analysen](configure-fxcop-analyzers.md).

## <a name="related-rules"></a>Verwandte Regeln

- [CA1714: Flags-Enumerationen sollten Plural Namen aufweisen.](../code-quality/ca1714-flags-enums-should-have-plural-names.md)
- [CA1027: Markierungen mit FlagsAttribute markieren](../code-quality/ca1027-mark-enums-with-flagsattribute.md)
- [CA2217: Auffüge Zeichen nicht mit FlagsAttribute markieren](../code-quality/ca2217-do-not-mark-enums-with-flagsattribute.md)

## <a name="see-also"></a>Siehe auch

- <xref:System.FlagsAttribute?displayProperty=fullName>
- [Aufzählungs Design](/dotnet/standard/design-guidelines/enum)