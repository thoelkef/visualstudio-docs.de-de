---
title: 'CA1014: Assemblys mit CLSCompliantAttribute markieren'
ms.date: 11/04/2016
ms.technology: vs-ide-code-analysis
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
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: dc4d1309723fd6a7246d7e684fc91099ea841537
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/19/2018
---
# <a name="ca1014-mark-assemblies-with-clscompliantattribute"></a>CA1014: Assemblys mit CLSCompliantAttribute markieren
|||
|-|-|
|TypeName|MarkAssembliesWithClsCompliant|
|CheckId|CA1014|
|Kategorie|Microsoft.Design|
|Unterbrechende Änderung|Nicht unterbrechend|

## <a name="cause"></a>Ursache
 Eine Assembly verfügt nicht über die <xref:System.CLSCompliantAttribute?displayProperty=fullName> angewendet werden.

## <a name="rule-description"></a>Regelbeschreibung
 In der Common Language Specification (CLS) sind Benennungseinschränkungen, Datentypen und Regeln definiert, denen Assemblys entsprechen müssen, wenn sie in verschiedenen Programmiersprachen verwendet werden sollen. Gute Entwurfsprinzipien verlangen, dass alle Assemblys die CLS-Kompatibilität mit explizit angegeben <xref:System.CLSCompliantAttribute>. Wenn das Attribut nicht auf eine Assembly vorhanden ist, ist die Assembly nicht kompatibel.

 Es ist möglich, dass eine CLS-kompatible Assembly enthalten Typen, oder geben die Elemente, die nicht kompatibel sind.

## <a name="how-to-fix-violations"></a>Behandeln von Verstößen
 Um einen Verstoß gegen diese Regel zu beheben, fügen Sie das Attribut auf die Assembly hinzu. Anstelle von markieren die gesamte Assembly als nicht kompatibel, sollten Sie bestimmen, welchen Typ oder Typmember nicht kompatibel sind, und markieren diese Elemente als solche. Wenn möglich, sollten Sie eine CLS-kompatible Alternative für nicht kompatible Member bereitstellen, sodass größtmögliche Zielgruppe alle Funktionen der Assembly zugreifen kann.

## <a name="when-to-suppress-warnings"></a>Wann sollten Warnungen unterdrückt werden?
 Unterdrücken Sie keine Warnung dieser Regel. Wenn Sie nicht, dass die Assembly kompatibel sein müssen möchten, wenden Sie das Attribut, und legen Sie dessen Wert auf `false`.

## <a name="example"></a>Beispiel
 Das folgende Beispiel zeigt eine Assembly, die <xref:System.CLSCompliantAttribute?displayProperty=fullName> Attribut angewendet, die CLS-kompatibel deklariert.

 [!code-csharp[FxCop.Design.AssembliesCls#1](../code-quality/codesnippet/CSharp/ca1014-mark-assemblies-with-clscompliantattribute_1.cs)]
 [!code-cpp[FxCop.Design.AssembliesCls#1](../code-quality/codesnippet/CPP/ca1014-mark-assemblies-with-clscompliantattribute_1.cpp)]
 [!code-vb[FxCop.Design.AssembliesCls#1](../code-quality/codesnippet/VisualBasic/ca1014-mark-assemblies-with-clscompliantattribute_1.vb)]

## <a name="see-also"></a>Siehe auch
 <xref:System.CLSCompliantAttribute?displayProperty=fullName> [Sprachenunabhängigkeit und sprachunabhängige Komponenten](/dotnet/standard/language-independence-and-language-independent-components)