---
title: "CA1036: Methoden bei vergleichbaren Typen überschreiben | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- CA1036
- OverrideMethodsOnComparableTypes
helpviewer_keywords:
- OverrideMethodsOnComparableTypes
- CA1036
ms.assetid: 2329f844-4cb8-426d-bee2-cd065d1346d0
caps.latest.revision: "21"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 9c8eedd58df2665b9e00051e40a07a0ac226ec6c
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/22/2017
---
# <a name="ca1036-override-methods-on-comparable-types"></a>CA1036: Methoden bei vergleichbaren Typen überschreiben
|||  
|-|-|  
|TypeName|OverrideMethodsOnComparableTypes|  
|CheckId|CA1036|  
|Kategorie|Microsoft.Design|  
|Unterbrechende Änderung|Nicht unterbrechend|  
  
## <a name="cause"></a>Ursache  
 Ein öffentlicher oder geschützter Typ implementiert den <xref:System.IComparable?displayProperty=fullName> -Schnittstelle und überschreibt nicht <xref:System.Object.Equals%2A?displayProperty=fullName> oder nicht den sprachspezifischen Operator für gleich, ungleich, kleiner als und größer als überladen. Diese Regel meldet keine Verletzung, wenn der Typ nur eine Implementierung der Schnittstelle erbt.  
  
## <a name="rule-description"></a>Regelbeschreibung  
 Implementieren von Typen, die eine benutzerdefinierte Sortierreihenfolge definieren die <xref:System.IComparable> Schnittstelle. Die <xref:System.IComparable.CompareTo%2A> Methode gibt einen ganzzahligen-Wert, der die richtigen Sortierreihenfolge für zwei Instanzen des Typs angibt. Diese Regel identifiziert Typen, die eine Sortierreihenfolge festgelegt; Dies bedeutet, dass die gewöhnliche Bedeutung gleich, ungleich, kleiner als und größer als nicht gültig sind. Wenn Sie eine Implementierung bereitstellen <xref:System.IComparable>, müssen Sie in der Regel auch überschreiben <xref:System.Object.Equals%2A> , sodass Werte zurückgegeben, die konsistent mit sind <xref:System.IComparable.CompareTo%2A>. Wenn Sie außer Kraft setzen <xref:System.Object.Equals%2A> und die sicherheitscodierung werden in einer anderen Sprache, die operatorüberladungen unterstützt, sollten Sie auch Operatoren mit konsistent sind, bereitstellen <xref:System.Object.Equals%2A>.  
  
## <a name="how-to-fix-violations"></a>Behandeln von Verstößen  
 Um einen Verstoß gegen diese Regel zu beheben, überschreiben <xref:System.Object.Equals%2A>. Wenn Ihre Programmiersprache Überladen von Operatoren unterstützt, geben Sie die folgenden Operatoren:  
  
-   op_Equality  
  
-   op_Inequality  
  
-   op_LessThan  
  
-   op_GreaterThan  
  
 In c#, die Token, die verwendet werden, um diese Operatoren darzustellen sind wie folgt: ==,! =, \<, und >.  
  
## <a name="when-to-suppress-warnings"></a>Wann sollten Warnungen unterdrückt werden?  
 Sie können ruhig auf eine Warnung dieser Regel zu unterdrücken, wenn der Verstoß durch fehlende Operatoren verursacht wird und Ihre Programmiersprache keine Operatoren überladen, unterstützt wie mit Visual Basic .NET. Es ist auch sicher, eine Warnung für diese Regel zu unterdrücken, wenn auf Gleichheitsoperatoren auslösende abgesehen Op_Equality, wenn Sie feststellen, dass die Implementierung der Operatoren in Ihrem Anwendungskontext keinen Sinn ergibt. Sie sollten jedoch immer op_Equality und den ==-Operator aus, wenn Sie Object.Equals überschreiben.  
  
## <a name="example"></a>Beispiel  
 Das folgende Beispiel enthält einen Typ, ordnungsgemäß implementiert <xref:System.IComparable>. Codekommentare identifizieren die Methoden, die verschiedenen Regeln erfüllen, die zusammengehören <xref:System.Object.Equals%2A> und <xref:System.IComparable> Schnittstelle.  
  
 [!code-csharp[FxCop.Design.IComparable#1](../code-quality/codesnippet/CSharp/ca1036-override-methods-on-comparable-types_1.cs)]  
  
## <a name="example"></a>Beispiel  
 Die folgende Anwendung testet das Verhalten der <xref:System.IComparable> Implementierung, die weiter oben gezeigt wurde.  
  
 [!code-csharp[FxCop.Design.TestIComparable#1](../code-quality/codesnippet/CSharp/ca1036-override-methods-on-comparable-types_2.cs)]  
  
## <a name="see-also"></a>Siehe auch  
 <xref:System.IComparable?displayProperty=fullName>   
 <xref:System.Object.Equals%2A?displayProperty=fullName>   
 [Gleichheitsoperatoren](/dotnet/standard/design-guidelines/equality-operators)