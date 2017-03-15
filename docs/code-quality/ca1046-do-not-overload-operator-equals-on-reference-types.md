---
title: "CA1046: Gleichheitsoperator f&#252;r Referenztypen nicht &#252;berladen | Microsoft Docs"
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
  - "DoNotOverloadOperatorEqualsOnReferenceTypes"
  - "CA1046"
helpviewer_keywords: 
  - "CA1046"
  - "DoNotOverrideOperatorEqualsOnReferenceTypes"
ms.assetid: c1dfbfe3-63f9-4005-a81a-890427b77e79
caps.latest.revision: 14
caps.handback.revision: 14
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# CA1046: Gleichheitsoperator f&#252;r Referenztypen nicht &#252;berladen
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|DoNotOverloadOperatorEqualsOnReferenceTypes|  
|CheckId|CA1046|  
|Kategorie \(Category\)|Microsoft.Design|  
|Unterbrechende Änderung|Breaking|  
  
## Ursache  
 Ein öffentlicher oder geschachtelter öffentlicher Verweistyp überlädt den Gleichheitsoperator.  
  
## Regelbeschreibung  
 Für Verweistypen ist die Standardimplementierung des Gleichheitsoperators fast immer zutreffend.  Standardmäßig sind zwei Verweise nur dann gleich, wenn sie auf dasselbe Objekt zeigen.  
  
## Behandeln von Verstößen  
 Um einen Verstoß gegen diese Regel zu beheben, entfernen Sie die Implementierung des Gleichheitsoperators.  
  
## Wann sollten Warnungen unterdrückt werden?  
 Eine Warnung dieser Regel kann gefahrlos unterdrückt werden, wenn sich der Verweistyp wie ein integrierter Werttyp verhält.  Wenn es sinnvoll ist, Additionen oder Subtraktionen mit Instanzen des Typs auszuführen, dann ist es wahrscheinlich richtig, den Gleichheitsoperator zu implementieren und den Regelverstoß zu unterdrücken.  
  
## Beispiel  
 Im folgenden Beispiel wird das Standardverhalten beim Vergleich zweier Verweise veranschaulicht.  
  
 [!code-cs[FxCop.Design.RefTypesNoEqualityOp#1](../code-quality/codesnippet/CSharp/ca1046-do-not-overload-operator-equals-on-reference-types_1.cs)]  
  
## Beispiel  
 Die folgende Anwendung vergleicht einige Verweise.  
  
 [!code-cs[FxCop.Design.TestRefTypesNoEqualityOp#1](../code-quality/codesnippet/CSharp/ca1046-do-not-overload-operator-equals-on-reference-types_2.cs)]  
  
 Folgende Ergebnisse werden zurückgegeben:  
  
  **a \= new \(2,2\) und b \= new \(2,2\) sind gleich?  nein**  
**c und a sind gleich?  ja**  
**b und a sind \=\= ?  nein**  
**c und a sind \=\= ?  ja**    
## Verwandte Regeln  
 [CA1013: Gleichheitsoperator beim Überladen von Addition und Subtraktion überladen](../code-quality/ca1013-overload-operator-equals-on-overloading-add-and-subtract.md)  
  
## Siehe auch  
 <xref:System.Object.Equals%2A?displayProperty=fullName>   
 [Gleichheitsoperatoren](../Topic/Equality%20Operators.md)