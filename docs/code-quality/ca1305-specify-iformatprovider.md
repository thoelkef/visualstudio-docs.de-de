---
title: 'CA1305: IFormatProvider angeben.'
ms.date: 06/30/2018
ms.topic: reference
f1_keywords:
- SpecifyIFormatProvider
- CA1305
helpviewer_keywords:
- CA1305
- SpecifyIFormatProvider
ms.assetid: fb34ed9a-4eab-47cc-8eef-3068a4a1397e
author: gewarren
ms.author: gewarren
manager: jillfra
dev_langs:
- CSharp
ms.workload:
- multiple
ms.openlocfilehash: eda86085a5a2b8ba8e42116005890d2bda0b1dca
ms.sourcegitcommit: 5483e399f14fb01f528b3b194474778fd6f59fa6
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/05/2019
ms.locfileid: "66714677"
---
# <a name="ca1305-specify-iformatprovider"></a>CA1305: IFormatProvider angeben.

|||
|-|-|
|TypeName|SpecifyIFormatProvider|
|CheckId|CA1305|
|Kategorie|Microsoft.Globalization|
|Unterbrechende Änderung|Nicht unterbrechend|

## <a name="cause"></a>Ursache

Eine Methode oder ein Konstruktor ruft ein oder mehrere Elemente, deren Überladungen akzeptieren einen <xref:System.IFormatProvider?displayProperty=fullName> -Parameter, und die Methode oder der Konstruktor ruft nicht die Überladung, akzeptiert die <xref:System.IFormatProvider> Parameter.

Diese Regel ignoriert Aufrufe für .NET-Methoden, die als ignoriert dokumentiert sind die <xref:System.IFormatProvider> Parameter. Die Regel ignoriert auch die folgenden Methoden:

- <xref:System.Activator.CreateInstance%2A?displayProperty=nameWithType>
- <xref:System.Resources.ResourceManager.GetObject%2A?displayProperty=nameWithType>
- <xref:System.Resources.ResourceManager.GetString%2A?displayProperty=nameWithType>

## <a name="rule-description"></a>Regelbeschreibung

Wenn eine <xref:System.Globalization.CultureInfo?displayProperty=nameWithType> oder <xref:System.IFormatProvider> Objekt ist nicht angegeben, der Standardwert, der vom überladenen Member bereitgestellte ist möglicherweise nicht die in allen Gebietsschemas den gewünschten Effekt. Darüber hinaus .NET Member auswählen Standardkultur und Formatierung basierend auf Annahmen, die möglicherweise nicht korrekt für Ihren Code. Um sicherzustellen, dass der Code ordnungsgemäß für Ihre Szenarien funktioniert, sollten Sie die kulturspezifische Informationen, anhand der folgenden Richtlinien angeben:

- Wenn der Wert für den Benutzer angezeigt wird, wird verwenden Sie die aktuelle Kultur. Siehe <xref:System.Globalization.CultureInfo.CurrentCulture%2A?displayProperty=nameWithType>.

- Wenn der Wert gespeichert und von Software (persistent in einer Datei oder Datenbank) zugegriffen werden, die verwenden Sie die invariante Kultur. Siehe <xref:System.Globalization.CultureInfo.InvariantCulture%2A?displayProperty=nameWithType>.

- Wenn Sie nicht, dass das Ziel des Werts wissen, haben Sie den Datenconsumer oder Anbieter die Kultur angeben.

Auch wenn das Standardverhalten des überladenen Member für Ihre Anforderungen geeignet ist, ist es besser, die kulturspezifische Überladung explizit aufrufen, so, dass der Code selbsterklärend und einfacher zu verwalten ist.

## <a name="how-to-fix-violations"></a>Behandeln von Verstößen

Um einen Verstoß gegen diese Regel zu beheben, verwenden Sie die Überladung mit einem <xref:System.IFormatProvider> Argument. Oder verwenden Sie eine [c# interpolierte Zeichenfolge](/dotnet/csharp/tutorials/string-interpolation) und übergeben es an der <xref:System.FormattableString.Invariant%2A?displayProperty=nameWithType> Methode.

## <a name="when-to-suppress-warnings"></a>Wenn Sie Warnungen unterdrücken

Es ist sicher eine Warnung dieser Regel zu unterdrücken, wenn sicher ist, dass das standardmäßige Format die richtige Wahl ist und die codeverwaltbarkeit von keine wichtige Entwicklungsszenarien Priorität ist.

## <a name="example"></a>Beispiel

In den folgenden Code der `example1` Zeichenfolge verstößt gegen die Regel CA1305. Die `example2` Zeichenfolge Regel CA1305 entspricht, indem Sie übergeben <xref:System.Globalization.CultureInfo.CurrentCulture%2A?displayProperty=nameWithType>, implementiert <xref:System.IFormatProvider>zu <xref:System.String.Format(System.IFormatProvider,System.String,System.Object)?displayProperty=nameWithType>. Die `example3` Zeichenfolge erfüllt Regel CA1305 durch Übergeben einer interpolierten Zeichenfolge in <xref:System.FormattableString.Invariant%2A?displayProperty=fullName]>.

```csharp
string name = "Georgette";

// Violates CA1305
string example1 = String.Format("Hello {0}", name);

// Satisfies CA1305
string example2 = String.Format(CultureInfo.CurrentCulture, "Hello {0}", name);

// Satisfies CA1305
string example3 = FormattableString.Invariant($"Hello {name}");
```

## <a name="related-rules"></a>Verwandte Regeln

- [CA1304: CultureInfo angeben](../code-quality/ca1304-specify-cultureinfo.md)

## <a name="see-also"></a>Siehe auch

- [Verwenden der CultureInfo-Klasse](/dotnet/standard/globalization-localization/globalization#work-with-culture-specific-settings)