---
title: 'CA1712: keine Präfixe für Enumerationswerte mit Typname | Microsoft-Dokumentation'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA1712
- DoNotPrefixEnumValuesWithTypeName
helpviewer_keywords:
- CA1712
- DoNotPrefixEnumValuesWithTypeName
ms.assetid: df0e3a12-67bf-48f1-a10b-2ef60484a5c7
caps.latest.revision: 17
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 4773a34ab7112434813990b4d25cbeeb865f3a08
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/30/2020
ms.locfileid: "85543896"
---
# <a name="ca1712-do-not-prefix-enum-values-with-type-name"></a>CA1712: Keine Typnamen als Präfixe für Enumerationswerte verwenden.
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|Element|Wert|
|-|-|
|TypName|DoNotPrefixEnumValuesWithTypeName|
|CheckId|CA1712|
|Category|Microsoft.Naming|
|Unterbrechende Änderung|Breaking|

## <a name="cause"></a>Ursache
 Eine Enumeration enthält einen Member, dessen Name mit dem Typnamen der Enumeration beginnt.

## <a name="rule-description"></a>Beschreibung der Regel
 Namen von Enumerationsmembern haben nicht den Typnamen als Präfix, da von den Entwicklungs Tools Typinformationen erwartet werden.

 Durch Benennungskonventionen erhalten Bibliotheken, die auf die Common Language Runtime abzielen, ein einheitliches Erscheinungsbild. Dies reduziert die Zeit, die erforderlich ist, um eine neue Software Bibliothek kennenzulernen, und steigert das Kunden Vertrauen, dass die Bibliothek von einem Benutzer entwickelt wurde, der über Kenntnisse in der Entwicklung von verwaltetem Code verfügt.

## <a name="how-to-fix-violations"></a>Behandeln von Verstößen
 Um einen Verstoß gegen diese Regel zu beheben, entfernen Sie das Typnamen Präfix aus dem-Enumerationsmember.

## <a name="when-to-suppress-warnings"></a>Wann sollten Warnungen unterdrückt werden?
 Unterdrücken Sie keine Warnung dieser Regel.

## <a name="example"></a>Beispiel
 Das folgende Beispiel zeigt eine falsch benannte Enumeration, gefolgt von der korrigierten Version.

 [!code-cpp[FxCop.Naming.EnumValues#1](../snippets/cpp/VS_Snippets_CodeAnalysis/FxCop.Naming.EnumValues/cpp/FxCop.Naming.EnumValues.cpp#1)]
 [!code-csharp[FxCop.Naming.EnumValues#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Naming.EnumValues/cs/FxCop.Naming.EnumValues.cs#1)]
 [!code-vb[FxCop.Naming.EnumValues#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Naming.EnumValues/vb/FxCop.Naming.EnumValues.vb#1)]

## <a name="related-rules"></a>Verwandte Regeln
 [CA1711: Bezeichner sollten kein falsches Suffix aufweisen.](../code-quality/ca1711-identifiers-should-not-have-incorrect-suffix.md)

 [CA1027: Enumerationen mit FlagsAttribute markieren.](../code-quality/ca1027-mark-enums-with-flagsattribute.md)

 [CA2217: Enumerationen nicht mit FlagsAttribute markieren.](../code-quality/ca2217-do-not-mark-enums-with-flagsattribute.md)

## <a name="see-also"></a>Weitere Informationen
 <xref:System.Enum?displayProperty=fullName>
