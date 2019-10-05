---
title: 'CA1014: Assemblys mit CLSCompliantAttribute markieren.'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- CA1014
- MarkAssembliesWithClsCompliant
helpviewer_keywords:
- CA1014
- MarkAssembliesWithClsCompliant
ms.assetid: 4fe57449-cf45-4745-bcd2-6345f1ed266d
author: gewarren
ms.author: gewarren
manager: jillfra
dev_langs:
- CPP
- CSharp
- VB
ms.workload:
- multiple
ms.openlocfilehash: 387eb464959fba522e31f9586998335cb306d844
ms.sourcegitcommit: 0c2523d975d48926dd2b35bcd2d32a8ae14c06d8
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/24/2019
ms.locfileid: "71236330"
---
# <a name="ca1014-mark-assemblies-with-clscompliantattribute"></a>CA1014: Assemblys mit CLSCompliantAttribute markieren.

|||
|-|-|
|TypeName|MarkAssembliesWithClsCompliant|
|CheckId|CA1014|
|Kategorie|Microsoft.Design|
|Unterbrechende Änderung|Nicht unterbrechend|

## <a name="cause"></a>Ursache
Auf eine Assembly wird das <xref:System.CLSCompliantAttribute?displayProperty=fullName> -Attribut nicht angewendet.

## <a name="rule-description"></a>Regelbeschreibung
In der Common Language Specification (CLS) sind Benennungseinschränkungen, Datentypen und Regeln definiert, denen Assemblys entsprechen müssen, wenn sie in verschiedenen Programmiersprachen verwendet werden sollen. Ein guter Entwurf bedeutet, dass alle Assemblys explizit die <xref:System.CLSCompliantAttribute>CLS-Konformität mit angeben. Wenn das Attribut in einer Assembly nicht vorhanden ist, ist die Assembly nicht kompatibel.

Eine CLS-kompatible Assembly kann Typen oder Typmember enthalten, die nicht konform sind.

## <a name="how-to-fix-violations"></a>Behandeln von Verstößen
Fügen Sie der Assembly das-Attribut hinzu, um einen Verstoß gegen diese Regel zu beheben. Anstatt die gesamte Assembly als nicht kompatibel zu markieren, sollten Sie bestimmen, welche Typen oder Typmember nicht kompatibel sind, und diese Elemente als solche markieren. Wenn möglich, sollten Sie eine CLS-kompatible Alternative für nicht kompatible Member bereitstellen, damit die größtmögliche Zielgruppe auf die gesamte Funktionalität Ihrer Assembly zugreifen kann.

## <a name="when-to-suppress-warnings"></a>Wann sollten Warnungen unterdrückt werden?
Unterdrücken Sie keine Warnung dieser Regel. Wenn Sie nicht möchten, dass die Assembly kompatibel ist, wenden Sie das-Attribut an, und `false`legen Sie dessen Wert auf fest.

## <a name="example"></a>Beispiel
Das folgende Beispiel zeigt eine Assembly, für die <xref:System.CLSCompliantAttribute?displayProperty=fullName> das-Attribut angewendet wurde, das CLS-kompatibel deklariert.

[!code-csharp[FxCop.Design.AssembliesCls#1](../code-quality/codesnippet/CSharp/ca1014-mark-assemblies-with-clscompliantattribute_1.cs)]
[!code-cpp[FxCop.Design.AssembliesCls#1](../code-quality/codesnippet/CPP/ca1014-mark-assemblies-with-clscompliantattribute_1.cpp)]
[!code-vb[FxCop.Design.AssembliesCls#1](../code-quality/codesnippet/VisualBasic/ca1014-mark-assemblies-with-clscompliantattribute_1.vb)]

## <a name="see-also"></a>Siehe auch

- <xref:System.CLSCompliantAttribute?displayProperty=fullName>
- [Sprachunabhängigkeit und sprachunabhängige Komponenten](/dotnet/standard/language-independence-and-language-independent-components)