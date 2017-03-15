---
title: "CA1815: Equals und Gleichheitsoperator f&#252;r Werttypen &#252;berschreiben | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CA1815"
  - "OverrideEqualsAndOperatorEqualsOnValueTypes"
helpviewer_keywords: 
  - "OverrideEqualsAndOperatorEqualsOnValueTypes"
  - "CA1815"
ms.assetid: 0a8ab3a3-ee8e-46f7-985d-dcf00c89363b
caps.latest.revision: 17
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
caps.handback.revision: 17
---
# CA1815: Equals und Gleichheitsoperator f&#252;r Werttypen &#252;berschreiben
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|OverrideEqualsAndOperatorEqualsOnValueTypes|  
|CheckId|CA1815|  
|Kategorie \(Category\)|Microsoft.Performance|  
|Unterbrechende Änderung|Nicht unterbrechend|  
  
## Ursache  
 Von einem öffentlichen Werttyp wird <xref:System.Object.Equals%2A?displayProperty=fullName> nicht überschrieben, bzw. der Gleichheitsoperator \(\=\=\) wird nicht implementiert.  Diese Regel überprüft keine Enumerationen.  
  
## Regelbeschreibung  
 Bei Werttypen wird die Reflection\-Bibliothek von der geerbten Implementierung von <xref:System.Object.Equals%2A> verwendet und der Inhalt aller Felder verglichen.  Reflection ist rechenintensiv, und das Überprüfen eines jeden Felds auf Gleichheit ist eventuell unnötig.  Wenn Sie erwarten, dass die Benutzer Instanzen vergleichen oder sortieren bzw. dass sie die Instanzen als Schlüssel für Hashtabellen verwenden, sollte der Werttyp <xref:System.Object.Equals%2A> implementieren.  Wenn die Programmiersprache das Überladen von Operatoren unterstützt, sollten Sie außerdem eine Implementierung der Gleichheits\- und Ungleichheitsoperatoren bereitstellen.  
  
## Behandeln von Verstößen  
 Um einen Verstoß gegen diese Regel zu beheben, stellen Sie eine Implementierung von <xref:System.Object.Equals%2A> bereit.  Implementieren Sie den Gleichheitsoperator, falls dies möglich ist.  
  
## Wann sollten Warnungen unterdrückt werden?  
 Eine Warnung dieser Regel kann gefahrlos unterdrückt werden, wenn Instanzen des Werttyps nicht miteinander verglichen werden.  
  
## Beispiel für einen Verstoß  
  
### **Beschreibung**  
 Im folgenden Beispiel wird eine Struktur \(Werttyp\) veranschaulicht, die gegen diese Regel verstößt.  
  
### Code  
 [!code-cs[FxCop.Performance.OverrideEqualsViolation#1](../code-quality/codesnippet/CSharp/ca1815-override-equals-and-operator-equals-on-value-types_1.cs)]  
  
## Beispiel für die Behandlung  
  
### **Beschreibung**  
 Im folgenden Beispiel wird der vorherige Verstoß korrigiert, indem <xref:System.ValueType.Equals%2A?displayProperty=fullName> überschrieben und die Gleichheitsoperatoren \(\=\=, \!\=\) implementiert werden.  
  
### Code  
 [!code-cs[FxCop.Performance.OverrideEqualsFixed#1](../code-quality/codesnippet/CSharp/ca1815-override-equals-and-operator-equals-on-value-types_2.cs)]  
  
## Verwandte Regeln  
 [CA2224: Equals beim Überladen von Gleichheitsoperatoren überschreiben](../code-quality/ca2224-override-equals-on-overloading-operator-equals.md)  
  
 [CA2231: Überladen Sie den Gleichheitsoperator beim Überschreiben von ValueType.Equals](../code-quality/ca2231-overload-operator-equals-on-overriding-valuetype-equals.md)  
  
 [CA2226: Operatoren sollten symmetrische Überladungen aufweisen](../code-quality/ca2226-operators-should-have-symmetrical-overloads.md)  
  
## Siehe auch  
 <xref:System.Object.Equals%2A?displayProperty=fullName>