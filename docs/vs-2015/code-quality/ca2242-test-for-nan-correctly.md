---
title: 'CA2242: für Nan ordnungsgemäß testen | Microsoft-Dokumentation'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- TestForNaNCorrectly
- CA2242
helpviewer_keywords:
- CA2242
ms.assetid: e12dcffc-e255-4e1e-8fdf-3c6054d44abe
caps.latest.revision: 13
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 8433ac081a45e3dbab80ffcd6f96e6d1db914337
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/19/2019
ms.locfileid: "72672009"
---
# <a name="ca2242-test-for-nan-correctly"></a>CA2242: Ordnungsgemäß auf NaN testen
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|Testfornanrichtig|
|CheckId|CA2242|
|Kategorie|Microsoft. Usage|
|Unterbrechende Änderung|Nicht unterbrechende Änderung|

## <a name="cause"></a>Ursache
 Ein Ausdruck testet einen Wert mit <xref:System.Single.NaN?displayProperty=fullName> oder <xref:System.Double.NaN?displayProperty=fullName>.

## <a name="rule-description"></a>Regelbeschreibung
 <xref:System.Double.NaN?displayProperty=fullName>, das not-a-Number darstellt, ergibt sich, wenn eine arithmetische Operation nicht definiert ist. Jeder Ausdruck, der die Gleichheit zwischen einem Wert und <xref:System.Double.NaN?displayProperty=fullName> testet, gibt immer `false` zurück. Jeder Ausdruck, der die Ungleichheit zwischen einem Wert und <xref:System.Double.NaN?displayProperty=fullName> testet, gibt immer `true` zurück.

## <a name="how-to-fix-violations"></a>Behandeln von Verstößen
 Um einen Verstoß gegen diese Regel zu beheben und genau zu bestimmen, ob ein Wert <xref:System.Double.NaN?displayProperty=fullName> darstellt, verwenden Sie <xref:System.Single.IsNaN%2A?displayProperty=fullName> oder <xref:System.Double.IsNaN%2A?displayProperty=fullName>, um den Wert zu testen.

## <a name="when-to-suppress-warnings"></a>Wann sollten Warnungen unterdrückt werden?
 Unterdrücken Sie keine Warnung dieser Regel.

## <a name="example"></a>Beispiel
 Das folgende Beispiel zeigt zwei Ausdrücke, die einen Wert fälschlicherweise mit <xref:System.Double.NaN?displayProperty=fullName> testen, und einen Ausdruck, der <xref:System.Double.IsNaN%2A?displayProperty=fullName> zum Testen des Werts ordnungsgemäß verwendet.

 [!code-csharp[FxCop.Usage.TestForNaN#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Usage.TestForNaN/cs/FxCop.Usage.TestForNaN.cs#1)]
 [!code-vb[FxCop.Usage.TestForNaN#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Usage.TestForNaN/vb/FxCop.Usage.TestForNaN.vb#1)]
