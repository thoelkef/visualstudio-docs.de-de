---
title: 'CA1304: CultureInfo angeben.'
ms.date: 06/30/2018
ms.topic: reference
f1_keywords:
- SpecifyCultureInfo
- CA1304
helpviewer_keywords:
- SpecifyCultureInfo
- CA1304
ms.assetid: b912d76a-54fd-4c93-b25d-16491e0ae319
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 2539cef9e6b2fe20513943f686aeaa1ff7a79013
ms.sourcegitcommit: 0c2523d975d48926dd2b35bcd2d32a8ae14c06d8
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/24/2019
ms.locfileid: "71235103"
---
# <a name="ca1304-specify-cultureinfo"></a>CA1304: CultureInfo angeben.

|||
|-|-|
|TypeName|SpecifyCultureInfo|
|CheckId|CA1304|
|Kategorie|Microsoft.Globalization|
|Unterbrechende Änderung|Nicht unterbrechend|

## <a name="cause"></a>Ursache

Eine Methode oder ein Konstruktor ruft einen Member mit einer Überladung auf, <xref:System.Globalization.CultureInfo?displayProperty=nameWithType> die einen-Parameter akzeptiert, und die-Methode oder der-Konstruktor ruft <xref:System.Globalization.CultureInfo> nicht die-Überladung auf, die den-Parameter annimmt. Diese Regel ignoriert Aufrufe der folgenden Methoden:

- <xref:System.Activator.CreateInstance%2A?displayProperty=nameWithType>
- <xref:System.Resources.ResourceManager.GetObject%2A?displayProperty=nameWithType>
- <xref:System.Resources.ResourceManager.GetString%2A?displayProperty=nameWithType>

## <a name="rule-description"></a>Regelbeschreibung

Wenn ein <xref:System.Globalization.CultureInfo> - <xref:System.IFormatProvider?displayProperty=nameWithType> oder-Objekt nicht angegeben wird, hat der vom überladenen Member bereitgestellte Standardwert möglicherweise nicht die gewünschte Auswirkung in allen Gebiets Schemas. .Net-Member wählen außerdem Standard Kultur und-Formatierung basierend auf Annahmen, die für Ihren Code möglicherweise nicht korrekt sind. Um sicherzustellen, dass der Code für Ihre Szenarien erwartungsgemäß funktioniert, sollten Sie kulturspezifische Informationen gemäß den folgenden Richtlinien angeben:

- Wenn der Wert für den Benutzer angezeigt wird, verwenden Sie die aktuelle Kultur. Siehe <xref:System.Globalization.CultureInfo.CurrentCulture%2A?displayProperty=nameWithType>.

- Verwenden Sie die invariante Kultur, wenn der Wert von Software gespeichert wird, d. h. in einer Datei oder Datenbank persistent gespeichert wird. Siehe <xref:System.Globalization.CultureInfo.InvariantCulture%2A?displayProperty=nameWithType>.

- Wenn Sie das Ziel des Werts nicht kennen, lassen Sie den Datenconsumer oder-Anbieter die Kultur angeben.

Auch wenn das Standardverhalten des überladenen Elements für Ihre Bedürfnisse geeignet ist, ist es besser, die kulturspezifische Überladung explizit aufzurufen, sodass Ihr Code selbst dokumentierend und leichter zu pflegen ist.

> [!NOTE]
> <xref:System.Globalization.CultureInfo.CurrentUICulture%2A?displayProperty=nameWithType>wird nur zum Abrufen lokalisierter Ressourcen mithilfe einer Instanz der <xref:System.Resources.ResourceManager?displayProperty=nameWithType> -Klasse verwendet.

## <a name="how-to-fix-violations"></a>Behandeln von Verstößen

Um einen Verstoß gegen diese Regel zu beheben, verwenden Sie die-über <xref:System.Globalization.CultureInfo> Ladung, die ein-Argument annimmt.

## <a name="when-to-suppress-warnings"></a>Wann sollten Warnungen unterdrückt werden?

Es ist sicher, eine Warnung aus dieser Regel zu unterdrücken, wenn sicher ist, dass die Standard Kultur die richtige Wahl ist und die Code Wartbarkeit keine wichtige Entwicklungs Priorität ist.

## <a name="example-showing-how-to-fix-violations"></a>Beispiel für das Beheben von Verstößen

Im folgenden Beispiel `BadMethod` verursacht zwei Verstöße gegen diese Regel. `GoodMethod`korrigiert den ersten Verstoß durch übergeben der invarianten Kultur an <xref:System.String.Compare%2A?displayProperty=nameWithType>und korrigiert den zweiten Verstoß durch übergeben der aktuellen Kultur an <xref:System.String.ToLower%2A?displayProperty=nameWithType> , da `string3` dem Benutzer angezeigt wird.

[!code-csharp[FxCop.Globalization.CultureInfo#1](../code-quality/codesnippet/CSharp/ca1304-specify-cultureinfo_1.cs)]

## <a name="example-showing-formatted-output"></a>Beispiel für formatierte Ausgabe

Das folgende Beispiel zeigt die Auswirkung der aktuellen Kultur auf den Standard <xref:System.IFormatProvider> Wert, der <xref:System.DateTime> vom-Typ ausgewählt wird.

[!code-csharp[FxCop.Globalization.IFormatProvider#1](../code-quality/codesnippet/CSharp/ca1304-specify-cultureinfo_2.cs)]

Dieses Beispiel erzeugt die folgende Ausgabe:

```txt
6/4/1900 12:15:12 PM
06/04/1900 12:15:12
```

## <a name="related-rules"></a>Verwandte Regeln

- [CA1305: IFormatProvider angeben](../code-quality/ca1305-specify-iformatprovider.md)

## <a name="see-also"></a>Siehe auch

- [Verwenden der CultureInfo-Klasse](/dotnet/standard/globalization-localization/globalization#work-with-culture-specific-settings)