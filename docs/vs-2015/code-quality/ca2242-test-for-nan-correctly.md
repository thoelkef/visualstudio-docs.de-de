---
title: 'CA2242: Ordnungsgemäß auf NaN testen | Microsoft-Dokumentation'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-devops-test
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- TestForNaNCorrectly
- CA2242
helpviewer_keywords:
- CA2242
ms.assetid: e12dcffc-e255-4e1e-8fdf-3c6054d44abe
caps.latest.revision: 13
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: d7cd2d6d823dfb13c86ad3f2cc4ef001e854955c
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/23/2018
ms.locfileid: "49842481"
---
# <a name="ca2242-test-for-nan-correctly"></a>CA2242: Ordnungsgemäß auf NaN testen
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

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

## <a name="when-to-suppress-warnings"></a>Wann sollten Warnungen unterdrückt werden?
 Unterdrücken Sie keine Warnung dieser Regel.

## <a name="example"></a>Beispiel
 Das folgende Beispiel zeigt zwei Ausdrücke, falsch einen Wert für <xref:System.Double.NaN?displayProperty=fullName> und ein Ausdruck, der verwendet <xref:System.Double.IsNaN%2A?displayProperty=fullName> zum Testen des Werts.

 [!code-csharp[FxCop.Usage.TestForNaN#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Usage.TestForNaN/cs/FxCop.Usage.TestForNaN.cs#1)]
 [!code-vb[FxCop.Usage.TestForNaN#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Usage.TestForNaN/vb/FxCop.Usage.TestForNaN.vb#1)]



