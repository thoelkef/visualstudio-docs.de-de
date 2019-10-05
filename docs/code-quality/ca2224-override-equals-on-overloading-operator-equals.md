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
ms.openlocfilehash: 72bcf01b9c0613bb390ac9adbbba2fb176db13bd
ms.sourcegitcommit: 0c2523d975d48926dd2b35bcd2d32a8ae14c06d8
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/24/2019
ms.locfileid: "71231216"
---
# <a name="ca2224-override-equals-on-overloading-operator-equals"></a>CA2224: Equals beim Überladen von Gleichheitsoperatoren überschreiben.

|||
|-|-|
|TypeName|OverrideEqualsOnOverloadingOperatorEquals|
|CheckId|CA2224|
|Kategorie|Microsoft.Usage|
|Unterbrechende Änderung|Nicht unterbrechend|

## <a name="cause"></a>Ursache

Ein öffentlicher Typ implementiert den Gleichheits Operator, überschreibt jedoch <xref:System.Object.Equals%2A?displayProperty=fullName>nicht.

## <a name="rule-description"></a>Regelbeschreibung

Der Gleichheits Operator soll eine syntaktisch bequeme <xref:System.Object.Equals%2A> Methode für den Zugriff auf die Funktionen der Methode sein. Wenn Sie den Gleichheits Operator implementieren, muss die zugehörige Logik mit der <xref:System.Object.Equals%2A>von identisch sein.

Der C# Compiler gibt eine Warnung aus, wenn Ihr Code gegen diese Regel verstößt.

## <a name="how-to-fix-violations"></a>Behandeln von Verstößen

Um einen Verstoß gegen diese Regel zu beheben, sollten Sie entweder die Implementierung des Gleichheits Operators entfernen oder über <xref:System.Object.Equals%2A> schreiben und festlegen, dass die beiden Methoden dieselben Werte zurückgeben. Wenn der Gleichheits Operator kein inkonsistentes Verhalten einführt, können Sie die Verletzung beheben, indem Sie <xref:System.Object.Equals%2A> eine Implementierung von <xref:System.Object.Equals%2A> bereitstellen, die die-Methode in der Basisklasse aufruft.

## <a name="when-to-suppress-warnings"></a>Wann sollten Warnungen unterdrückt werden?

Es ist sicher, eine Warnung aus dieser Regel zu unterdrücken, wenn der Gleichheits Operator denselben Wert zurückgibt wie <xref:System.Object.Equals%2A>die geerbte Implementierung von. Die Beispiele in diesem Artikel enthalten einen Typ, mit dem eine Warnung aus dieser Regel sicher unterdrückt werden kann.

## <a name="examples-of-inconsistent-equality-definitions"></a>Beispiele für inkonsistente Gleichheits Definitionen

Das folgende Beispiel zeigt einen Typ mit inkonsistenten Definitionen der Gleichheit. `BadPoint`ändert die Bedeutung von Gleichheit durch Bereitstellen einer benutzerdefinierten Implementierung des Gleichheits Operators, jedoch nicht <xref:System.Object.Equals%2A> , sodass Sie identisch verhält.

[!code-csharp[FxCop.Usage.OperatorEqualsRequiresEquals#1](../code-quality/codesnippet/CSharp/ca2224-override-equals-on-overloading-operator-equals_1.cs)]

Der folgende Code testet das Verhalten von `BadPoint`.

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

Im folgenden Beispiel wird ein Typ gezeigt, der technisch gegen diese Regel verstößt, sich aber nicht auf inkonsistente Weise verhält.

[!code-csharp[FxCop.Usage.ValueTypeEquals#1](../code-quality/codesnippet/CSharp/ca2224-override-equals-on-overloading-operator-equals_3.cs)]

Der folgende Code testet das Verhalten von `GoodPoint`.

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

## <a name="class-example"></a>Klassen Beispiel

Das folgende Beispiel zeigt eine Klasse (Verweistyp), die gegen diese Regel verstößt.

[!code-csharp[FxCop.Usage.OverrideEqualsClassViolation#1](../code-quality/codesnippet/CSharp/ca2224-override-equals-on-overloading-operator-equals_5.cs)]

Im folgenden Beispiel wird die Verletzung durch über <xref:System.Object.Equals%2A?displayProperty=fullName>schreiben behoben.

[!code-csharp[FxCop.Usage.OverrideEqualsClassFixed#1](../code-quality/codesnippet/CSharp/ca2224-override-equals-on-overloading-operator-equals_6.cs)]

## <a name="structure-example"></a>Struktur Beispiel

Das folgende Beispiel zeigt eine Struktur (Werttyp), die gegen diese Regel verstößt:

[!code-csharp[FxCop.Usage.OverrideEqualsStructViolation#1](../code-quality/codesnippet/CSharp/ca2224-override-equals-on-overloading-operator-equals_7.cs)]

Im folgenden Beispiel wird die Verletzung durch über <xref:System.ValueType.Equals%2A?displayProperty=fullName>schreiben behoben.

[!code-csharp[FxCop.Usage.OverrideEqualsStructFixed#1](../code-quality/codesnippet/CSharp/ca2224-override-equals-on-overloading-operator-equals_8.cs)]

## <a name="related-rules"></a>Verwandte Regeln

[CA1046: Gleichheits Operator für Referenztypen nicht überladen](../code-quality/ca1046-do-not-overload-operator-equals-on-reference-types.md)

[CA2225: Operator Überladungen weisen benannte Alternativen auf](../code-quality/ca2225-operator-overloads-have-named-alternates.md)

[CA2226: Operatoren sollten symmetrische über Ladungen aufweisen](../code-quality/ca2226-operators-should-have-symmetrical-overloads.md)

[CA2218: GetHashCode beim Überschreiben von ist überschreiben](../code-quality/ca2218-override-gethashcode-on-overriding-equals.md)

[CA2231: Überladen Sie den Gleichheitsoperator beim Überschreiben von ValueType.Equals](../code-quality/ca2231-overload-operator-equals-on-overriding-valuetype-equals.md)