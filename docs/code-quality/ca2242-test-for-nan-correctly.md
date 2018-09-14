---
title: 'CA2242: Ordnungsgemäß auf NaN testen'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- TestForNaNCorrectly
- CA2242
helpviewer_keywords:
- CA2242
ms.assetid: e12dcffc-e255-4e1e-8fdf-3c6054d44abe
author: gewarren
ms.author: gewarren
manager: douge
dev_langs:
- CSharp
- VB
ms.workload:
- multiple
ms.openlocfilehash: c742c73d73802a21ea7a21a426cf815ee4e34e2d
ms.sourcegitcommit: 568bb0b944d16cfe1af624879fa3d3594d020187
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/13/2018
ms.locfileid: "45545618"
---
# <a name="ca2242-test-for-nan-correctly"></a>CA2242: Ordnungsgemäß auf NaN testen

|||
|-|-|
|TypeName|TestForNaNCorrectly|
|CheckId|CA2242|
|Kategorie|Microsoft.Usage|
|Unterbrechende Änderung|Nicht unterbrechende Änderung|

## <a name="cause"></a>Ursache
 Ein Ausdruck testen Sie einen Wert für <xref:System.Single.NaN?displayProperty=fullName> oder <xref:System.Double.NaN?displayProperty=fullName>.

## <a name="rule-description"></a>Regelbeschreibung
 <xref:System.Double.NaN?displayProperty=fullName>, die Not-a-Number darstellt, die entsteht, wenn eine arithmetische Operation nicht definiert ist. Ein Ausdruck, der auf Gleichheit zwischen einem Wert testet und <xref:System.Double.NaN?displayProperty=fullName> gibt immer `false`. Ein Ausdruck, der Ungleichheit zwischen einem Wert getestet und <xref:System.Double.NaN?displayProperty=fullName> gibt immer `true`.

## <a name="how-to-fix-violations"></a>Behandeln von Verstößen
 Um einen Verstoß gegen diese Regel zu beheben, und genau zu bestimmen, ob ein Wert darstellt <xref:System.Double.NaN?displayProperty=fullName>, verwenden Sie <xref:System.Single.IsNaN%2A?displayProperty=fullName> oder <xref:System.Double.IsNaN%2A?displayProperty=fullName> zum Testen des Werts.

## <a name="when-to-suppress-warnings"></a>Wenn Sie Warnungen unterdrücken
 Unterdrücken Sie keine Warnung dieser Regel.

## <a name="example"></a>Beispiel
 Das folgende Beispiel zeigt zwei Ausdrücke, falsch einen Wert für <xref:System.Double.NaN?displayProperty=fullName> und ein Ausdruck, der verwendet <xref:System.Double.IsNaN%2A?displayProperty=fullName> zum Testen des Werts.

 [!code-vb[FxCop.Usage.TestForNaN#1](../code-quality/codesnippet/VisualBasic/ca2242-test-for-nan-correctly_1.vb)]
 [!code-csharp[FxCop.Usage.TestForNaN#1](../code-quality/codesnippet/CSharp/ca2242-test-for-nan-correctly_1.cs)]