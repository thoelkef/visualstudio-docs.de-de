---
title: 'CA1304: CultureInfo angeben'
ms.date: 06/30/2018
ms.prod: visual-studio-dev15
ms.technology: vs-ide-code-analysis
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
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: bae12da61047e8e9bde6ee097ed84c1d6c95acbc
ms.sourcegitcommit: f37affbc1b885dfe246d4b2c295a6538b383a0ca
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/02/2018
ms.locfileid: "37174139"
---
# <a name="ca1304-specify-cultureinfo"></a>CA1304: CultureInfo angeben

|||
|-|-|
|TypeName|SpecifyCultureInfo|
|CheckId|CA1304|
|Kategorie|Microsoft.Globalization|
|Unterbrechende Änderung|Nicht unterbrechend|

## <a name="cause"></a>Ursache

Eine Methode oder der Konstruktor ruft einen Member auf, die eine Überladung, die akzeptiert eine <xref:System.Globalization.CultureInfo?displayProperty=nameWithType> -Parameter, und die Methode oder der Konstruktor ruft nicht die Überladung, akzeptiert die <xref:System.Globalization.CultureInfo> Parameter. Diese Regel ignoriert Aufrufe der folgenden Methoden:

- <xref:System.Activator.CreateInstance%2A?displayProperty=nameWithType>
- <xref:System.Resources.ResourceManager.GetObject%2A?displayProperty=nameWithType>
- <xref:System.Resources.ResourceManager.GetString%2A?displayProperty=nameWithType>

## <a name="rule-description"></a>Regelbeschreibung

Wenn eine <xref:System.Globalization.CultureInfo> oder <xref:System.IFormatProvider?displayProperty=nameWithType> Objekt ist nicht angegeben, der Standardwert, der vom überladenen Member bereitgestellte ist möglicherweise nicht die in allen Gebietsschemas den gewünschten Effekt. Darüber hinaus wird .NET Framework-Member wählen Sie Standardkultur, und Formatierung basierend auf Annahmen, die möglicherweise nicht korrekt für Ihren Code. Um sicherzustellen, dass der Code funktioniert, wie für Ihre Szenarien erwartet, sollten Sie die kulturspezifische Informationen, anhand der folgenden Richtlinien angeben:

- Wenn der Wert für den Benutzer angezeigt wird, wird verwenden Sie die aktuelle Kultur. Siehe <xref:System.Globalization.CultureInfo.CurrentCulture%2A?displayProperty=nameWithType>.

- Wenn der Wert gespeichert und von der Software zugegriffen werden, verwenden Sie persistent gespeichert, in einer Datei oder Datenbank, die invariante Kultur, also. Siehe <xref:System.Globalization.CultureInfo.InvariantCulture%2A?displayProperty=nameWithType>.

- Wenn Sie nicht, dass das Ziel des Werts wissen, haben Sie den Datenconsumer oder Anbieter die Kultur angeben.

Auch wenn das Standardverhalten des überladenen Member für Ihre Anforderungen geeignet ist, ist es besser, die kulturspezifische Überladung explizit aufrufen, so, dass der Code selbsterklärend und einfacher zu verwalten ist.

> [!NOTE]
> <xref:System.Globalization.CultureInfo.CurrentUICulture%2A?displayProperty=nameWithType> wird nur verwendet, um lokalisierte Ressourcen abruft, mit einer Instanz von der <xref:System.Resources.ResourceManager?displayProperty=nameWithType> Klasse.

## <a name="how-to-fix-violations"></a>Behandeln von Verstößen

Um einen Verstoß gegen diese Regel zu beheben, verwenden Sie die Überladung mit einem <xref:System.Globalization.CultureInfo> Argument.

## <a name="when-to-suppress-warnings"></a>Wenn Sie Warnungen unterdrücken

Es ist sicher eine Warnung dieser Regel zu unterdrücken, wenn sicher ist, dass die Standardkultur die richtige Wahl ist und die codeverwaltbarkeit von keine wichtige Entwicklungsszenarien Priorität ist.

## <a name="example-showing-how-to-fix-violations"></a>Beispiel für die Behandlung von Verstößen

Im folgenden Beispiel `BadMethod` bewirkt, dass zwei Verstöße gegen diese Regel. `GoodMethod` korrigiert den ersten Verstoß durch Übergeben der invarianten Kultur, <xref:System.String.Compare%2A?displayProperty=nameWithType>, und diese gegebenenfalls korrigiert des zweiten Verstoßes durch Übergeben der aktuellen Kultur zu <xref:System.String.ToLower%2A?displayProperty=nameWithType> da `string3` wird dem Benutzer angezeigt.

[!code-csharp[FxCop.Globalization.CultureInfo#1](../code-quality/codesnippet/CSharp/ca1304-specify-cultureinfo_1.cs)]

## <a name="example-showing-formatted-output"></a>Beispiel zeigt die formatierte Ausgabe

Das folgende Beispiel zeigt die Auswirkung der aktuellen Kultur auf dem standardmäßigen <xref:System.IFormatProvider> , wird ausgewählt, die <xref:System.DateTime> Typ.

[!code-csharp[FxCop.Globalization.IFormatProvider#1](../code-quality/codesnippet/CSharp/ca1304-specify-cultureinfo_2.cs)]

Dieses Beispiel erzeugt die folgende Ausgabe:

**6/4/1900 12:15:12 UHR**

**06/04/1900 12:15:12**

## <a name="related-rules"></a>Verwandte Regeln

- [CA1305: IFormatProvider angeben](../code-quality/ca1305-specify-iformatprovider.md)

## <a name="see-also"></a>Siehe auch

- [Verwenden der CultureInfo-Klasse](/dotnet/standard/globalization-localization/globalization#Cultures)