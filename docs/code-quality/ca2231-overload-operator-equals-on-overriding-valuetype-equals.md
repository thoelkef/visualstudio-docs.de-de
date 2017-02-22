---
title: "CA2231: &#220;berladen Sie den Gleichheitsoperator beim &#220;berschreiben von ValueType.Equals | Microsoft Docs"
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
  - "OverloadOperatorEqualsOnOverridingValueTypeEquals"
  - "CA2231"
  - "OverrideOperatorEqualsOnOverridingValueTypeEquals"
helpviewer_keywords: 
  - "CA2231"
  - "OverloadOperatorEqualsOnOverridingValueTypeEquals"
ms.assetid: 114c0161-261a-40ad-8b2c-0932d6909d2a
caps.latest.revision: 17
caps.handback.revision: 17
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# CA2231: &#220;berladen Sie den Gleichheitsoperator beim &#220;berschreiben von ValueType.Equals
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|OverloadOperatorEqualsOnOverridingValueTypeEquals|  
|CheckId|CA2231|  
|Kategorie \(Category\)|Microsoft.Usage|  
|Unterbrechende Änderung|Nicht unterbrechend|  
  
## Ursache  
 Ein Werttyp überschreibt <xref:System.Object.Equals%2A?displayProperty=fullName>, implementiert jedoch den Gleichheitsoperator nicht.  
  
## Regelbeschreibung  
 In den meisten Programmiersprachen gibt es keine Standardimplementierung des Gleichheitsoperators \(\=\=\) für Werttypen.  Wenn die verwendete Programmiersprache Operatorüberladungen unterstützt, sollten Sie erwägen, den Gleichheitsoperator zu implementieren.  Das Verhalten des Gleichheitsoperators sollte mit dem von <xref:System.Object.Equals%2A> übereinstimmen.  
  
 Sie können den Standardgleichheitsoperator nicht in einer überladenen Implementierung des Gleichheitsoperators verwenden.  Eine solche Vorgehensweise führt zu einem Stapelüberlauf.  Verwenden Sie zur Implementierung des Gleichheitsoperators die Object.Equals\-Methode.  Beispiel:  
  
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
 Um einen Verstoß gegen diese Regel zu beheben, implementieren Sie den Gleichheitsoperator.  
  
## Wann sollten Warnungen unterdrückt werden?  
 Eine Warnung dieser Regel kann gefahrlos unterdrückt werden. Es wird jedoch empfohlen, den Gleichheitsoperator bereitzustellen, falls dies möglich ist.  
  
## Beispiel  
 Im folgenden Beispiel wird ein Typ definiert, der gegen diese Regel verstößt.  
  
 [!code-cs[FxCop.Usage.EqualsGetHashCode#1](../code-quality/codesnippet/CSharp/ca2231-overload-operator-equals-on-overriding-valuetype-equals_1.cs)]  
  
## Verwandte Regeln  
 [CA1046: Gleichheitsoperator für Referenztypen nicht überladen](../code-quality/ca1046-do-not-overload-operator-equals-on-reference-types.md)  
  
 [CA2225: Operatorüberladungen weisen benannte Alternativen auf](../code-quality/ca2225-operator-overloads-have-named-alternates.md)  
  
 [CA2226: Operatoren sollten symmetrische Überladungen aufweisen](../code-quality/ca2226-operators-should-have-symmetrical-overloads.md)  
  
 [CA2224: Equals beim Überladen von Gleichheitsoperatoren überschreiben](../code-quality/ca2224-override-equals-on-overloading-operator-equals.md)  
  
 [CA2218: GetHashCode beim Überschreiben von Equals überschreiben](../code-quality/ca2218-override-gethashcode-on-overriding-equals.md)  
  
## Siehe auch  
 <xref:System.Object.Equals%2A?displayProperty=fullName>