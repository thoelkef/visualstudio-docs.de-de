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
ms.openlocfilehash: a9f6c8fd44749de43d86bf8037df0130ad682321
ms.sourcegitcommit: 0c2523d975d48926dd2b35bcd2d32a8ae14c06d8
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/24/2019
ms.locfileid: "71235032"
---
# <a name="ca1305-specify-iformatprovider"></a>CA1305: IFormatProvider angeben.

|||
|-|-|
|TypeName|SpecifyIFormatProvider|
|CheckId|CA1305|
|Kategorie|Microsoft.Globalization|
|Unterbrechende Änderung|Nicht unterbrechend|

## <a name="cause"></a>Ursache

Eine Methode oder ein Konstruktor ruft einen oder mehrere Member auf, die über Ladungen aufweisen <xref:System.IFormatProvider?displayProperty=fullName> , die einen Parameter akzeptieren, und die Methode oder der Konstruktor ruft nicht die <xref:System.IFormatProvider> Überladung auf, die den-Parameter annimmt.

Diese Regel ignoriert Aufrufe von .NET-Methoden, die so dokumentiert sind <xref:System.IFormatProvider> , dass der-Parameter ignoriert wird. Die Regel ignoriert auch die folgenden Methoden:

- <xref:System.Activator.CreateInstance%2A?displayProperty=nameWithType>
- <xref:System.Resources.ResourceManager.GetObject%2A?displayProperty=nameWithType>
- <xref:System.Resources.ResourceManager.GetString%2A?displayProperty=nameWithType>

## <a name="rule-description"></a>Regelbeschreibung

Wenn ein <xref:System.Globalization.CultureInfo?displayProperty=nameWithType> - <xref:System.IFormatProvider> oder-Objekt nicht angegeben wird, hat der vom überladenen Member bereitgestellte Standardwert möglicherweise nicht die gewünschte Auswirkung in allen Gebiets Schemas. .Net-Member wählen außerdem Standard Kultur und-Formatierung basierend auf Annahmen, die für Ihren Code möglicherweise nicht korrekt sind. Um sicherzustellen, dass der Code für Ihre Szenarien erwartungsgemäß funktioniert, sollten Sie kulturspezifische Informationen gemäß den folgenden Richtlinien angeben:

- Wenn der Wert für den Benutzer angezeigt wird, verwenden Sie die aktuelle Kultur. Siehe <xref:System.Globalization.CultureInfo.CurrentCulture%2A?displayProperty=nameWithType>.

- Wenn der Wert von Software (persistent in einer Datei oder Datenbank) gespeichert wird und darauf zugegriffen wird, verwenden Sie die invariante Kultur. Siehe <xref:System.Globalization.CultureInfo.InvariantCulture%2A?displayProperty=nameWithType>.

- Wenn Sie das Ziel des Werts nicht kennen, lassen Sie den Datenconsumer oder-Anbieter die Kultur angeben.

Auch wenn das Standardverhalten des überladenen Elements für Ihre Bedürfnisse geeignet ist, ist es besser, die kulturspezifische Überladung explizit aufzurufen, sodass Ihr Code selbst dokumentierend und leichter zu pflegen ist.

## <a name="how-to-fix-violations"></a>Behandeln von Verstößen

Um einen Verstoß gegen diese Regel zu beheben, verwenden Sie die-über <xref:System.IFormatProvider> Ladung, die ein Argument annimmt. Oder verwenden Sie eine [ C# interinterpolierte Zeichenfolge](/dotnet/csharp/tutorials/string-interpolation) , und übergeben <xref:System.FormattableString.Invariant%2A?displayProperty=nameWithType> Sie Sie an die-Methode.

## <a name="when-to-suppress-warnings"></a>Wann sollten Warnungen unterdrückt werden?

Es ist sicher, eine Warnung aus dieser Regel zu unterdrücken, wenn sicher ist, dass das Standardformat die richtige Wahl ist und die Code Wartbarkeit keine wichtige Entwicklungs Priorität ist.

## <a name="example"></a>Beispiel

Im folgenden Code verstößt die Zeichen `example1` Folge gegen die Regel CA1305. Die `example2` Zeichenfolge erfüllt die Regel CA1305 <xref:System.Globalization.CultureInfo.CurrentCulture%2A?displayProperty=nameWithType>durch Übergeben von <xref:System.IFormatProvider>, der <xref:System.String.Format(System.IFormatProvider,System.String,System.Object)?displayProperty=nameWithType>implementiert, in. Die `example3` Zeichenfolge erfüllt die Regel CA1305, indem eine interpoliert <xref:System.FormattableString.Invariant%2A?displayProperty=fullName]>-Zeichenfolge an übergeben wird.

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

- [CA1304: Geben Sie CultureInfo an.](../code-quality/ca1304-specify-cultureinfo.md)

## <a name="see-also"></a>Siehe auch

- [Verwenden der CultureInfo-Klasse](/dotnet/standard/globalization-localization/globalization#work-with-culture-specific-settings)