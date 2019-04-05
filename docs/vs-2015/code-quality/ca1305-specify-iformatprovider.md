---
title: 'CA1305: IFormatProvider angeben | Microsoft-Dokumentation'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- SpecifyIFormatProvider
- CA1305
helpviewer_keywords:
- CA1305
- SpecifyIFormatProvider
ms.assetid: fb34ed9a-4eab-47cc-8eef-3068a4a1397e
caps.latest.revision: 24
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: a31dfbae3ca07f913a5ddad3cf0a788cd9c62b73
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/23/2019
ms.locfileid: "58956116"
---
# <a name="ca1305-specify-iformatprovider"></a>CA1305: IFormatProvider angeben.
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|SpecifyIFormatProvider|
|CheckId|CA1305|
|Kategorie|Microsoft.Globalization|
|Unterbrechende Änderung|Nicht unterbrechend|

## <a name="cause"></a>Ursache
 Eine Methode oder ein Konstruktor ruft ein oder mehrere Elemente, deren Überladungen akzeptieren einen <xref:System.IFormatProvider?displayProperty=fullName> -Parameter, und die Methode oder der Konstruktor ruft nicht die Überladung, akzeptiert die <xref:System.IFormatProvider> Parameter. Dieser Regel werden ignoriert, Aufrufe von [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] ignorieren, beschriebenen Methoden die <xref:System.IFormatProvider> Parameter und außerdem die folgenden Methoden:

-   <xref:System.Activator.CreateInstance%2A?displayProperty=fullName>

-   <xref:System.Resources.ResourceManager.GetObject%2A?displayProperty=fullName>

-   <xref:System.Resources.ResourceManager.GetString%2A?displayProperty=fullName>

## <a name="rule-description"></a>Regelbeschreibung
 Wenn eine <xref:System.Globalization.CultureInfo?displayProperty=fullName> oder <xref:System.IFormatProvider> Objekt ist nicht angegeben, der Standardwert, der vom überladenen Member bereitgestellte ist möglicherweise nicht die in allen Gebietsschemas den gewünschten Effekt. Darüber hinaus [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] Membern die Standardkultur Auswahl und Formatierung basierend auf Annahmen, die möglicherweise nicht korrekt für Ihren Code. Um sicherzustellen, dass der Code ordnungsgemäß für Ihre Szenarien funktioniert, sollten Sie die kulturspezifische Informationen, anhand der folgenden Richtlinien angeben:

- Wenn der Wert für den Benutzer angezeigt wird, wird verwenden Sie die aktuelle Kultur. Siehe <xref:System.Globalization.CultureInfo.CurrentCulture%2A?displayProperty=fullName>.

- Wenn der Wert gespeichert und von Software (persistent in einer Datei oder Datenbank) zugegriffen werden, die verwenden Sie die invariante Kultur. Siehe <xref:System.Globalization.CultureInfo.InvariantCulture%2A?displayProperty=fullName>.

- Wenn Sie nicht, dass das Ziel des Werts wissen, haben Sie den Datenconsumer oder Anbieter die Kultur angeben.

  Beachten Sie, dass <xref:System.Globalization.CultureInfo.CurrentUICulture%2A?displayProperty=fullName> wird nur verwendet, um lokalisierte Ressourcen abruft, mit einer Instanz von der <xref:System.Resources.ResourceManager?displayProperty=fullName> Klasse.

  Auch wenn das Standardverhalten des überladenen Member für Ihre Anforderungen geeignet ist, ist es besser, die kulturspezifische Überladung explizit aufrufen, so, dass der Code selbsterklärend und einfacher zu verwalten ist.

## <a name="how-to-fix-violations"></a>Behandeln von Verstößen
 Um einen Verstoß gegen diese Regel zu beheben, verwenden Sie die Überladung mit einem <xref:System.Globalization.CultureInfo> oder <xref:System.IFormatProvider> , und geben Sie das Argument, gemäß den Richtlinien, die weiter oben aufgeführt wurden.

## <a name="when-to-suppress-warnings"></a>Wann sollten Warnungen unterdrückt werden?
 Es ist sicher, um eine Warnung dieser Regel zu unterdrücken, wenn sicher ist, dass der Standardanbieter für die Kultur oder das Format ist die richtige Wahl und, wenn die codeverwaltbarkeit von keine wichtige Entwicklungsszenarien Priorität ist.

## <a name="example"></a>Beispiel
 Im folgenden Beispiel `BadMethod` bewirkt, dass zwei Verstöße gegen diese Regel. `GoodMethod` korrigiert den ersten Verstoß durch Übergeben der invarianten Kultur, <xref:System.String.Compare%2A>, und diese gegebenenfalls korrigiert des zweiten Verstoßes durch Übergeben der aktuellen Kultur zu <xref:System.String.ToLower%2A> da `string3` wird dem Benutzer angezeigt.

 [!code-csharp[FxCop.Globalization.CultureInfo#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Globalization.CultureInfo/cs/FxCop.Globalization.CultureInfo.cs#1)]

## <a name="example"></a>Beispiel
 Das folgende Beispiel zeigt die Auswirkung der aktuellen Kultur auf dem standardmäßigen <xref:System.IFormatProvider> , wird ausgewählt, die <xref:System.DateTime> Typ.

 [!code-csharp[FxCop.Globalization.IFormatProvider#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Globalization.IFormatProvider/cs/FxCop.Globalization.IFormatProvider.cs#1)]

 Folgende Ergebnisse werden zurückgegeben:

 **6/4/1900 12:15:12 UHR**
**06/04/1900 12:15:12**
## <a name="related-rules"></a>Verwandte Regeln
 [CA1304: CultureInfo angeben](../code-quality/ca1304-specify-cultureinfo.md)

## <a name="see-also"></a>Siehe auch
 [NIB: Verwenden der CultureInfo-Klasse](http://msdn.microsoft.com/d4329e34-64c3-4d1e-8c73-5b0ee626ba7a)
