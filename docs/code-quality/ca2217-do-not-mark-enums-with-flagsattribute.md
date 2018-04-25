---
title: 'CA2217: Enumerationen nicht mit FlagsAttribute markieren'
ms.date: 11/04/2016
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- DoNotMarkEnumsWithFlags
- CA2217
helpviewer_keywords:
- DoNotMarkEnumsWithFlags
- CA2217
ms.assetid: 1b6f626c-66bf-45b0-a3e2-7c41ee9ceda7
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 1aaa080aaa238f15cbcedefd9302d23758948d77
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/19/2018
---
# <a name="ca2217-do-not-mark-enums-with-flagsattribute"></a>CA2217: Enumerationen nicht mit FlagsAttribute markieren
|||
|-|-|
|TypeName|DoNotMarkEnumsWithFlags|
|CheckId|CA2217|
|Kategorie|Microsoft.Usage|
|Unterbrechende Änderung|Nicht unterbrechende Änderung|

## <a name="cause"></a>Ursache
 Eine extern sichtbare Enumeration wird mit gekennzeichnet <xref:System.FlagsAttribute> und verfügt über ein oder mehr Werte, die keine Potenzen von 2 oder eine Kombination aus den anderen sind Werte für die Enumeration definiert.

## <a name="rule-description"></a>Regelbeschreibung
 Eine Enumeration müssen <xref:System.FlagsAttribute> vorhanden, nur, wenn jeder Wert, der in der Enumeration definiert, eine Potenz von zwei ist oder eine Kombination aus Werte definierten.

## <a name="how-to-fix-violations"></a>Behandeln von Verstößen
 Um einen Verstoß gegen diese Regel zu beheben, entfernen Sie <xref:System.FlagsAttribute> aus der Enumeration.

## <a name="when-to-suppress-warnings"></a>Wann sollten Warnungen unterdrückt werden?
 Unterdrücken Sie keine Warnung dieser Regel.

## <a name="example"></a>Beispiel
 Das folgende Beispiel zeigt eine Enumeration, die Farbe, mit dem Wert 3, also weder eine Potenz von 2 noch eine Kombination der definierten Werte. Die Color-Enumeration sollten nicht gekennzeichnet werden, mit der <xref:System.FlagsAttribute>.

 [!code-cpp[FxCop.Usage.EnumNoFlags#1](../code-quality/codesnippet/CPP/ca2217-do-not-mark-enums-with-flagsattribute_1.cpp)]
 [!code-csharp[FxCop.Usage.EnumNoFlags#1](../code-quality/codesnippet/CSharp/ca2217-do-not-mark-enums-with-flagsattribute_1.cs)]
 [!code-vb[FxCop.Usage.EnumNoFlags#1](../code-quality/codesnippet/VisualBasic/ca2217-do-not-mark-enums-with-flagsattribute_1.vb)]

## <a name="example"></a>Beispiel
 Das folgende Beispiel zeigt eine Enumeration, Tage, die die Anforderungen für eine mit das System.FlagsAttribute markiert werden erfüllt.

 [!code-cpp[FxCop.Usage.EnumNoFlags2#1](../code-quality/codesnippet/CPP/ca2217-do-not-mark-enums-with-flagsattribute_2.cpp)]
 [!code-csharp[FxCop.Usage.EnumNoFlags2#1](../code-quality/codesnippet/CSharp/ca2217-do-not-mark-enums-with-flagsattribute_2.cs)]
 [!code-vb[FxCop.Usage.EnumNoFlags2#1](../code-quality/codesnippet/VisualBasic/ca2217-do-not-mark-enums-with-flagsattribute_2.vb)]

## <a name="related-rules"></a>Verwandte Regeln
 [CA1027: Enumerationen mit FlagsAttribute markieren](../code-quality/ca1027-mark-enums-with-flagsattribute.md)

## <a name="see-also"></a>Siehe auch
 <xref:System.FlagsAttribute?displayProperty=fullName>