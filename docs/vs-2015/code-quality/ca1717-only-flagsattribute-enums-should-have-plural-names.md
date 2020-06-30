---
title: 'CA1717: Nur FlagsAttribute-Enumerationen sollten Plural Namen aufweisen. Microsoft-Dokumentation'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA1717
- OnlyFlagsEnumsShouldHavePluralNames
helpviewer_keywords:
- OnlyFlagsEnumsShouldHavePluralNames
- CA1717
ms.assetid: a6855d8b-d78a-42c1-834e-61c31f5572ed
caps.latest.revision: 19
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: c58c218991226a954185853097dc81da36c69ed6
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/30/2020
ms.locfileid: "85543688"
---
# <a name="ca1717-only-flagsattribute-enums-should-have-plural-names"></a>CA1717: Nur FlagsAttribute-Enumerationen sollten Pluralnamen aufweisen.
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|Element|Wert|
|-|-|
|TypName|OnlyFlagsEnumsShouldHavePluralNames|
|CheckId|CA1717|
|Category|Microsoft.Naming|
|Unterbrechende Änderung|Breaking|

## <a name="cause"></a>Ursache
 Der Name einer extern sichtbaren Enumeration endet in einem Plural Wort, und die Enumeration ist nicht mit dem- <xref:System.FlagsAttribute?displayProperty=fullName> Attribut gekennzeichnet.

## <a name="rule-description"></a>Beschreibung der Regel
 Benennungs Konventionen legen fest, dass ein Plural Name für eine Enumeration angibt, dass mehr als ein Wert der Enumeration gleichzeitig angegeben werden kann. Der <xref:System.FlagsAttribute> weist Compiler an, dass die Enumeration als Bitfeld behandelt werden soll, das bitweise Operationen für die Enumeration ermöglicht.

 Wenn nur ein Wert einer Enumeration gleichzeitig angegeben werden kann, sollte der Name der Enumeration ein einzelnes Wort sein. Beispielsweise kann eine Enumeration, die die Wochentage definiert, für die Verwendung in einer Anwendung bestimmt werden, in der Sie mehrere Tage angeben können. Diese Enumeration sollte den <xref:System.FlagsAttribute> und den Namen "Days" aufweisen. Eine ähnliche Enumeration, die zulässt, dass nur ein einzelner Tag angegeben wird, verfügt nicht über das-Attribut und könnte als "Day" bezeichnet werden.

 Durch Benennungskonventionen erhalten Bibliotheken, die auf die Common Language Runtime abzielen, ein einheitliches Erscheinungsbild. Dies reduziert die Zeit, die erforderlich ist, um eine neue Software Bibliothek kennenzulernen, und steigert das Kunden Vertrauen, dass die Bibliothek von einem Benutzer entwickelt wurde, der über Kenntnisse in der Entwicklung von verwaltetem Code verfügt.

## <a name="how-to-fix-violations"></a>Behandeln von Verstößen
 Geben Sie den Namen der Enumeration als Singular Wort an, oder fügen Sie hinzu <xref:System.FlagsAttribute> .

## <a name="when-to-suppress-warnings"></a>Wann sollten Warnungen unterdrückt werden?
 Es ist sicher, eine Warnung aus der Regel zu unterdrücken, wenn der Name auf ein einzelnes Wort endet.

## <a name="related-rules"></a>Verwandte Regeln
 [CA1714: Flags-Enumerationen sollten Pluralnamen aufweisen.](../code-quality/ca1714-flags-enums-should-have-plural-names.md)

 [CA1027: Enumerationen mit FlagsAttribute markieren.](../code-quality/ca1027-mark-enums-with-flagsattribute.md)

 [CA2217: Enumerationen nicht mit FlagsAttribute markieren.](../code-quality/ca2217-do-not-mark-enums-with-flagsattribute.md)

## <a name="see-also"></a>Weitere Informationen
 <xref:System.FlagsAttribute?displayProperty=fullName>Aufzählungs [Design](https://msdn.microsoft.com/library/dd53c952-9d9a-4736-86ff-9540e815d545)
