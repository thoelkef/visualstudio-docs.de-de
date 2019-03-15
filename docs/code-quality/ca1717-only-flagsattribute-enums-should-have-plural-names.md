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
ms.openlocfilehash: e6da5a791237aefa037b2cb16bffef34576ac6e7
ms.sourcegitcommit: f7c401a376ce410336846835332a693e6159c551
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/14/2019
ms.locfileid: "57869865"
---
# <a name="ca1717-only-flagsattribute-enums-should-have-plural-names"></a>CA1717: Nur FlagsAttribute-Enumerationen sollten Pluralnamen aufweisen.

|||
|-|-|
|TypeName|OnlyFlagsEnumsShouldHavePluralNames|
|CheckId|CA1717|
|Kategorie|Microsoft.Naming|
|Unterbrechende Änderung|Breaking|

## <a name="cause"></a>Ursache

Der Name einer Enumeration, die in der Pluralform endet und die Enumeration ist nicht mit markiert die <xref:System.FlagsAttribute?displayProperty=fullName> Attribut.

Diese Regel nur sucht standardmäßig an extern sichtbare Enumerationen, dies ist jedoch [konfigurierbare](#configurability).

## <a name="rule-description"></a>Regelbeschreibung

Benennungskonventionen für vorgeben, dass ein Pluralname für eine Enumeration gibt an, dass mehr als einen Wert der Enumeration gleichzeitig angegeben werden kann. Die <xref:System.FlagsAttribute> werden Compiler angewiesen, die Enumeration als Bitfeld behandelt werden soll, der bitweise Vorgänge in der Enumeration ermöglicht.

Wenn nur ein Wert einer Enumeration zu einem Zeitpunkt angegeben werden kann, sollte der Name der Enumeration Singularform sein. Beispielsweise könnte eine Enumeration, die Tage der Woche definiert, gedacht ist für die Verwendung in einer Anwendung in dem Sie mehrere Tage angeben können. Diese Enumeration müssen den <xref:System.FlagsAttribute> 'Days' aufgerufen werden kann. Eine ähnliche-Enumeration, die nur einen einzelnen Tag angegeben werden kann. das Attribut keine, und möglicherweise 'Day' aufgerufen.

Durch Benennungskonventionen erhalten Bibliotheken, die auf die Common Language Runtime abzielen, ein einheitliches Erscheinungsbild. Dies reduziert die Zeit, die ist erforderlich, um eine neue Softwarebibliothek erfahren, und zudem wird das Kundenvertrauen, dass die Bibliothek von einer Person entwickelt wurde, die Erfahrung in der Entwicklung von verwaltetem Code hat.

## <a name="how-to-fix-violations"></a>Behandeln von Verstößen

Ändern Sie dem Namen der Enumeration Singularform oder Hinzufügen der <xref:System.FlagsAttribute>.

## <a name="when-to-suppress-warnings"></a>Wenn Sie Warnungen unterdrücken

Es ist sicher eine Warnung von der Regel zu unterdrücken, wenn der Name in die Singularform endet.

## <a name="configurability"></a>Konfigurierbarkeit

Wenn Sie diese Regel aus ausführen, [FxCop-Analysen](install-fxcop-analyzers.md) (und nicht über die Analyse von statischem Code), können Sie konfigurieren, welche Teile Ihrer Codebasis, um die Ausführung dieser Regel auf, um basierend auf deren Barrierefreiheit. Z. B. um anzugeben, dass die Regel nur für die nicht öffentlichen API-Oberfläche ausgeführt werden soll, fügen Sie die folgenden Schlüssel-Wert-Paar in einer editorconfig-Datei in Ihrem Projekt:

```
dotnet_code_quality.ca1717.api_surface = private, internal
```

Sie können diese Option, die für diese eine Regel, für alle Regeln oder für alle Regeln in dieser Kategorie (Naming) konfigurieren. Weitere Informationen finden Sie unter [konfigurieren FxCop-Analysetools](configure-fxcop-analyzers.md).

## <a name="related-rules"></a>Verwandte Regeln

- [CA1714: Flags-Enumerationen sollten Pluralnamen aufweisen.](../code-quality/ca1714-flags-enums-should-have-plural-names.md)
- [CA1027: Enumerationen mit FlagsAttribute markieren](../code-quality/ca1027-mark-enums-with-flagsattribute.md)
- [CA2217: Nicht Enumerationen mit FlagsAttribute markieren](../code-quality/ca2217-do-not-mark-enums-with-flagsattribute.md)

## <a name="see-also"></a>Siehe auch

- <xref:System.FlagsAttribute?displayProperty=fullName>
- [Enum-Entwurf](/dotnet/standard/design-guidelines/enum)