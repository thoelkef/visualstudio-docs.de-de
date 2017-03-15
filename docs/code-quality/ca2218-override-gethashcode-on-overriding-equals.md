---
title: "CA2218: GetHashCode beim &#220;berschreiben von Equals &#252;berschreiben | Microsoft Docs"
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
  - "CA2218"
  - "OverrideGetHashCodeOnOverridingEquals"
helpviewer_keywords: 
  - "CA2218"
  - "OverrideGetHashCodeOnOverridingEquals"
ms.assetid: 69b020cd-29e8-45a6-952e-32cf3ce2e21d
caps.latest.revision: 20
caps.handback.revision: 20
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# CA2218: GetHashCode beim &#220;berschreiben von Equals &#252;berschreiben
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|OverrideGetHashCodeOnOverridingEquals|  
|CheckId|CA2218|  
|Kategorie \(Category\)|Microsoft.Usage|  
|Unterbrechende Änderung|Nicht unterbrechend|  
  
## Ursache  
 Ein öffentlicher Typ überschreibt <xref:System.Object.Equals%2A?displayProperty=fullName>, nicht jedoch <xref:System.Object.GetHashCode%2A?displayProperty=fullName>.  
  
## Regelbeschreibung  
 <xref:System.Object.GetHashCode%2A> gibt einen Wert auf der Grundlage der aktuellen Instanz zurück, die sich für Hashalgorithmen und Datenstrukturen eignet, z. B. für eine Hashtabelle.  Zwei Objekte, die den gleichen Typ aufweisen und gleich sind, müssen den gleichen Hashcode zurückgeben, damit sichergestellt ist, dass Instanzen der folgenden Typen einwandfrei arbeiten:  
  
-   <xref:System.Collections.HashTable?displayProperty=fullName>  
  
-   <xref:System.Collections.SortedList?displayProperty=fullName>  
  
-   <xref:System.Collections.Generic.Dictionary?displayProperty=fullName>  
  
-   <xref:System.Collections.Generic.SortDictionary?displayProperty=fullName>  
  
-   <xref:System.Collections.Generic.SortList?displayProperty=fullName>  
  
-   <xref:System.Collections.Specialized.HybredDictionary?displayProperty=fullName>  
  
-   <xref:System.Collections.Specialized.ListDictionary?displayProperty=fullName>  
  
-   <xref:System.Collections.Specialized.OrderedDictionary?displayProperty=fullName>  
  
-   Typen, die <xref:System.Collections.Generic.IEqualityComparer?displayProperty=fullName> implementieren  
  
## Behandeln von Verstößen  
 Um einen Verstoß gegen diese Regel zu beheben, stellen Sie eine Implementierung von <xref:System.Object.GetHashCode%2A> bereit.  Bei einem Paar von Objekten des gleichen Typs müssen Sie sicherstellen, dass die Implementierung den gleichen Wert zurückgibt, wenn die Implementierung von <xref:System.Object.Equals%2A> für das Paar `true` zurückgibt.  
  
## Wann sollten Warnungen unterdrückt werden?  
 Unterdrücken Sie keine Warnung dieser Regel.  
  
## Klassenbeispiel  
  
### **Beschreibung**  
 Im folgenden Beispiel wird eine Klasse \(Referenztyp\) veranschaulicht, die gegen diese Regel verstößt.  
  
### Code  
 [!code-cs[FxCop.Usage.GetHashCodeErrorClass#1](../code-quality/codesnippet/CSharp/ca2218-override-gethashcode-on-overriding-equals_1.cs)]  
  
### Kommentare  
 Im folgenden Beispiel wird der Verstoß korrigiert, indem <xref:System.Object.GetHashCode> überschrieben wird.  
  
### Code  
 [!code-cs[FxCop.Usage.GetHashCodeFixedClass#1](../code-quality/codesnippet/CSharp/ca2218-override-gethashcode-on-overriding-equals_2.cs)]  
  
## Strukturbeispiel  
  
### **Beschreibung**  
 Im folgenden Beispiel wird eine Struktur \(Werttyp\) veranschaulicht, die gegen diese Regel verstößt.  
  
### Code  
 [!code-cs[FxCop.Usage.GetHashCodeErrorStruct#1](../code-quality/codesnippet/CSharp/ca2218-override-gethashcode-on-overriding-equals_3.cs)]  
  
### Kommentare  
 Im folgenden Beispiel wird der Verstoß korrigiert, indem <xref:System.Object.GetHashCode> überschrieben wird.  
  
### Code  
 [!code-cs[FxCop.Usage.GetHashCodeFixedStruct#1](../code-quality/codesnippet/CSharp/ca2218-override-gethashcode-on-overriding-equals_4.cs)]  
  
## Verwandte Regeln  
 [CA1046: Gleichheitsoperator für Referenztypen nicht überladen](../code-quality/ca1046-do-not-overload-operator-equals-on-reference-types.md)  
  
 [CA2225: Operatorüberladungen weisen benannte Alternativen auf](../code-quality/ca2225-operator-overloads-have-named-alternates.md)  
  
 [CA2226: Operatoren sollten symmetrische Überladungen aufweisen](../code-quality/ca2226-operators-should-have-symmetrical-overloads.md)  
  
 [CA2224: Equals beim Überladen von Gleichheitsoperatoren überschreiben](../code-quality/ca2224-override-equals-on-overloading-operator-equals.md)  
  
 [CA2231: Überladen Sie den Gleichheitsoperator beim Überschreiben von ValueType.Equals](../code-quality/ca2231-overload-operator-equals-on-overriding-valuetype-equals.md)  
  
## Siehe auch  
 <xref:System.Object.Equals%2A?displayProperty=fullName>   
 <xref:System.Object.GetHashCode%2A?displayProperty=fullName>   
 <xref:System.Collections.HashTable?displayProperty=fullName>   
 [Gleichheitsoperatoren](../Topic/Equality%20Operators.md)