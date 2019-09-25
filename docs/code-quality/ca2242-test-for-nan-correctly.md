---
title: 'CA2242: Ordnungsgemäß auf NaN testen.'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- TestForNaNCorrectly
- CA2242
helpviewer_keywords:
- CA2242
ms.assetid: e12dcffc-e255-4e1e-8fdf-3c6054d44abe
author: gewarren
ms.author: gewarren
manager: jillfra
dev_langs:
- CSharp
- VB
ms.workload:
- multiple
ms.openlocfilehash: 0e74ec49667a4fe66c399bd15e8b24aa6589ce88
ms.sourcegitcommit: 0c2523d975d48926dd2b35bcd2d32a8ae14c06d8
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/24/2019
ms.locfileid: "71237840"
---
# <a name="ca2242-test-for-nan-correctly"></a>CA2242: Ordnungsgemäß auf NaN testen.

|||
|-|-|
|TypeName|TestForNaNCorrectly|
|CheckId|CA2242|
|Kategorie|Microsoft.Usage|
|Unterbrechende Änderung|Nicht unterbrechend|

## <a name="cause"></a>Ursache
Ein Ausdruck testet einen Wert <xref:System.Single.NaN?displayProperty=fullName> mit oder. <xref:System.Double.NaN?displayProperty=fullName>

## <a name="rule-description"></a>Regelbeschreibung
 <xref:System.Double.NaN?displayProperty=fullName>, das not-a-Number-Ergebnisse darstellt, wenn eine arithmetische Operation nicht definiert ist. Jeder Ausdruck, der die Gleichheit zwischen einem Wert <xref:System.Double.NaN?displayProperty=fullName> testet und `false`immer zurückgibt. Jeder Ausdruck, der die Ungleichheit zwischen einem Wert <xref:System.Double.NaN?displayProperty=fullName> testet und `true`immer zurückgibt.

## <a name="how-to-fix-violations"></a>Behandeln von Verstößen
Um einen Verstoß gegen diese Regel zu beheben und genau zu bestimmen, ob <xref:System.Double.NaN?displayProperty=fullName>ein Wert <xref:System.Single.IsNaN%2A?displayProperty=fullName> darstellt <xref:System.Double.IsNaN%2A?displayProperty=fullName> , verwenden Sie oder, um den Wert zu testen.

## <a name="when-to-suppress-warnings"></a>Wann sollten Warnungen unterdrückt werden?
Unterdrücken Sie keine Warnung dieser Regel.

## <a name="example"></a>Beispiel
Das folgende Beispiel zeigt zwei Ausdrücke, die fälschlicherweise einen Wert gegen <xref:System.Double.NaN?displayProperty=fullName> testen, und einen Ausdruck, <xref:System.Double.IsNaN%2A?displayProperty=fullName> der zum Testen des Werts ordnungsgemäß verwendet.

[!code-vb[FxCop.Usage.TestForNaN#1](../code-quality/codesnippet/VisualBasic/ca2242-test-for-nan-correctly_1.vb)]
[!code-csharp[FxCop.Usage.TestForNaN#1](../code-quality/codesnippet/CSharp/ca2242-test-for-nan-correctly_1.cs)]