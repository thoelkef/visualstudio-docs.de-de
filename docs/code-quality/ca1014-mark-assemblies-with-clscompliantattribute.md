---
title: 'CA1014: Assemblys mit CLSCompliantAttribute markieren.'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
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
ms.openlocfilehash: 3c97d7731cc3bbad98ce5b62346bab1b7d5029ea
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/25/2019
ms.locfileid: "54986643"
---
# <a name="ca1014-mark-assemblies-with-clscompliantattribute"></a>CA1014: Assemblys mit CLSCompliantAttribute markieren.

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
 Um einen Verstoß gegen diese Regel zu beheben, fügen Sie das Attribut auf die Assembly ein. Anstelle von markieren die gesamte Assembly als nicht kompatibel, sollten Sie ermitteln, welchen Typ oder Typmember, nicht kompatibel sind, und markieren diese Elemente entsprechend. Wenn möglich, sollten Sie eine CLS-kompatible Alternative für nicht kompatible Member bereitstellen, damit die größtmögliche Zielgruppe auf alle Funktionen der Assembly zugreifen kann.

## <a name="when-to-suppress-warnings"></a>Wenn Sie Warnungen unterdrücken
 Unterdrücken Sie keine Warnung dieser Regel. Wenn Sie nicht, dass die Assembly kompatibel sein müssen möchten, wenden Sie das Attribut, und setzen ihren Wert auf `false`.

## <a name="example"></a>Beispiel
 Das folgende Beispiel zeigt eine Assembly, die <xref:System.CLSCompliantAttribute?displayProperty=fullName> Attribut angewendet, die CLS-kompatibel deklariert.

 [!code-csharp[FxCop.Design.AssembliesCls#1](../code-quality/codesnippet/CSharp/ca1014-mark-assemblies-with-clscompliantattribute_1.cs)]
 [!code-cpp[FxCop.Design.AssembliesCls#1](../code-quality/codesnippet/CPP/ca1014-mark-assemblies-with-clscompliantattribute_1.cpp)]
 [!code-vb[FxCop.Design.AssembliesCls#1](../code-quality/codesnippet/VisualBasic/ca1014-mark-assemblies-with-clscompliantattribute_1.vb)]

## <a name="see-also"></a>Siehe auch

- <xref:System.CLSCompliantAttribute?displayProperty=fullName>
- [Sprachunabhängigkeit und sprachunabhängige Komponenten](/dotnet/standard/language-independence-and-language-independent-components)