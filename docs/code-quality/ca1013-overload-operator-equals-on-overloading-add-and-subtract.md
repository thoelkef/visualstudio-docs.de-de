---
title: "CA1013: Gleichheitsoperator beim &#220;berladen von Addition und Subtraktion &#252;berladen | Microsoft Docs"
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
  - "OverrideOperatorEqualsOnOverridingAddAndSubtract"
  - "OverrideOperatorEqualsOnOverloadingAddAndSubtract"
  - "CA1013"
  - "OverloadOperatorEqualsOnOverloadingAddAndSubtract"
helpviewer_keywords: 
  - "OverrideOperatorEqualsOnOverloadingAddAndSubtract"
  - "OverrideOperatorEqualsOnOverridingAddAndSubtract"
  - "CA1013"
  - "OverloadOperatorEqualsOnOverloadingAddAndSubtract"
ms.assetid: 5bd28d68-c179-49ff-af47-5250b8b18a10
caps.latest.revision: 22
caps.handback.revision: 22
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# CA1013: Gleichheitsoperator beim &#220;berladen von Addition und Subtraktion &#252;berladen
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|OverloadOperatorEqualsOnOverloadingAddAndSubtract|  
|CheckId|CA1013|  
|Kategorie \(Category\)|Microsoft.Design|  
|Unterbrechende Änderung|Nicht unterbrechend|  
  
## Ursache  
 Ein öffentlicher oder geschützter Typ implementiert den Additions\- oder Subtraktionsoperator, ohne den Gleichheitsoperator zu implementieren.  
  
## Regelbeschreibung  
 Wenn Instanzen eines Typs mithilfe von Rechenoperationen wie Addition und Subtraktion kombiniert werden können, sollten Sie die Gleichheit fast immer so definieren, dass `true` zurückgegeben wird, wenn zwei Instanzen die gleichen konstituierenden Werte aufweisen.  
  
 Sie können den Standardgleichheitsoperator nicht in einer überladenen Implementierung des Gleichheitsoperators verwenden.  Eine solche Vorgehensweise führt zu einem Stapelüberlauf.  Verwenden Sie zur Implementierung des Gleichheitsoperators die Object.Equals\-Methode.  \(Siehe nachstehendes Beispiel.\)  
  
```vb  
If (Object.ReferenceEquals(left, Nothing)) Then  
    Return Object.ReferenceEquals(right, Nothing)  
Else  
    Return left.Equals(right)  
End If  
```  
  
```c#  
if (Object.ReferenceEquals(left, null))   
    return Object.ReferenceEquals(right, null);  
return left.Equals(right);  
```  
  
## Behandeln von Verstößen  
 Um einen Verstoß gegen diese Regel zu beheben, implementieren Sie den Gleichheitsoperator so, dass er mathematisch konsistent ist mit dem Additions\- und dem Subtraktionsoperator.  
  
## Wann sollten Warnungen unterdrückt werden?  
 Eine Warnung dieser Regel kann gefahrlos unterdrückt werden, wenn die Standardimplementierung des Gleichheitsoperators das richtige Verhalten für den Typ angibt.  
  
## Beispiel  
 Im folgenden Beispiel wird ein Typ \(`BadAddableType`\) definiert, der gegen diese Regel verstößt.  Dieser Typ sollte den Gleichheitsoperator implementieren, damit zwei Instanzen mit den gleichen Feldwerten bei Gleichheit mit `true` bewertet werden.  Der `GoodAddableType`\-Typ zeigt die korrigierte Implementierung.  Sie sehen, dass dieser Typ auch den Ungleichheitsoperator implementiert und <xref:System.Object.Equals%2A> überschreibt, damit andere Regeln eingehalten werden.  Bei einer vollständigen Implementierung würde auch <xref:System.Object.GetHashCode%2A> implementiert werden.  
  
 [!code-cs[FxCop.Design.AddAndSubtract#1](../code-quality/codesnippet/CSharp/ca1013-overload-operator-equals-on-overloading-add-and-subtract_1.cs)]  
  
## Beispiel  
 Im folgenden Beispiel wird mithilfe der Instanzen der zuvor in diesem Thema definierten Typen ein Test auf Gleichheit durchgeführt, um das Standardverhalten und die richtigen Verhalten des Gleichheitsoperators zu veranschaulichen.  
  
 [!code-cs[FxCop.Design.TestAddAndSubtract#1](../code-quality/codesnippet/CSharp/ca1013-overload-operator-equals-on-overloading-add-and-subtract_2.cs)]  
  
 Folgende Ergebnisse werden zurückgegeben:  
  
  **Ungültiger Typ: {2,2} {2,2} sind gleich?  nein**  
**Gültiger Typ: {3,3} {3,3} sind gleich?  ja**  
**Gültiger Typ: {3,3} {3,3} sind \=\= ?   ja**  
**Ungültiger Typ: {2,2} {9,9} sind gleich?  nein**  
**Gültiger Typ: {3,3} {9,9} sind \=\= ?   nein**    
## Siehe auch  
 [Gleichheitsoperatoren](../Topic/Equality%20Operators.md)