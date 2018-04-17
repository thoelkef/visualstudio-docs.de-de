---
title: 'CA2224: Überschreiben von equals beim Überladen des Gleichheitsoperators | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-code-analysis
ms.topic: conceptual
f1_keywords:
- CA2224
- OverrideEqualsOnOverloadingOperatorEquals
- OverrideEqualsOnOverridingOperatorEquals
helpviewer_keywords:
- OverrideEqualsOnOverloadingOperatorEquals
- CA2224
ms.assetid: 7312afd9-84ba-417f-923e-7a159b53bf70
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 9931e359b866573099723faa91b147d44f17e3bb
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/16/2018
---
# <a name="ca2224-override-equals-on-overloading-operator-equals"></a>CA2224: Equals beim Überladen von Gleichheitsoperatoren überschreiben
|||  
|-|-|  
|TypeName|OverrideEqualsOnOverloadingOperatorEquals|  
|CheckId|CA2224|  
|Kategorie|Microsoft.Usage|  
|Unterbrechende Änderung|Nicht unterbrechende Änderung|  
  
## <a name="cause"></a>Ursache  
 Ein öffentlicher Typ implementiert den Gleichheitsoperator, aber nicht außer Kraft setzen <xref:System.Object.Equals%2A?displayProperty=fullName>.  
  
## <a name="rule-description"></a>Regelbeschreibung  
 Der Gleichheitsoperator soll eine syntaktisch bequeme Methode zum Zugriff auf die Funktionen der <xref:System.Object.Equals%2A> Methode. Wenn Sie den Gleichheitsoperator zu implementieren, muss die Logik der identisch sein <xref:System.Object.Equals%2A>.  
  
 Der C#-Compiler gibt eine Warnung aus, wenn der Code mit dieser Regel verletzt.  
  
## <a name="how-to-fix-violations"></a>Behandeln von Verstößen  
 Um einen Verstoß gegen diese Regel zu beheben, sollten Sie entweder entfernen Sie die Implementierung des Gleichheitsoperators oder override <xref:System.Object.Equals%2A> und haben die beiden Methoden die gleichen Werte zurückgeben. Wenn Sie der Gleichheitsoperator keine inkonsistentes Verhalten entstehen, können Sie die Verletzung beheben, indem eine Implementierung von <xref:System.Object.Equals%2A> aufruft, die die <xref:System.Object.Equals%2A> Methode in der Basisklasse.  
  
## <a name="when-to-suppress-warnings"></a>Wann sollten Warnungen unterdrückt werden?  
 Ist eine Warnung dieser Regel zu unterdrücken, sofern der Gleichheitsoperator den gleichen Wert wie der geerbten Implementierung von zurückgibt sicher <xref:System.Object.Equals%2A>. Im Abschnitt Beispiel umfasst einen Typ, der gefahrlos unterdrücken Sie eine Warnung dieser Regel konnte.  
  
## <a name="examples-of-inconsistent-equality-definitions"></a>Beispiele für Gleichheitsdefinitionen inkonsistent  
  
### <a name="description"></a>Beschreibung  
 Das folgende Beispiel zeigt einen Typ mit inkonsistenten Definitionen auf Wertgleichheit. `BadPoint` Ändert die Bedeutung der Gleichheit, indem eine benutzerdefinierte Implementierung des Gleichheitsoperators jedoch nicht außer Kraft setzen <xref:System.Object.Equals%2A> , damit es identisch verhält.  
  
### <a name="code"></a>Code  
 [!code-csharp[FxCop.Usage.OperatorEqualsRequiresEquals#1](../code-quality/codesnippet/CSharp/ca2224-override-equals-on-overloading-operator-equals_1.cs)]  
  
## <a name="example"></a>Beispiel  
 Der folgende Code überprüft das Verhalten des `BadPoint`.  
  
 [!code-csharp[FxCop.Usage.TestOperatorEqualsRequiresEquals#1](../code-quality/codesnippet/CSharp/ca2224-override-equals-on-overloading-operator-equals_2.cs)]  
  
 Folgende Ergebnisse werden zurückgegeben:  
  
 **a = ([0] 1,1) und b = ([1] 2,2) sind gleich? Nein**  
**eine b ==? Nein**  
**a1 und a sind gleich? Ja**  
**a1 == ein? Ja**  
**b und viele sind gleich? Nein**  
**b == viele? Ja**   
## <a name="example"></a>Beispiel  
 Das folgende Beispiel zeigt einen Typ, der technisch verstößt gegen diese Regel, aber verhält sich inkonsistent nicht.  
  
 [!code-csharp[FxCop.Usage.ValueTypeEquals#1](../code-quality/codesnippet/CSharp/ca2224-override-equals-on-overloading-operator-equals_3.cs)]  
  
## <a name="example"></a>Beispiel  
 Der folgende Code überprüft das Verhalten des `GoodPoint`.  
  
 [!code-csharp[FxCop.Usage.TestValueTypeEquals#1](../code-quality/codesnippet/CSharp/ca2224-override-equals-on-overloading-operator-equals_4.cs)]  
  
 Folgende Ergebnisse werden zurückgegeben:  
  
 **a = (1,1) und b = (2,2) sind gleich? Nein**  
**eine b ==? Nein**  
**a1 und a sind gleich? Ja**  
**a1 == ein? Ja**  
**b und viele sind gleich? Ja**  
**b == viele? Ja**   
## <a name="class-example"></a>Beispiel für die Klasse  
  
### <a name="description"></a>Beschreibung  
 Das folgende Beispiel zeigt eine Klasse (Referenztyp), die mit dieser Regel verletzt.  
  
### <a name="code"></a>Code  
 [!code-csharp[FxCop.Usage.OverrideEqualsClassViolation#1](../code-quality/codesnippet/CSharp/ca2224-override-equals-on-overloading-operator-equals_5.cs)]  
  
## <a name="example"></a>Beispiel  
 Im folgenden Beispiel wird der Verstoß durch Überschreiben korrigiert <xref:System.Object.Equals%2A?displayProperty=fullName>.  
  
 [!code-csharp[FxCop.Usage.OverrideEqualsClassFixed#1](../code-quality/codesnippet/CSharp/ca2224-override-equals-on-overloading-operator-equals_6.cs)]  
  
## <a name="structure-example"></a>Struktur-Beispiel  
  
### <a name="description"></a>Beschreibung  
 Das folgende Beispiel zeigt eine Struktur (Werttyp), die mit dieser Regel verletzt.  
  
### <a name="code"></a>Code  
 [!code-csharp[FxCop.Usage.OverrideEqualsStructViolation#1](../code-quality/codesnippet/CSharp/ca2224-override-equals-on-overloading-operator-equals_7.cs)]  
  
## <a name="example"></a>Beispiel  
 Im folgenden Beispiel wird der Verstoß durch Überschreiben korrigiert <xref:System.ValueType.Equals%2A?displayProperty=fullName>.  
  
 [!code-csharp[FxCop.Usage.OverrideEqualsStructFixed#1](../code-quality/codesnippet/CSharp/ca2224-override-equals-on-overloading-operator-equals_8.cs)]  
  
## <a name="related-rules"></a>Verwandte Regeln  
 [CA1046: Gleichheitsoperator für Referenztypen nicht überladen](../code-quality/ca1046-do-not-overload-operator-equals-on-reference-types.md)  
  
 [CA2225: Operatorüberladungen weisen benannte Alternativen auf](../code-quality/ca2225-operator-overloads-have-named-alternates.md)  
  
 [CA2226: Operatoren sollten symmetrische Überladungen aufweisen](../code-quality/ca2226-operators-should-have-symmetrical-overloads.md)  
  
 [CA2218: GetHashCode beim Überschreiben von Equals überschreiben](../code-quality/ca2218-override-gethashcode-on-overriding-equals.md)  
  
 [CA2231: Überladen Sie den Gleichheitsoperator beim Überschreiben von ValueType.Equals](../code-quality/ca2231-overload-operator-equals-on-overriding-valuetype-equals.md)