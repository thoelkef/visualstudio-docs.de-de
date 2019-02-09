---
title: 'CA1027: Enumerationen mit FlagsAttribute markieren.'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- MarkEnumsWithFlags
- CA1027
helpviewer_keywords:
- CA1027
- MarkEnumsWithFlags
ms.assetid: 249e882c-8cd1-4c00-a2de-7b6bdc1849ff
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 185ff6a133fdb990e350d5d5737a40a27c24d588
ms.sourcegitcommit: 21d667104199c2493accec20c2388cf674b195c3
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2019
ms.locfileid: "55935263"
---
# <a name="ca1027-mark-enums-with-flagsattribute"></a>CA1027: Enumerationen mit FlagsAttribute markieren.

|||
|-|-|
|TypeName|MarkEnumsWithFlags|
|CheckId|CA1027|
|Kategorie|Microsoft.Design|
|Unterbrechende Änderung|Nicht unterbrechend|

## <a name="cause"></a>Ursache
 Die Werte der eine öffentliche Enumeration sind Potenzen von 2 oder Kombinationen von anderen Werten, die in der Enumeration definiert sind und die <xref:System.FlagsAttribute?displayProperty=fullName> Attribut ist nicht vorhanden. Um falsch positive Ergebnisse zu reduzieren, meldet diese Regel keinen Verstoß für Enumerationen, die aufeinander folgender Werte aufweisen.

## <a name="rule-description"></a>Regelbeschreibung
 Eine Enumeration ist ein Werttyp, der einen Satz verwandter benannter Konstanten definiert. Anwenden <xref:System.FlagsAttribute> auf eine Enumeration, wenn deren benannten Konstanten sinnvoll kombiniert werden können. Betrachten Sie beispielsweise eine Enumeration der Tage der Woche in einer Anwendung, die überwacht die Tag-Ressourcen verfügbar sind. Wenn die Verfügbarkeit der einzelnen Ressourcen codiert ist, mit der Enumeration, die <xref:System.FlagsAttribute> vorhanden, eine beliebige Kombination von Tagen dargestellt werden kann. Ohne das Attribut kann nur ein Tag der Woche dargestellt werden.

 Für Felder, die mit den flexibel kombinierbaren Enumerationen zu speichern, werden die einzelnen Enumerationswerte als Gruppen von Bits in das Feld behandelt. Aus diesem Grund diese Felder werden manchmal als bezeichnet *Bitfelder*. Enumerationswerte für die Speicherung in einem Bitfeld zu kombinieren, verwenden Sie die boolesche bedingten Operatoren. Verwenden Sie die booleschen logischen Operatoren, zum Testen ein Bitfeld, um festzustellen, ob ein bestimmtes Enumerationswert vorhanden ist. Für ein Bitfeld zum Speichern und Abrufen von kombinierten Enumerationswerte ordnungsgemäß muss jeder Wert, der in der Enumeration definiert ist, eine Potenz von zwei sein. Wenn dies der Fall ist, werden die booleschen logischen Operatoren nicht extrahieren, die einzelnen Enumerationswerte, die in das Feld gespeichert werden.

## <a name="how-to-fix-violations"></a>Behandeln von Verstößen
 Um einen Verstoß gegen diese Regel zu beheben, fügen <xref:System.FlagsAttribute> der Enumeration.

## <a name="when-to-suppress-warnings"></a>Wenn Sie Warnungen unterdrücken
 Unterdrücken Sie eine Warnung dieser Regel, wenn Sie nicht, dass die Enumerationswerte kombinierbar sein möchten.

## <a name="example"></a>Beispiel
 Im folgenden Beispiel `DaysEnumNeedsFlags` ist eine Enumeration, die erfüllt die Anforderungen für die Verwendung von <xref:System.FlagsAttribute>, aber nicht vorhanden. Die `ColorEnumShouldNotHaveFlag` Enumeration keine Werte, die Potenzen von 2 sind, aber falsch gibt <xref:System.FlagsAttribute>. Dies verstößt gegen die Regel [CA2217: Nicht Enumerationen mit FlagsAttribute markieren](../code-quality/ca2217-do-not-mark-enums-with-flagsattribute.md).

 [!code-csharp[FxCop.Design.EnumFlags#1](../code-quality/codesnippet/CSharp/ca1027-mark-enums-with-flagsattribute_1.cs)]

## <a name="related-rules"></a>Verwandte Regeln
 [CA2217: Nicht Enumerationen mit FlagsAttribute markieren](../code-quality/ca2217-do-not-mark-enums-with-flagsattribute.md)

## <a name="see-also"></a>Siehe auch
 <xref:System.FlagsAttribute?displayProperty=fullName>