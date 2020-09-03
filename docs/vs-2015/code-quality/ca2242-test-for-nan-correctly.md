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
ms.openlocfilehash: a0c832b7eb4a94506c5e15dfa5858bb9f6753912
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "85546262"
---
# <a name="ca2242-test-for-nan-correctly"></a>CA2242: Ordnungsgemäß auf NaN testen.
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|Element|value|
|-|-|
|TypName|Testfornanrichtig|
|CheckId|CA2242|
|Category|Microsoft. Usage|
|Unterbrechende Änderung|Nicht unterbrechende Änderung|

## <a name="cause"></a>Ursache
 Ein Ausdruck testet einen Wert mit <xref:System.Single.NaN?displayProperty=fullName> oder <xref:System.Double.NaN?displayProperty=fullName> .

## <a name="rule-description"></a>Beschreibung der Regel
 <xref:System.Double.NaN?displayProperty=fullName>, das not-a-Number-Ergebnisse darstellt, wenn eine arithmetische Operation nicht definiert ist. Jeder Ausdruck, der die Gleichheit zwischen einem Wert testet und <xref:System.Double.NaN?displayProperty=fullName> immer zurückgibt `false` . Jeder Ausdruck, der die Ungleichheit zwischen einem Wert testet und <xref:System.Double.NaN?displayProperty=fullName> immer zurückgibt `true` .

## <a name="how-to-fix-violations"></a>Behandeln von Verstößen
 Um einen Verstoß gegen diese Regel zu beheben und genau zu bestimmen, ob ein Wert darstellt <xref:System.Double.NaN?displayProperty=fullName> , verwenden <xref:System.Single.IsNaN%2A?displayProperty=fullName> Sie oder, <xref:System.Double.IsNaN%2A?displayProperty=fullName> um den Wert zu testen.

## <a name="when-to-suppress-warnings"></a>Wann sollten Warnungen unterdrückt werden?
 Unterdrücken Sie keine Warnung dieser Regel.

## <a name="example"></a>Beispiel
 Das folgende Beispiel zeigt zwei Ausdrücke, die fälschlicherweise einen Wert gegen testen, <xref:System.Double.NaN?displayProperty=fullName> und einen Ausdruck, <xref:System.Double.IsNaN%2A?displayProperty=fullName> der zum Testen des Werts ordnungsgemäß verwendet.

 [!code-csharp[FxCop.Usage.TestForNaN#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Usage.TestForNaN/cs/FxCop.Usage.TestForNaN.cs#1)]
 [!code-vb[FxCop.Usage.TestForNaN#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Usage.TestForNaN/vb/FxCop.Usage.TestForNaN.vb#1)]
