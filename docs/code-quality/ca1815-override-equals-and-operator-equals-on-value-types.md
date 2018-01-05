---
title: "CA1815: Override equals und Gleichheitsoperator für Werttypen | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- CA1815
- OverrideEqualsAndOperatorEqualsOnValueTypes
helpviewer_keywords:
- OverrideEqualsAndOperatorEqualsOnValueTypes
- CA1815
ms.assetid: 0a8ab3a3-ee8e-46f7-985d-dcf00c89363b
caps.latest.revision: "17"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 927e13266bf308096592fb5714e1247f4b596ca8
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/22/2017
---
# <a name="ca1815-override-equals-and-operator-equals-on-value-types"></a>CA1815: Equals und Gleichheitsoperator für Werttypen überschreiben
|||  
|-|-|  
|TypeName|OverrideEqualsAndOperatorEqualsOnValueTypes|  
|CheckId|CA1815|  
|Kategorie|Microsoft.Performance|  
|Unterbrechende Änderung|Nicht unterbrechend|  
  
## <a name="cause"></a>Ursache  
 Ein öffentlicher Werttyp überschreibt nicht <xref:System.Object.Equals%2A?displayProperty=fullName>, oder den Gleichheitsoperator (==) nicht implementiert. Diese Regel überprüft die Enumerationen nicht.  
  
## <a name="rule-description"></a>Regelbeschreibung  
 Bei der geerbten Implementierung von Werttypen <xref:System.Object.Equals%2A> wird die Reflection-Bibliothek verwendet, und der Inhalt aller Felder verglichen. Reflection ist rechenintensiv, und das Überprüfen eines jeden Felds auf Gleichheit ist eventuell unnötig. Wenn Sie erwarten, Benutzer mit Instanzen von vergleichen oder sortieren dass oder als Schlüssel für Hashtabellen verwenden, sollte der Werttyp implementieren <xref:System.Object.Equals%2A>. Wenn Ihre Programmiersprache Operatorüberladung unterstützt, sollten Sie ebenso eine Implementierung der Gleichheits- und Ungleichheitsoperatoren bereitstellen.  
  
## <a name="how-to-fix-violations"></a>Behandeln von Verstößen  
 Um einen Verstoß gegen diese Regel zu beheben, stellen Sie eine Implementierung von <xref:System.Object.Equals%2A>. Wenn Sie den Gleichheitsoperator implementieren können.  
  
## <a name="when-to-suppress-warnings"></a>Wann sollten Warnungen unterdrückt werden?  
 Sie können ruhig zum Unterdrücken einer Warnung dieser Regel, wenn Instanzen des Werttyps nicht miteinander verglichen werden.  
  
## <a name="example-of-a-violation"></a>Beispiel eines Verstoßes  
  
### <a name="description"></a>Beschreibung  
 Das folgende Beispiel zeigt eine Struktur (Werttyp), die mit dieser Regel verletzt.  
  
### <a name="code"></a>Code  
 [!code-csharp[FxCop.Performance.OverrideEqualsViolation#1](../code-quality/codesnippet/CSharp/ca1815-override-equals-and-operator-equals-on-value-types_1.cs)]  
  
## <a name="example-of-how-to-fix"></a>Beispiel für die Korrektur  
  
### <a name="description"></a>Beschreibung  
 Im folgenden Beispiel wird der vorherige Verstoß durch Überschreiben korrigiert <xref:System.ValueType.Equals%2A?displayProperty=fullName> und die Gleichheitsoperatoren (==,! =).  
  
### <a name="code"></a>Code  
 [!code-csharp[FxCop.Performance.OverrideEqualsFixed#1](../code-quality/codesnippet/CSharp/ca1815-override-equals-and-operator-equals-on-value-types_2.cs)]  
  
## <a name="related-rules"></a>Verwandte Regeln  
 [CA2224: Equals beim Überladen von Gleichheitsoperatoren überschreiben](../code-quality/ca2224-override-equals-on-overloading-operator-equals.md)  
  
 [CA2231: Überladen Sie den Gleichheitsoperator beim Überschreiben von ValueType.Equals](../code-quality/ca2231-overload-operator-equals-on-overriding-valuetype-equals.md)  
  
 [CA2226: Operatoren sollten symmetrische Überladungen aufweisen](../code-quality/ca2226-operators-should-have-symmetrical-overloads.md)  
  
## <a name="see-also"></a>Siehe auch  
 <xref:System.Object.Equals%2A?displayProperty=fullName>