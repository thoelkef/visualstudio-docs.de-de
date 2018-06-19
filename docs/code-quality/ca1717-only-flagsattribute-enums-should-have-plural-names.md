---
title: 'CA1717: Nur FlagsAttribute-Enumerationen sollten Pluralnamen aufweisen'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA1717
- OnlyFlagsEnumsShouldHavePluralNames
helpviewer_keywords:
- OnlyFlagsEnumsShouldHavePluralNames
- CA1717
ms.assetid: a6855d8b-d78a-42c1-834e-61c31f5572ed
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 93cc4b36372d1e5ef6c81f16dc74285c336d08cc
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/26/2018
ms.locfileid: "31914574"
---
# <a name="ca1717-only-flagsattribute-enums-should-have-plural-names"></a>CA1717: Nur FlagsAttribute-Enumerationen sollten Pluralnamen aufweisen
|||
|-|-|
|TypeName|OnlyFlagsEnumsShouldHavePluralNames|
|CheckId|CA1717|
|Kategorie|Microsoft.Naming|
|Unterbrechende Änderung|Breaking|

## <a name="cause"></a>Ursache
 Der Name einer extern sichtbare Enumeration in Pluralform endet und die Enumeration ist nicht mit markiert die <xref:System.FlagsAttribute?displayProperty=fullName> Attribut.

## <a name="rule-description"></a>Regelbeschreibung
 Durch Benennungskonventionen vorgibt, dass für ein Pluralname für eine Enumeration gibt an, dass die Enumeration mehrere Werte gleichzeitig angegeben werden kann. Die <xref:System.FlagsAttribute> werden Compiler angewiesen, die Enumeration als Bitfeld, das bitweise Operationen für die Enumeration ermöglicht behandelt werden sollen.

 Wenn nur ein Wert einer Enumeration zu einem Zeitpunkt angegeben werden kann, sollte der Name der Enumeration Singularform sein. Beispielsweise kann eine Enumeration, die die Tage der Woche definiert vorgesehen werden für die Verwendung in einer Anwendung, in dem Sie mehrere Tage angeben. Diese Enumeration müssen den <xref:System.FlagsAttribute> und 'Days' aufgerufen werden. Eine ähnliche-Enumeration, die nur einen einzigen Tag angegeben werden kann keine das Attribut, und möglicherweise 'Day' aufgerufen.

 Durch Benennungskonventionen erhalten Bibliotheken, die auf die Common Language Runtime abzielen, ein einheitliches Erscheinungsbild. Dies reduziert die Zeit, die ist erforderlich, um eine neue Softwarebibliothek Informationen zu erhalten, zudem wird, dass die Bibliothek von einem Benutzer, Kenntnisse in der Entwicklung von verwaltetem Code hat.

## <a name="how-to-fix-violations"></a>Behandeln von Verstößen
 Ändern Sie dem Namen der Enumeration Singularform, oder fügen die <xref:System.FlagsAttribute>.

## <a name="when-to-suppress-warnings"></a>Wann sollten Warnungen unterdrückt werden?
 Sie können ruhig auf eine Warnung von der Regel zu unterdrücken, sofern der Name in Singularform endet.

## <a name="related-rules"></a>Verwandte Regeln
 [CA1714: Flags-Enumerationen sollten Pluralnamen aufweisen](../code-quality/ca1714-flags-enums-should-have-plural-names.md)

 [CA1027: Enumerationen mit FlagsAttribute markieren](../code-quality/ca1027-mark-enums-with-flagsattribute.md)

 [CA2217: Enumerationen nicht mit FlagsAttribute markieren](../code-quality/ca2217-do-not-mark-enums-with-flagsattribute.md)

## <a name="see-also"></a>Siehe auch
 <xref:System.FlagsAttribute?displayProperty=fullName> [Enum-Entwurf](/dotnet/standard/design-guidelines/enum)