---
title: "CA2224: Equals beim &#220;berladen von Gleichheitsoperatoren &#252;berschreiben | Microsoft Docs"
ms.custom: ""
ms.date: "12/02/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CA2224"
  - "OverrideEqualsOnOverloadingOperatorEquals"
  - "OverrideEqualsOnOverridingOperatorEquals"
helpviewer_keywords: 
  - "CA2224"
  - "OverrideEqualsOnOverloadingOperatorEquals"
ms.assetid: 7312afd9-84ba-417f-923e-7a159b53bf70
caps.latest.revision: 15
caps.handback.revision: 15
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# CA2224: Equals beim &#220;berladen von Gleichheitsoperatoren &#252;berschreiben
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|OverrideEqualsOnOverloadingOperatorEquals|  
|CheckId|CA2224|  
|Kategorie \(Category\)|Microsoft.Usage|  
|Unterbrechende Änderung|Nicht unterbrechend|  
  
## Ursache  
 Ein öffentlicher Typ implementiert den Gleichheitsoperator, überschreibt jedoch <xref:System.Object.Equals%2A?displayProperty=fullName> nicht.  
  
## Regelbeschreibung  
 Der Gleichheitsoperator soll die Syntax für den Zugriff auf die Funktionalität der <xref:System.Object.Equals%2A>\-Methode vereinfachen.  Wenn Sie den Gleichheitsoperator implementieren, muss seine Logik mit der Logik von <xref:System.Object.Equals%2A> übereinstimmen.  
  
 Der C\#\-Compiler gibt eine Warnung aus, wenn der Code gegen diese Regel verstößt.  
  
## Behandeln von Verstößen  
 Um einen Verstoß gegen diese Regel zu beheben, sollten Sie die Implementierung des Gleichheitsoperators entweder entfernen oder <xref:System.Object.Equals%2A> überschreiben und von den beiden Methoden die gleichen Werte zurückgeben lassen.  Wenn der Gleichheitsoperator kein inkonsistentes Verhalten einleitet, können Sie den Verstoß beheben, indem Sie eine Implementierung von <xref:System.Object.Equals%2A> angeben, mit der die <xref:System.Object.Equals%2A>\-Methode in der Basisklasse aufgerufen wird.  
  
## Wann sollten Warnungen unterdrückt werden?  
 Eine Warnung dieser Regel kann gefahrlos unterdrückt werden, wenn der Gleichheitsoperator den gleichen Wert wie die geerbte Implementierung von <xref:System.Object.Equals%2A> zurückgibt.  Der Beispielabschnitt enthält einen Typ, der das Unterdrücken einer Warnung dieser Regel gefahrlos ermöglicht.  
  
## Beispiele für inkonsistente Gleichheitsdefinitionen  
  
### **Beschreibung**  
 Im folgenden Beispiel wird ein Typ mit inkonsistenten Definitionen von Gleichheit veranschaulicht.  `BadPoint` ändert die Bedeutung der Gleichheit, indem eine benutzerdefinierte Implementierung des Gleichheitsoperators angegeben wird, überschreibt <xref:System.Object.Equals%2A> jedoch nicht, sodass es sich identisch verhält.  
  
### Code  
 [!code-cs[FxCop.Usage.OperatorEqualsRequiresEquals#1](../code-quality/codesnippet/CSharp/ca2224-override-equals-on-overloading-operator-equals_1.cs)]  
  
## Beispiel  
 Im folgenden Code wird das Verhalten von `BadPoint` getestet.  
  
 [!code-cs[FxCop.Usage.TestOperatorEqualsRequiresEquals#1](../code-quality/codesnippet/CSharp/ca2224-override-equals-on-overloading-operator-equals_2.cs)]  
  
 Folgende Ergebnisse werden zurückgegeben:  
  
  **a \= \(\[0\] 1,1\) und b \= \(\[1\] 2,2\) sind gleich?  nein**  
**a \=\= b ?  nein**  
**a1 und a sind gleich?  ja**  
**a1 \=\= a ?  ja**  
**b und bcopy sind gleich ?  nein**  
**b \=\= bcopy ?  ja**    
## Beispiel  
 Das folgende Beispiel zeigt einen Typ, der zwar technisch gegen diese Regel verstößt, sich jedoch nicht inkonsistent verhält.  
  
 [!code-cs[FxCop.Usage.ValueTypeEquals#1](../code-quality/codesnippet/CSharp/ca2224-override-equals-on-overloading-operator-equals_3.cs)]  
  
## Beispiel  
 Im folgenden Code wird das Verhalten von `GoodPoint` getestet.  
  
 [!code-cs[FxCop.Usage.TestValueTypeEquals#1](../code-quality/codesnippet/CSharp/ca2224-override-equals-on-overloading-operator-equals_4.cs)]  
  
 Folgende Ergebnisse werden zurückgegeben:  
  
  **a \= \(1,1\) und b \= \(2,2\) sind gleich?  nein**  
**a \=\= b ?  nein**  
**a1 und a sind gleich?  ja**  
**a1 \=\= a ?  ja**  
**b und bcopy sind gleich ?  ja**  
**b \=\= bcopy ?  ja**    
## Klassenbeispiel  
  
### **Beschreibung**  
 Im folgenden Beispiel wird eine Klasse \(Referenztyp\) veranschaulicht, die gegen diese Regel verstößt.  
  
### Code  
 [!code-cs[FxCop.Usage.OverrideEqualsClassViolation#1](../code-quality/codesnippet/CSharp/ca2224-override-equals-on-overloading-operator-equals_5.cs)]  
  
## Beispiel  
 Im folgenden Beispiel wird der Verstoß korrigiert, indem <xref:System.Object.Equals%2A?displayProperty=fullName> überschrieben wird.  
  
 [!code-cs[FxCop.Usage.OverrideEqualsClassFixed#1](../code-quality/codesnippet/CSharp/ca2224-override-equals-on-overloading-operator-equals_6.cs)]  
  
## Strukturbeispiel  
  
### **Beschreibung**  
 Im folgenden Beispiel wird eine Struktur \(Werttyp\) veranschaulicht, die gegen diese Regel verstößt.  
  
### Code  
 [!code-cs[FxCop.Usage.OverrideEqualsStructViolation#1](../code-quality/codesnippet/CSharp/ca2224-override-equals-on-overloading-operator-equals_7.cs)]  
  
## Beispiel  
 Im folgenden Beispiel wird der Verstoß korrigiert, indem <xref:System.ValueType.Equals%2A?displayProperty=fullName> überschrieben wird.  
  
 [!code-cs[FxCop.Usage.OverrideEqualsStructFixed#1](../code-quality/codesnippet/CSharp/ca2224-override-equals-on-overloading-operator-equals_8.cs)]  
  
## Verwandte Regeln  
 [CA1046: Gleichheitsoperator für Referenztypen nicht überladen](../code-quality/ca1046-do-not-overload-operator-equals-on-reference-types.md)  
  
 [CA2225: Operatorüberladungen weisen benannte Alternativen auf](../code-quality/ca2225-operator-overloads-have-named-alternates.md)  
  
 [CA2226: Operatoren sollten symmetrische Überladungen aufweisen](../code-quality/ca2226-operators-should-have-symmetrical-overloads.md)  
  
 [CA2218: GetHashCode beim Überschreiben von Equals überschreiben](../code-quality/ca2218-override-gethashcode-on-overriding-equals.md)  
  
 [CA2231: Überladen Sie den Gleichheitsoperator beim Überschreiben von ValueType.Equals](../code-quality/ca2231-overload-operator-equals-on-overriding-valuetype-equals.md)