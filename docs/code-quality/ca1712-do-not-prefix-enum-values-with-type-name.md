---
title: 'CA1712: Keine Typnamen als Präfixe für Enumerationswerte verwenden.'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- CA1712
- DoNotPrefixEnumValuesWithTypeName
helpviewer_keywords:
- CA1712
- DoNotPrefixEnumValuesWithTypeName
ms.assetid: df0e3a12-67bf-48f1-a10b-2ef60484a5c7
author: gewarren
ms.author: gewarren
manager: jillfra
dev_langs:
- CPP
- CSharp
- VB
ms.workload:
- multiple
ms.openlocfilehash: 323025eb03d2a949a970659aba2357c01ed8bfab
ms.sourcegitcommit: 5216c15e9f24d1d5db9ebe204ee0e7ad08705347
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/09/2019
ms.locfileid: "68921764"
---
# <a name="ca1712-do-not-prefix-enum-values-with-type-name"></a>CA1712: Keine Typnamen als Präfixe für Enumerationswerte verwenden.

|||
|-|-|
|TypeName|DoNotPrefixEnumValuesWithTypeName|
|CheckId|CA1712|
|Kategorie|Microsoft.Naming|
|Unterbrechende Änderung|Breaking|

## <a name="cause"></a>Ursache
Eine Enumeration enthält einen Member, dessen Name mit dem Typnamen der Enumeration beginnt.

## <a name="rule-description"></a>Regelbeschreibung
Namen von Enumerationsmembern haben nicht den Typnamen als Präfix, da von den Entwicklungs Tools Typinformationen erwartet werden.

Durch Benennungskonventionen erhalten Bibliotheken, die auf die Common Language Runtime abzielen, ein einheitliches Erscheinungsbild. Dies reduziert die Zeit, die erforderlich ist, um eine neue Software Bibliothek kennenzulernen, und steigert das Kunden Vertrauen, dass die Bibliothek von einem Benutzer entwickelt wurde, der über Kenntnisse in der Entwicklung von verwaltetem Code verfügt.

## <a name="how-to-fix-violations"></a>Behandeln von Verstößen
Um einen Verstoß gegen diese Regel zu beheben, entfernen Sie das Typnamen Präfix aus dem-Enumerationsmember.

## <a name="when-to-suppress-warnings"></a>Wann sollten Warnungen unterdrückt werden?
Unterdrücken Sie keine Warnung dieser Regel.

## <a name="example"></a>Beispiel
Das folgende Beispiel zeigt eine falsch benannte Enumeration, gefolgt von der korrigierten Version.

[!code-csharp[FxCop.Naming.EnumValues#1](../code-quality/codesnippet/CSharp/ca1712-do-not-prefix-enum-values-with-type-name_1.cs)]
[!code-cpp[FxCop.Naming.EnumValues#1](../code-quality/codesnippet/CPP/ca1712-do-not-prefix-enum-values-with-type-name_1.cpp)]
[!code-vb[FxCop.Naming.EnumValues#1](../code-quality/codesnippet/VisualBasic/ca1712-do-not-prefix-enum-values-with-type-name_1.vb)]

## <a name="related-rules"></a>Verwandte Regeln
[CA1711: Bezeichner sollten kein falsches Suffix aufweisen](../code-quality/ca1711-identifiers-should-not-have-incorrect-suffix.md)

[CA1027: Markierungen mit FlagsAttribute markieren](../code-quality/ca1027-mark-enums-with-flagsattribute.md)

[CA2217: Auffüge Zeichen nicht mit FlagsAttribute markieren](../code-quality/ca2217-do-not-mark-enums-with-flagsattribute.md)

## <a name="see-also"></a>Siehe auch

- <xref:System.Enum?displayProperty=fullName>