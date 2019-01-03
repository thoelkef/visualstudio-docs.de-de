---
title: 'CA2217: Nicht Enumerationen mit FlagsAttribute markieren'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.topic: reference
f1_keywords:
- DoNotMarkEnumsWithFlags
- CA2217
helpviewer_keywords:
- DoNotMarkEnumsWithFlags
- CA2217
dev_langs:
- VB
- CSharp
- CPP
ms.assetid: 1b6f626c-66bf-45b0-a3e2-7c41ee9ceda7
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: d8afe63de8630b3fa7466e8c0784c26ba00bb1ba
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/02/2019
ms.locfileid: "53852478"
---
# <a name="ca2217-do-not-mark-enums-with-flagsattribute"></a>CA2217: Nicht Enumerationen mit FlagsAttribute markieren

|||
|-|-|
|TypeName|DoNotMarkEnumsWithFlags|
|CheckId|CA2217|
|Kategorie|Microsoft.Usage|
|Unterbrechende Änderung|Nicht unterbrechende Änderung|

## <a name="cause"></a>Ursache

Eine extern sichtbare Enumeration wird mit markiert <xref:System.FlagsAttribute>, und sie verfügt über einen oder mehr Werte, die keine Potenzen von 2 oder eine Kombination aus anderen sind Werte für die Enumeration definiert.

## <a name="rule-description"></a>Regelbeschreibung

Eine Enumeration müssen <xref:System.FlagsAttribute> vorhanden, nur, wenn jeder in der Enumeration definierte Wert eine Potenz von zwei oder eine Kombination von definierten Werte.

## <a name="how-to-fix-violations"></a>Behandeln von Verstößen

Um einen Verstoß gegen diese Regel zu beheben, entfernen Sie <xref:System.FlagsAttribute> aus der Enumeration.

## <a name="when-to-suppress-warnings"></a>Wenn Sie Warnungen unterdrücken

Unterdrücken Sie keine Warnung dieser Regel.

## <a name="example-that-should-not-have-the-attribute"></a>Beispiel, in dem das Attribut keinen sollten

Das folgende Beispiel zeigt eine Enumeration, `Color`, den Wert 3 enthält. 3 ist keine Potenz von 2 oder eine Kombination der definierten Werte. Die `Color` Enumeration darf nicht mit markiert werden <xref:System.FlagsAttribute>.

[!code-cpp[FxCop.Usage.EnumNoFlags#1](../code-quality/codesnippet/CPP/ca2217-do-not-mark-enums-with-flagsattribute_1.cpp)]
[!code-csharp[FxCop.Usage.EnumNoFlags#1](../code-quality/codesnippet/CSharp/ca2217-do-not-mark-enums-with-flagsattribute_1.cs)]
[!code-vb[FxCop.Usage.EnumNoFlags#1](../code-quality/codesnippet/VisualBasic/ca2217-do-not-mark-enums-with-flagsattribute_1.vb)]

## <a name="example-that-should-have-the-attribute"></a>Beispiel mit dem Attribut enthalten soll

Das folgende Beispiel zeigt eine Enumeration, `Days`, erfüllt die Anforderungen für die Markierung mit <xref:System.FlagsAttribute>.

[!code-cpp[FxCop.Usage.EnumNoFlags2#1](../code-quality/codesnippet/CPP/ca2217-do-not-mark-enums-with-flagsattribute_2.cpp)]
[!code-csharp[FxCop.Usage.EnumNoFlags2#1](../code-quality/codesnippet/CSharp/ca2217-do-not-mark-enums-with-flagsattribute_2.cs)]
[!code-vb[FxCop.Usage.EnumNoFlags2#1](../code-quality/codesnippet/VisualBasic/ca2217-do-not-mark-enums-with-flagsattribute_2.vb)]

## <a name="related-rules"></a>Verwandte Regeln

[CA1027: Enumerationen mit FlagsAttribute markieren](../code-quality/ca1027-mark-enums-with-flagsattribute.md)

## <a name="see-also"></a>Siehe auch

- <xref:System.FlagsAttribute?displayProperty=fullName>
