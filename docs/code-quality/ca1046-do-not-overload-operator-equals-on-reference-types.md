---
title: 'CA1046: Gleichheitsoperator für Referenztypen nicht überladen.'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- DoNotOverloadOperatorEqualsOnReferenceTypes
- CA1046
helpviewer_keywords:
- CA1046
- DoNotOverloadOperatorEqualsOnReferenceTypes
ms.assetid: c1dfbfe3-63f9-4005-a81a-890427b77e79
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 9f9304fcd86a9b36a729b1436fe16471b449ac0d
ms.sourcegitcommit: 21d667104199c2493accec20c2388cf674b195c3
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2019
ms.locfileid: "55953762"
---
# <a name="ca1046-do-not-overload-operator-equals-on-reference-types"></a>CA1046: Gleichheitsoperator für Referenztypen nicht überladen.

|||
|-|-|
|TypeName|DoNotOverrideOperatorEqualsOnReferenceTypes|
|CheckId|CA1046|
|Kategorie|Microsoft.Design|
|Unterbrechende Änderung|Breaking|

## <a name="cause"></a>Ursache
 Ein öffentlicher oder verschachtelter öffentlicher Verweistyp überlädt den Equality-Operator.

## <a name="rule-description"></a>Regelbeschreibung
 Für Verweistypen ist die Standardimplementierung des Gleichheitsoperators fast immer zutreffend. Standardmäßig sind zwei Verweise nur dann gleich, wenn sie auf dasselbe Objekt zeigen.

## <a name="how-to-fix-violations"></a>Behandeln von Verstößen
 Um einen Verstoß gegen diese Regel zu beheben, entfernen Sie die Implementierung des Gleichheitsoperators.

## <a name="when-to-suppress-warnings"></a>Wenn Sie Warnungen unterdrücken
 Es ist sicher ist, eine Warnung dieser Regel zu unterdrücken, wenn sich der Verweistyp wie eines integrierten Werttyps verhält. Wenn es für die Addition oder Subtraktion auf Instanzen des Typs ist von Bedeutung ist, ist es wahrscheinlich richtig ist, den Gleichheitsoperator zu implementieren und den Regelverstoß zu unterdrücken.

## <a name="example"></a>Beispiel
 Das folgende Beispiel veranschaulicht das Standardverhalten für den Vergleich zwei Verweise.

 [!code-csharp[FxCop.Design.RefTypesNoEqualityOp#1](../code-quality/codesnippet/CSharp/ca1046-do-not-overload-operator-equals-on-reference-types_1.cs)]

## <a name="example"></a>Beispiel

Folgende Anwendungen werden einige Verweise verglichen.

[!code-csharp[FxCop.Design.TestRefTypesNoEqualityOp#1](../code-quality/codesnippet/CSharp/ca1046-do-not-overload-operator-equals-on-reference-types_2.cs)]

Dieses Beispiel erzeugt die folgende Ausgabe:

```txt
a = new (2,2) and b = new (2,2) are equal? No
c and a are equal? Yes
b and a are == ? No
c and a are == ? Yes
```

## <a name="related-rules"></a>Verwandte Regeln

[CA1013: Gleichheitsoperator beim Überladen von Addition und Subtraktion](../code-quality/ca1013-overload-operator-equals-on-overloading-add-and-subtract.md)

## <a name="see-also"></a>Siehe auch

- <xref:System.Object.Equals%2A?displayProperty=fullName>
- [Gleichheitsoperatoren](/dotnet/standard/design-guidelines/equality-operators)