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
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 299e8bfec526dc3a5e8dc166d9ab405d51037cbe
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/19/2019
ms.locfileid: "72661441"
---
# <a name="ca1305-specify-iformatprovider"></a>CA1305: IFormatProvider angeben
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|SpecifyIFormatProvider|
|CheckId|CA1305|
|Kategorie|Microsoft.Globalization|
|Unterbrechende Änderung|Nicht unterbrechend|

## <a name="cause"></a>Ursache
 Eine Methode oder ein Konstruktor ruft einen oder mehrere Member mit über Ladungen auf, die einen <xref:System.IFormatProvider?displayProperty=fullName> Parameter akzeptieren, und die Methode oder der Konstruktor ruft nicht die Überladung auf, die den <xref:System.IFormatProvider>-Parameter annimmt. Diese Regel ignoriert Aufrufe von [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] Methoden, die als ignorieren des <xref:System.IFormatProvider>-Parameters dokumentiert sind, und zusätzlich die folgenden Methoden:

- <xref:System.Activator.CreateInstance%2A?displayProperty=fullName>

- <xref:System.Resources.ResourceManager.GetObject%2A?displayProperty=fullName>

- <xref:System.Resources.ResourceManager.GetString%2A?displayProperty=fullName>

## <a name="rule-description"></a>Regelbeschreibung
 Wenn keine <xref:System.Globalization.CultureInfo?displayProperty=fullName> oder <xref:System.IFormatProvider> Objekt bereitgestellt wird, hat der Standardwert, der vom überladenen Member bereitgestellt wird, möglicherweise nicht die gewünschte Auswirkung in allen Gebiets Schemas. Außerdem wählen [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] Mitglieder Standard Kultur und-Formatierung basierend auf Annahmen aus, die für Ihren Code möglicherweise nicht korrekt sind. Um sicherzustellen, dass der Code für Ihre Szenarien erwartungsgemäß funktioniert, sollten Sie kulturspezifische Informationen gemäß den folgenden Richtlinien angeben:

- Wenn der Wert für den Benutzer angezeigt wird, verwenden Sie die aktuelle Kultur. Siehe <xref:System.Globalization.CultureInfo.CurrentCulture%2A?displayProperty=fullName>.

- Wenn der Wert von Software (persistent in einer Datei oder Datenbank) gespeichert wird und darauf zugegriffen wird, verwenden Sie die invariante Kultur. Siehe <xref:System.Globalization.CultureInfo.InvariantCulture%2A?displayProperty=fullName>.

- Wenn Sie das Ziel des Werts nicht kennen, lassen Sie den Datenconsumer oder-Anbieter die Kultur angeben.

  Beachten Sie, dass <xref:System.Globalization.CultureInfo.CurrentUICulture%2A?displayProperty=fullName> nur zum Abrufen lokalisierter Ressourcen mithilfe einer Instanz der <xref:System.Resources.ResourceManager?displayProperty=fullName>-Klasse verwendet wird.

  Auch wenn das Standardverhalten des überladenen Elements für Ihre Bedürfnisse geeignet ist, ist es besser, die kulturspezifische Überladung explizit aufzurufen, sodass Ihr Code selbst dokumentierend und leichter zu pflegen ist.

## <a name="how-to-fix-violations"></a>Behandeln von Verstößen
 Um einen Verstoß gegen diese Regel zu beheben, verwenden Sie die-Überladung, die eine <xref:System.Globalization.CultureInfo> oder <xref:System.IFormatProvider> annimmt, und geben Sie das-Argument gemäß den zuvor aufgelisteten Richtlinien an.

## <a name="when-to-suppress-warnings"></a>Wann sollten Warnungen unterdrückt werden?
 Es ist sicher, eine Warnung aus dieser Regel zu unterdrücken, wenn sicher ist, dass der standardmäßige Kultur-/Formatanbieter die richtige Wahl ist und die Code Wartbarkeit keine wichtige Entwicklungs Priorität darstellt.

## <a name="example"></a>Beispiel
 Im folgenden Beispiel verursacht `BadMethod` zwei Verstöße gegen diese Regel. `GoodMethod` korrigiert den ersten Verstoß, indem die invariante Kultur an <xref:System.String.Compare%2A>übergeben wird, und korrigiert den zweiten Verstoß, indem die aktuelle Kultur an <xref:System.String.ToLower%2A> übergeben wird, da `string3` für den Benutzer angezeigt wird.

 [!code-csharp[FxCop.Globalization.CultureInfo#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Globalization.CultureInfo/cs/FxCop.Globalization.CultureInfo.cs#1)]

## <a name="example"></a>Beispiel
 Das folgende Beispiel zeigt die Auswirkung der aktuellen Kultur auf die Standard <xref:System.IFormatProvider>, die vom <xref:System.DateTime>-Typ ausgewählt wird.

 [!code-csharp[FxCop.Globalization.IFormatProvider#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Globalization.IFormatProvider/cs/FxCop.Globalization.IFormatProvider.cs#1)]

 Folgende Ergebnisse werden zurückgegeben:

 **6/4/1900 12:15:12 Uhr**
**06/04/1900 12:15:12**
## <a name="related-rules"></a>Verwandte Regeln
 [CA1304: CultureInfo angeben](../code-quality/ca1304-specify-cultureinfo.md)

## <a name="see-also"></a>Siehe auch
 [NIB: Verwenden der CultureInfo-Klasse](https://msdn.microsoft.com/d4329e34-64c3-4d1e-8c73-5b0ee626ba7a)
