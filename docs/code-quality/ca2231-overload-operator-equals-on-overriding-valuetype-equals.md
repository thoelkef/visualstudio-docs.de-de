---
title: 'CA2231: Überladen Sie den Gleichheitsoperator beim Überschreiben von ValueType.Equals'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- OverloadOperatorEqualsOnOverridingValueTypeEquals
- CA2231
- OverrideOperatorEqualsOnOverridingValueTypeEquals
helpviewer_keywords:
- OverloadOperatorEqualsOnOverridingValueTypeEquals
- CA2231
ms.assetid: 114c0161-261a-40ad-8b2c-0932d6909d2a
author: gewarren
ms.author: gewarren
manager: douge
dev_langs:
- CSharp
- VB
ms.workload:
- multiple
ms.openlocfilehash: b7965665ea59da6833a01885201a25f1e24b80ca
ms.sourcegitcommit: 568bb0b944d16cfe1af624879fa3d3594d020187
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/13/2018
ms.locfileid: "45547382"
---
# <a name="ca2231-overload-operator-equals-on-overriding-valuetypeequals"></a>CA2231: Überladen Sie den Gleichheitsoperator beim Überschreiben von ValueType.Equals
|||
|-|-|
|TypeName|OverloadOperatorEqualsOnOverridingValueTypeEquals|
|CheckId|CA2231|
|Kategorie|Microsoft.Usage|
|Unterbrechende Änderung|Nicht unterbrechende Änderung|

## <a name="cause"></a>Ursache
 Ein Werttyp überschreibt <xref:System.Object.Equals%2A?displayProperty=fullName> jedoch nicht den Gleichheitsoperator implementiert wird.

## <a name="rule-description"></a>Regelbeschreibung
 In den meisten Programmiersprachen ist es keine Standardimplementierung des Gleichheitsoperators (==) für Werttypen. Wenn Ihre bevorzugte Programmiersprache operatorüberladungen unterstützt, sollten Sie erwägen, den Gleichheitsoperator zu implementieren. Das Verhalten muss identisch mit dem der <xref:System.Object.Equals%2A>.

 Sie können nicht den standardmäßigen Equality-Operator in einer überladenen Implementierung des Gleichheitsoperators verwenden. Auf diese Weise wird die einen Stapelüberlauf verursachen. Um den Gleichheitsoperator zu implementieren, verwenden Sie die Object.Equals-Methode in Ihrer Implementierung. Zum Beispiel:

```vb
If (Object.ReferenceEquals(left, Nothing)) Then
    Return Object.ReferenceEquals(right, Nothing)
Else
    Return left.Equals(right)
End If
```

```csharp
if (Object.ReferenceEquals(left, null))
    return Object.ReferenceEquals(right, null);
return left.Equals(right);
```

## <a name="how-to-fix-violations"></a>Behandeln von Verstößen
 Um einen Verstoß gegen diese Regel zu beheben, müssen implementieren Sie den Gleichheitsoperator.

## <a name="when-to-suppress-warnings"></a>Wenn Sie Warnungen unterdrücken
 Es ist sicher ist, unterdrücken Sie eine Warnung dieser Regel. Allerdings empfiehlt es sich, dass Sie nach Möglichkeit den Equality-Operator angeben.

## <a name="example"></a>Beispiel
 Das folgende Beispiel definiert einen Typ, der gegen diese Regel verstößt.

 [!code-csharp[FxCop.Usage.EqualsGetHashCode#1](../code-quality/codesnippet/CSharp/ca2231-overload-operator-equals-on-overriding-valuetype-equals_1.cs)]

## <a name="related-rules"></a>Verwandte Regeln
 [CA1046: Gleichheitsoperator für Referenztypen nicht überladen](../code-quality/ca1046-do-not-overload-operator-equals-on-reference-types.md)

 [CA2225: Operatorüberladungen weisen benannte Alternativen auf](../code-quality/ca2225-operator-overloads-have-named-alternates.md)

 [CA2226: Operatoren sollten symmetrische Überladungen aufweisen](../code-quality/ca2226-operators-should-have-symmetrical-overloads.md)

 [CA2224: Equals beim Überladen von Gleichheitsoperatoren überschreiben](../code-quality/ca2224-override-equals-on-overloading-operator-equals.md)

 [CA2218: GetHashCode beim Überschreiben von Equals überschreiben](../code-quality/ca2218-override-gethashcode-on-overriding-equals.md)

## <a name="see-also"></a>Siehe auch

- <xref:System.Object.Equals%2A?displayProperty=fullName>