---
title: "CA2242: Ordnungsgem&#228;&#223; auf NaN testen | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "TestForNaNCorrectly"
  - "CA2242"
helpviewer_keywords: 
  - "CA2242"
ms.assetid: e12dcffc-e255-4e1e-8fdf-3c6054d44abe
caps.latest.revision: 11
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
caps.handback.revision: 11
---
# CA2242: Ordnungsgem&#228;&#223; auf NaN testen
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|TestForNaNCorrectly|  
|CheckId|CA2242|  
|Kategorie \(Category\)|Microsoft.Usage|  
|Unterbrechende Änderung|Nicht unterbrechend|  
  
## Ursache  
 Ein Ausdruck testet einen Wert anhand von <xref:System.Single.Nan?displayProperty=fullName> oder <xref:System.Double.Nan?displayProperty=fullName>.  
  
## Regelbeschreibung  
 <xref:System.Double.NaN?displayProperty=fullName> steht für keine Zahl \(Not a Number, NaN\) und wird ausgegeben, wenn eine arithmetische Operation nicht definiert ist.  Jeder Ausdruck, durch den die Gleichheit zwischen einem Wert und <xref:System.Double.NaN?displayProperty=fullName> getestet wird, gibt immer `false` zurück.  Jeder Ausdruck, durch den die Ungleichheit zwischen einem Wert und <xref:System.Double.NaN?displayProperty=fullName> getestet wird, gibt immer `true` zurück.  
  
## Behandeln von Verstößen  
 Um einen Verstoß gegen diese Regel zu beheben und genau zu bestimmen, ob ein Wert <xref:System.Double.NaN?displayProperty=fullName> darstellt, verwenden Sie <xref:System.Single.IsNan%2A?displayProperty=fullName> oder <xref:System.Double.IsNan%2A?displayProperty=fullName>, um den Wert zu testen.  
  
## Wann sollten Warnungen unterdrückt werden?  
 Unterdrücken Sie keine Warnung dieser Regel.  
  
## Beispiel  
 Das folgende Beispiel enthält zwei Ausdrücke, durch die ein Wert falsch anhand von <xref:System.Double.NaN?displayProperty=fullName> getestet wird, sowie einen Ausdruck, der <xref:System.Double.IsNaN%2A?displayProperty=fullName> auf richtige Weise zum Testen des Werts verwendet.  
  
 [!code-vb[FxCop.Usage.TestForNaN#1](../code-quality/codesnippet/VisualBasic/ca2242-test-for-nan-correctly_1.vb)]
 [!code-cs[FxCop.Usage.TestForNaN#1](../code-quality/codesnippet/CSharp/ca2242-test-for-nan-correctly_1.cs)]