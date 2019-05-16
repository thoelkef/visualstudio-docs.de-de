---
title: 'CA1304: CultureInfo angeben | Microsoft-Dokumentation'
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
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: f5d4333508d6faec3df81f860f5b5b2b526be324
ms.sourcegitcommit: 08fc78516f1107b83f46e2401888df4868bb1e40
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/15/2019
ms.locfileid: "65692087"
---
# <a name="ca1304-specify-cultureinfo"></a>CA1304: CultureInfo angeben.
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|SpecifyCultureInfo|
|CheckId|CA1304|
|Kategorie|Microsoft.Globalization|
|Unterbrechende Änderung|Nicht unterbrechend|

## <a name="cause"></a>Ursache
 Eine Methode oder der Konstruktor ruft einen Member auf, die eine Überladung, die akzeptiert eine <xref:System.Globalization.CultureInfo?displayProperty=fullName> -Parameter, und die Methode oder der Konstruktor ruft nicht die Überladung, akzeptiert die <xref:System.Globalization.CultureInfo> Parameter. Diese Regel ignoriert Aufrufe der folgenden Methoden:

- <xref:System.Activator.CreateInstance%2A?displayProperty=fullName>

- <xref:System.Resources.ResourceManager.GetObject%2A?displayProperty=fullName>

- <xref:System.Resources.ResourceManager.GetString%2A?displayProperty=fullName>

## <a name="rule-description"></a>Regelbeschreibung
 Wenn eine <xref:System.Globalization.CultureInfo> oder <xref:System.IFormatProvider?displayProperty=fullName> Objekt ist nicht angegeben, der Standardwert, der vom überladenen Member bereitgestellte ist möglicherweise nicht die in allen Gebietsschemas den gewünschten Effekt. Darüber hinaus [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] Membern die Standardkultur Auswahl und Formatierung basierend auf Annahmen, die möglicherweise nicht korrekt für Ihren Code. Um sicherzustellen, dass der Code funktioniert, wie für Ihre Szenarien erwartet, sollten Sie die kulturspezifische Informationen, anhand der folgenden Richtlinien angeben:

- Wenn der Wert für den Benutzer angezeigt wird, wird verwenden Sie die aktuelle Kultur. Siehe <xref:System.Globalization.CultureInfo.CurrentCulture%2A?displayProperty=fullName>.

- Wenn der Wert gespeichert und von der Software zugegriffen werden, verwenden Sie persistent gespeichert, in einer Datei oder Datenbank, die invariante Kultur, also. Siehe <xref:System.Globalization.CultureInfo.InvariantCulture%2A?displayProperty=fullName>.

- Wenn Sie nicht, dass das Ziel des Werts wissen, haben Sie den Datenconsumer oder Anbieter die Kultur angeben.

  Beachten Sie, dass <xref:System.Globalization.CultureInfo.CurrentUICulture%2A?displayProperty=fullName> wird nur verwendet, um lokalisierte Ressourcen abruft, mit einer Instanz von der <xref:System.Resources.ResourceManager?displayProperty=fullName> Klasse.

  Auch wenn das Standardverhalten des überladenen Member für Ihre Anforderungen geeignet ist, ist es besser, die kulturspezifische Überladung explizit aufrufen, so, dass der Code selbsterklärend und einfacher zu verwalten ist.

## <a name="how-to-fix-violations"></a>Behandeln von Verstößen
 Um einen Verstoß gegen diese Regel zu beheben, verwenden Sie die Überladung mit einem <xref:System.Globalization.CultureInfo> oder <xref:System.IFormatProvider> , und geben Sie das Argument, gemäß den Richtlinien, die weiter oben aufgeführt wurden.

## <a name="when-to-suppress-warnings"></a>Wann sollten Warnungen unterdrückt werden?
 Es ist sicher eine Warnung dieser Regel zu unterdrücken, wenn sicher ist, dass der Standardanbieter für die Kultur oder das Format die richtige Wahl ist und die codeverwaltbarkeit von keine wichtige Entwicklungsszenarien Priorität ist.

## <a name="example"></a>Beispiel
 Im folgenden Beispiel `BadMethod` bewirkt, dass zwei Verstöße gegen diese Regel. `GoodMethod` korrigiert den ersten Verstoß durch die invariante Kultur an System.String.Compare übergeben und korrigiert den zweiten Verstoß durch Übergeben der aktuellen Kultur zu <xref:System.String.ToLower%2A> da `string3` wird dem Benutzer angezeigt.

 [!code-csharp[FxCop.Globalization.CultureInfo#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Globalization.CultureInfo/cs/FxCop.Globalization.CultureInfo.cs#1)]

## <a name="example"></a>Beispiel
 Das folgende Beispiel zeigt die Auswirkung der aktuellen Kultur auf dem standardmäßigen <xref:System.IFormatProvider> , wird ausgewählt, die <xref:System.DateTime> Typ.

 [!code-csharp[FxCop.Globalization.IFormatProvider#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Globalization.IFormatProvider/cs/FxCop.Globalization.IFormatProvider.cs#1)]

 Folgende Ergebnisse werden zurückgegeben:

 **6/4/1900 12:15:12 UHR**
**06/04/1900 12:15:12**
## <a name="related-rules"></a>Verwandte Regeln
 [CA1305: IFormatProvider angeben](../code-quality/ca1305-specify-iformatprovider.md)

## <a name="see-also"></a>Siehe auch
 [NIB: Verwenden der CultureInfo-Klasse](https://msdn.microsoft.com/d4329e34-64c3-4d1e-8c73-5b0ee626ba7a)
