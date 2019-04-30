---
title: 'CA2224: Equals beim Überladen von Gleichheitsoperatoren überschreiben.'
ms.date: 11/04/2016
ms.topic: reference
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
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 3fa6bfa5b590d330d791eb8c735099e619ffaf3a
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62541909"
---
# <a name="ca2224-override-equals-on-overloading-operator-equals"></a>CA2224: Equals beim Überladen von Gleichheitsoperatoren überschreiben.

|||
|-|-|
|TypeName|OverrideEqualsOnOverloadingOperatorEquals|
|CheckId|CA2224|
|Kategorie|Microsoft.Usage|
|Unterbrechende Änderung|Nicht unterbrechende Änderung|

## <a name="cause"></a>Ursache

Ein öffentlicher Typ implementiert den Gleichheitsoperator, aber überschreibt nicht die <xref:System.Object.Equals%2A?displayProperty=fullName>.

## <a name="rule-description"></a>Regelbeschreibung

Der Gleichheitsoperator syntaktisch bequem Zugriff auf die Funktionen werden die <xref:System.Object.Equals%2A> Methode. Wenn Sie den Gleichheitsoperator implementieren, die Logik muss identisch mit dem der <xref:System.Object.Equals%2A>.

Der C#-Compiler gibt eine Warnung aus, wenn Ihr Code gegen diese Regel verstößt.

## <a name="how-to-fix-violations"></a>Behandeln von Verstößen

Um einen Verstoß gegen diese Regel zu beheben, sollten Sie entweder entfernen Sie die Implementierung des Gleichheitsoperators oder außer Kraft setzen <xref:System.Object.Equals%2A> und haben die beiden Methoden die gleichen Werte zurückgibt. Wenn der Gleichheitsoperator nicht inkonsistentes Verhalten einleitet, können Sie den Verstoß beheben, indem eine Implementierung von <xref:System.Object.Equals%2A> aufruft, die <xref:System.Object.Equals%2A> -Methode in der Basisklasse.

## <a name="when-to-suppress-warnings"></a>Wenn Sie Warnungen unterdrücken

Es ist sicherer, eine Warnung dieser Regel zu unterdrücken, sofern es sich bei der Equality-Operator gibt zurück, den gleichen Wert wie der geerbten Implementierung von <xref:System.Object.Equals%2A>. In die Beispielen in diesem Artikel enthalten einen Typ, der sicher unterdrücken Sie eine Warnung dieser Regel kann.

## <a name="examples-of-inconsistent-equality-definitions"></a>Beispiele für Gleichheitsdefinitionen von inkonsistenten

Das folgende Beispiel zeigt einen Typ mit inkonsistente Definitionen auf Wertgleichheit. `BadPoint` Ändert die Bedeutung der Gleichheit, indem eine benutzerdefinierte Implementierung des Gleichheitsoperators jedoch überschreibt nicht die <xref:System.Object.Equals%2A> , damit es identisch verhält.

[!code-csharp[FxCop.Usage.OperatorEqualsRequiresEquals#1](../code-quality/codesnippet/CSharp/ca2224-override-equals-on-overloading-operator-equals_1.cs)]

Der folgende Code überprüft das Verhalten der `BadPoint`.

[!code-csharp[FxCop.Usage.TestOperatorEqualsRequiresEquals#1](../code-quality/codesnippet/CSharp/ca2224-override-equals-on-overloading-operator-equals_2.cs)]

Dieses Beispiel erzeugt die folgende Ausgabe:

```txt
a =  ([0] 1,1) and b = ([1] 2,2) are equal? No
a == b ? No
a1 and a are equal? Yes
a1 == a ? Yes
b and bcopy are equal ? No
b == bcopy ? Yes
```

Das folgende Beispiel zeigt einen Typ, der technisch verstößt gegen diese Regel, aber nicht in einem inkonsistenten Weise verhält.

[!code-csharp[FxCop.Usage.ValueTypeEquals#1](../code-quality/codesnippet/CSharp/ca2224-override-equals-on-overloading-operator-equals_3.cs)]

Der folgende Code überprüft das Verhalten der `GoodPoint`.

[!code-csharp[FxCop.Usage.TestValueTypeEquals#1](../code-quality/codesnippet/CSharp/ca2224-override-equals-on-overloading-operator-equals_4.cs)]

Dieses Beispiel erzeugt die folgende Ausgabe:

```txt
a =  (1,1) and b = (2,2) are equal? No
a == b ? No
a1 and a are equal? Yes
a1 == a ? Yes
b and bcopy are equal ? Yes
b == bcopy ? Yes
```

## <a name="class-example"></a>Beispiel:

Das folgende Beispiel zeigt eine Klasse (Referenztyp), die gegen diese Regel verstößt.

[!code-csharp[FxCop.Usage.OverrideEqualsClassViolation#1](../code-quality/codesnippet/CSharp/ca2224-override-equals-on-overloading-operator-equals_5.cs)]

Im folgenden Beispiel wird der Verstoß durch Überschreiben korrigiert <xref:System.Object.Equals%2A?displayProperty=fullName>.

[!code-csharp[FxCop.Usage.OverrideEqualsClassFixed#1](../code-quality/codesnippet/CSharp/ca2224-override-equals-on-overloading-operator-equals_6.cs)]

## <a name="structure-example"></a>Struktur-Beispiel

Das folgende Beispiel zeigt eine Struktur (Werttyp), die gegen diese Regel verstößt:

[!code-csharp[FxCop.Usage.OverrideEqualsStructViolation#1](../code-quality/codesnippet/CSharp/ca2224-override-equals-on-overloading-operator-equals_7.cs)]

Im folgenden Beispiel wird der Verstoß durch Überschreiben korrigiert <xref:System.ValueType.Equals%2A?displayProperty=fullName>.

[!code-csharp[FxCop.Usage.OverrideEqualsStructFixed#1](../code-quality/codesnippet/CSharp/ca2224-override-equals-on-overloading-operator-equals_8.cs)]

## <a name="related-rules"></a>Verwandte Regeln

[CA1046: Gleichheitsoperator für Referenztypen nicht überladen](../code-quality/ca1046-do-not-overload-operator-equals-on-reference-types.md)

[CA2225: Operatorüberladungen weisen benannte alternativen auf](../code-quality/ca2225-operator-overloads-have-named-alternates.md)

[CA2226: Operatoren sollten symmetrische Überladungen aufweisen.](../code-quality/ca2226-operators-should-have-symmetrical-overloads.md)

[CA2218: Überschreiben von GetHashCode beim Überschreiben von Equals überschreiben](../code-quality/ca2218-override-gethashcode-on-overriding-equals.md)

[CA2231: Überladen Sie den Gleichheitsoperator beim Überschreiben von ValueType.Equals](../code-quality/ca2231-overload-operator-equals-on-overriding-valuetype-equals.md)