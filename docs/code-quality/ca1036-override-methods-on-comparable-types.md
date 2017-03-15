---
title: "CA1036: Methoden bei vergleichbaren Typen &#252;berschreiben | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CA1036"
  - "OverrideMethodsOnComparableTypes"
helpviewer_keywords: 
  - "OverrideMethodsOnComparableTypes"
  - "CA1036"
ms.assetid: 2329f844-4cb8-426d-bee2-cd065d1346d0
caps.latest.revision: 21
caps.handback.revision: 21
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# CA1036: Methoden bei vergleichbaren Typen &#252;berschreiben
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|OverrideMethodsOnComparableTypes|  
|CheckId|CA1036|  
|Kategorie \(Category\)|Microsoft.Design|  
|Unterbrechende Änderung|Nicht unterbrechend|  
  
## Ursache  
 Von einem öffentlichen oder geschützten Typ wird die <xref:System.IComparable?displayProperty=fullName>\-Schnittstelle implementiert. <xref:System.Object.Equals%2A?displayProperty=fullName> wird jedoch nicht überschrieben, bzw. die sprachspezifischen Operatoren für Gleichheit, Ungleichheit, Kleiner als oder Größer als werden nicht überladen.  Die Regel meldet keinen Verstoß, wenn der Typ nur eine Implementierung der Schnittstelle erbt.  
  
## Regelbeschreibung  
 Typen, die eine benutzerdefinierte Sortierreihenfolge definieren, implementieren die <xref:System.IComparable>\-Schnittstelle.  Die <xref:System.IComparable.CompareTo%2A>\-Methode gibt einen Ganzzahlwert zurück, der die richtige Sortierreihenfolge für zwei Instanzen des Typs angibt.  Diese Regel identifiziert Typen, die eine Sortierreihenfolge festlegen. Dies impliziert, dass die gewöhnliche Bedeutung von Gleichheit, Ungleichheit, kleiner als und größer als nicht gilt.  Wenn Sie eine Implementierung von <xref:System.IComparable> angeben, muss in der Regel auch <xref:System.Object.Equals%2A> überschrieben werden, damit Werte zurückgegeben werden, die mit <xref:System.IComparable.CompareTo%2A> konsistent sind.  Wenn Sie <xref:System.Object.Equals%2A> überschreiben und den Programmcode in einer Sprache schreiben, die Operatorüberladungen unterstützt, müssen Sie auch Operatoren angeben, die mit <xref:System.Object.Equals%2A> konsistent sind.  
  
## Behandeln von Verstößen  
 Um einen Verstoß gegen diese Regel zu korrigieren, überschreiben Sie <xref:System.Object.Equals%2A>.  Wenn die Programmiersprache das Überladen von Operatoren unterstützt, geben Sie die folgenden Operatoren an:  
  
-   op\_Equality  
  
-   op\_Inequality  
  
-   op\_LessThan  
  
-   op\_GreaterThan  
  
 In C\# sind die Token, die verwendet werden, um anzuzeigen, diese Operatoren, wie folgt: \=\=\! \=, \<und \>.  
  
## Wann sollten Warnungen unterdrückt werden?  
 Eine Warnung dieser Regel kann gefahrlos unterdrückt werden, wenn der Verstoß durch fehlende Operatoren verursacht wird und die Programmiersprache das Überladen von Operatoren nicht unterstützt, wie dies bei Visual Basic .NET der Fall ist.  Es ist auch sicher, eine Warnung für diese Regel zu unterdrücken, wenn sie bei anderen Gleichheitsoperatoren als op\_Equality ausgelöst wird, falls Sie entscheiden, dass eine Implementierung der Operatoren im Anwendungskontext keinen Sinn ergibt.  Sie sollten jedoch immer op\_Equality und den \=\=\-Operator überschreiben, wenn Sie Object.Equals überschreiben.  
  
## Beispiel  
 Das folgende Beispiel enthält einen Typ, von dem <xref:System.IComparable> ordnungsgemäß implementiert wird.  Codekommentare identifizieren die Methoden, die verschiedenen Regeln entsprechen, die sich auf <xref:System.Object.Equals%2A> und auf die <xref:System.IComparable>\-Schnittstelle beziehen.  
  
 [!code-cs[FxCop.Design.IComparable#1](../code-quality/codesnippet/CSharp/ca1036-override-methods-on-comparable-types_1.cs)]  
  
## Beispiel  
 Die folgende Anwendung testet das Verhalten der weiter oben dargestellten <xref:System.IComparable>\-Implementierung.  
  
 [!code-cs[FxCop.Design.TestIComparable#1](../code-quality/codesnippet/CSharp/ca1036-override-methods-on-comparable-types_2.cs)]  
  
## Siehe auch  
 <xref:System.IComparable?displayProperty=fullName>   
 <xref:System.Object.Equals%2A?displayProperty=fullName>   
 [Gleichheitsoperatoren](../Topic/Equality%20Operators.md)