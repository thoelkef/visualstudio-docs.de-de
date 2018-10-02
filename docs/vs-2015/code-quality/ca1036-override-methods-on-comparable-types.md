---
title: 'CA1036: Methoden bei vergleichbaren Typen überschreiben | Microsoft-Dokumentation'
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-devops-test
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- CA1036
- OverrideMethodsOnComparableTypes
helpviewer_keywords:
- OverrideMethodsOnComparableTypes
- CA1036
ms.assetid: 2329f844-4cb8-426d-bee2-cd065d1346d0
caps.latest.revision: 23
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 906ee4c3e5300f04b5627c7b3aa19ba7950f3239
ms.sourcegitcommit: 99d097d82ee4f9eff6f588e5ebb6b17d8f724b04
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/24/2018
ms.locfileid: "47589211"
---
# <a name="ca1036-override-methods-on-comparable-types"></a>CA1036: Methoden bei vergleichbaren Typen überschreiben
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Die neueste Version dieses Themas finden Sie unter [CA1036: Methoden bei vergleichbaren Typen überschreiben](https://docs.microsoft.com/visualstudio/code-quality/ca1036-override-methods-on-comparable-types).

|||
|-|-|
|TypeName|OverrideMethodsOnComparableTypes|
|CheckId|CA1036|
|Kategorie|Microsoft.Design|
|Unterbrechende Änderung|Nicht unterbrechend|

## <a name="cause"></a>Ursache
 Ein öffentlicher oder geschützter Typ implementiert die <xref:System.IComparable?displayProperty=fullName> -Schnittstelle und überschreibt nicht die <xref:System.Object.Equals%2A?displayProperty=fullName> oder nicht den sprachspezifischen Operator für gleich, ungleich, kleiner als oder größer als überladen. Die Regel meldet einen Verstoß gegen nicht, wenn der Typ nur eine Implementierung der Schnittstelle erbt.

## <a name="rule-description"></a>Regelbeschreibung
 Implementieren von Typen, die eine benutzerdefinierte Sortierreihenfolge definieren die <xref:System.IComparable> Schnittstelle. Die <xref:System.IComparable.CompareTo%2A> Methode gibt einen ganzzahligen-Wert, der die richtigen Sortierreihenfolge für zwei Instanzen des Typs angibt. Mit dieser Regel identifiziert die Typen, die eine Sortierreihenfolge festgelegt. Dies bedeutet, dass die gewöhnliche Bedeutung von gleich, ungleich, kleiner als und größer als nicht gelten. Wenn Sie eine Implementierung bereitstellen <xref:System.IComparable>, müssen Sie in der Regel außer Kraft setzen <xref:System.Object.Equals%2A> , damit sie Werte zurückgibt, die konsistent mit sind <xref:System.IComparable.CompareTo%2A>. Wenn Sie außer Kraft setzen <xref:System.Object.Equals%2A> und Codierung werden in einer Sprache, die von überladenen Operatoren unterstützt, sollten Sie auch Operatoren, die konsistent mit sind bereitstellen <xref:System.Object.Equals%2A>.

## <a name="how-to-fix-violations"></a>Behandeln von Verstößen
 Um einen Verstoß gegen diese Regel zu beheben, außer Kraft setzen <xref:System.Object.Equals%2A>. Wenn Ihre Programmiersprache operatorüberladung unterstützt, geben Sie die folgenden Operatoren:

-   op_Equality

-   op_Inequality

-   op_LessThan

-   op_GreaterThan

 In c# werden die Token, die zur Darstellung dieser Operatoren verwendet werden wie folgt: ==,! =, \<, und >.

## <a name="when-to-suppress-warnings"></a>Wann sollten Warnungen unterdrückt werden?
 Es ist sicher, um eine Warnung dieser Regel zu unterdrücken, wenn es sich bei den Verstoß verursacht wird, durch fehlende Operatoren und Ihre bevorzugte Programmiersprache unterstützt keine operatorüberladung, wie mit Visual Basic .NET. Es ist auch sicher, um eine Warnung für diese Regel zu unterdrücken, wenn es auf Gleichheitsoperatoren ausgelöst wird, anders als Op_Equality, wenn Sie feststellen, dass die Implementierung der Operatoren nicht im Kontext Ihrer Anwendung sinnvoll ist. Sie sollten jedoch immer op_Equality und dem == Operator, wenn Sie Object.Equals überschreiben.

## <a name="example"></a>Beispiel
 Das folgende Beispiel enthält einen Typ, der korrekt implementiert <xref:System.IComparable>. Codekommentare zu identifizieren, die Methoden, die verschiedene Regeln, die im Zusammenhang erfüllen mit <xref:System.Object.Equals%2A> und <xref:System.IComparable> Schnittstelle.

 [!code-csharp[FxCop.Design.IComparable#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.IComparable/cs/FxCop.Design.IComparable.cs#1)]

## <a name="example"></a>Beispiel
 Die folgende Anwendung testet das Verhalten der <xref:System.IComparable> -Implementierung, die zuvor gezeigt wurde.

 [!code-csharp[FxCop.Design.TestIComparable#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.TestIComparable/cs/FxCop.Design.TestIComparable.cs#1)]

## <a name="see-also"></a>Siehe auch
 <xref:System.IComparable?displayProperty=fullName> <xref:System.Object.Equals%2A?displayProperty=fullName>
 [Gleichheitsoperatoren](http://msdn.microsoft.com/library/bc496a91-fefb-4ce0-ab4c-61f09964119a)



