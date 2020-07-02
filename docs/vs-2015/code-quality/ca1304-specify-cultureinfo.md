---
title: 'CA1304: Geben Sie CultureInfo an | Microsoft-Dokumentation'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- SpecifyCultureInfo
- CA1304
helpviewer_keywords:
- SpecifyCultureInfo
- CA1304
ms.assetid: b912d76a-54fd-4c93-b25d-16491e0ae319
caps.latest.revision: 22
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: d874d69f36fc8520a7cfbe3e946116c2d85ed88f
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/30/2020
ms.locfileid: "85539060"
---
# <a name="ca1304-specify-cultureinfo"></a>CA1304: CultureInfo angeben.
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|Element|Wert|
|-|-|
|TypName|SpecifyCultureInfo|
|CheckId|CA1304|
|Kategorie|Microsoft. Globalization|
|Unterbrechende Änderung|Nicht unterbrechend|

## <a name="cause"></a>Ursache
 Eine Methode oder ein Konstruktor ruft einen Member mit einer Überladung auf, die einen <xref:System.Globalization.CultureInfo?displayProperty=fullName> -Parameter akzeptiert, und die-Methode oder der-Konstruktor ruft nicht die-Überladung auf, die den- <xref:System.Globalization.CultureInfo> Parameter annimmt. Diese Regel ignoriert Aufrufe der folgenden Methoden:

- <xref:System.Activator.CreateInstance%2A?displayProperty=fullName>

- <xref:System.Resources.ResourceManager.GetObject%2A?displayProperty=fullName>

- <xref:System.Resources.ResourceManager.GetString%2A?displayProperty=fullName>

## <a name="rule-description"></a>Beschreibung der Regel
 Wenn ein- <xref:System.Globalization.CultureInfo> oder- <xref:System.IFormatProvider?displayProperty=fullName> Objekt nicht angegeben wird, hat der vom überladenen Member bereitgestellte Standardwert möglicherweise nicht die gewünschte Auswirkung in allen Gebiets Schemas. Außerdem [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] Wählen Mitglieder Standard Kultur und-Formatierung basierend auf Annahmen aus, die für Ihren Code möglicherweise nicht korrekt sind. Um sicherzustellen, dass der Code für Ihre Szenarien erwartungsgemäß funktioniert, sollten Sie kulturspezifische Informationen gemäß den folgenden Richtlinien angeben:

- Wenn der Wert für den Benutzer angezeigt wird, verwenden Sie die aktuelle Kultur. Siehe <xref:System.Globalization.CultureInfo.CurrentCulture%2A?displayProperty=fullName>.

- Verwenden Sie die invariante Kultur, wenn der Wert von Software gespeichert wird, d. h. in einer Datei oder Datenbank persistent gespeichert wird. Siehe <xref:System.Globalization.CultureInfo.InvariantCulture%2A?displayProperty=fullName>.

- Wenn Sie das Ziel des Werts nicht kennen, lassen Sie den Datenconsumer oder-Anbieter die Kultur angeben.

  Beachten Sie, dass <xref:System.Globalization.CultureInfo.CurrentUICulture%2A?displayProperty=fullName> nur zum Abrufen lokalisierter Ressourcen mithilfe einer Instanz der- <xref:System.Resources.ResourceManager?displayProperty=fullName> Klasse verwendet wird.

  Auch wenn das Standardverhalten des überladenen Elements für Ihre Bedürfnisse geeignet ist, ist es besser, die kulturspezifische Überladung explizit aufzurufen, sodass Ihr Code selbst dokumentierend und leichter zu pflegen ist.

## <a name="how-to-fix-violations"></a>Behandeln von Verstößen
 Um einen Verstoß gegen diese Regel zu beheben, verwenden Sie die-Überladung, die einen oder annimmt, <xref:System.Globalization.CultureInfo> <xref:System.IFormatProvider> und geben Sie das-Argument gemäß den zuvor aufgelisteten Richtlinien an.

## <a name="when-to-suppress-warnings"></a>Wann sollten Warnungen unterdrückt werden?
 Es ist sicher, eine Warnung aus dieser Regel zu unterdrücken, wenn sicher ist, dass der standardmäßige Kultur-/Formatanbieter die richtige Wahl ist und die Code Wartbarkeit keine wichtige Entwicklungs Priorität darstellt.

## <a name="example"></a>Beispiel
 Im folgenden Beispiel `BadMethod` verursacht zwei Verstöße gegen diese Regel. `GoodMethod`korrigiert den ersten Verstoß durch übergeben der invarianten Kultur an System. String. Compare und korrigiert den zweiten Verstoß durch übergeben der aktuellen Kultur an, <xref:System.String.ToLower%2A> da `string3` dem Benutzer angezeigt wird.

 [!code-csharp[FxCop.Globalization.CultureInfo#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Globalization.CultureInfo/cs/FxCop.Globalization.CultureInfo.cs#1)]

## <a name="example"></a>Beispiel
 Das folgende Beispiel zeigt die Auswirkung der aktuellen Kultur auf den Standardwert <xref:System.IFormatProvider> , der vom- <xref:System.DateTime> Typ ausgewählt wird.

 [!code-csharp[FxCop.Globalization.IFormatProvider#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Globalization.IFormatProvider/cs/FxCop.Globalization.IFormatProvider.cs#1)]

 Folgende Ergebnisse werden zurückgegeben:

 **6/4/1900 12:15:12 Uhr** 
 **06/04/1900 12:15:12**
## <a name="related-rules"></a>Verwandte Regeln
 [CA1305: IFormatProvider angeben.](../code-quality/ca1305-specify-iformatprovider.md)

## <a name="see-also"></a>Weitere Informationen
 [NIB: Verwenden der CultureInfo-Klasse](https://msdn.microsoft.com/d4329e34-64c3-4d1e-8c73-5b0ee626ba7a)
