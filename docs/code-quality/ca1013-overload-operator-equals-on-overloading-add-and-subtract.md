---
title: 'CA1013: Gleichheitsoperator beim Überladen von Addition und Subtraktion überladen.'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- OverrideOperatorEqualsOnOverridingAddAndSubtract
- OverrideOperatorEqualsOnOverloadingAddAndSubtract
- CA1013
- OverloadOperatorEqualsOnOverloadingAddAndSubtract
helpviewer_keywords:
- OverrideOperatorEqualsOnOverloadingAddAndSubtract
- OverrideOperatorEqualsOnOverridingAddAndSubtract
- CA1013
- OverloadOperatorEqualsOnOverloadingAddAndSubtract
ms.assetid: 5bd28d68-c179-49ff-af47-5250b8b18a10
author: gewarren
ms.author: gewarren
manager: jillfra
dev_langs:
- CSharp
- VB
ms.workload:
- multiple
ms.openlocfilehash: 76a3790f57882071bddc90ef78a0ac74dd565514
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62779582"
---
# <a name="ca1013-overload-operator-equals-on-overloading-add-and-subtract"></a>CA1013: Gleichheitsoperator beim Überladen von Addition und Subtraktion überladen.

|||
|-|-|
|TypeName|OverloadOperatorEqualsOnOverloadingAddAndSubtract|
|CheckId|CA1013|
|Kategorie|Microsoft.Design|
|Unterbrechende Änderung|Nicht unterbrechend|

## <a name="cause"></a>Ursache
 Ein öffentlicher oder geschützter Typ implementiert den Additions- oder Subtraktionsoperator, ohne den Gleichheitsoperator zu implementieren.

## <a name="rule-description"></a>Regelbeschreibung
 Wenn Instanzen eines Typs mit Operationen wie Addition und Subtraktion kombiniert werden können, sollten Sie fast immer definieren die Gleichheit zurückzugebenden `true` zwei Instanzen, die die gleichen konstituierenden Werte aufweisen.

 Sie können nicht den standardmäßigen Equality-Operator in einer überladenen Implementierung des Gleichheitsoperators verwenden. Auf diese Weise wird die einen Stapelüberlauf verursachen. Um den Gleichheitsoperator zu implementieren, verwenden Sie die Object.Equals-Methode in Ihrer Implementierung. Weitere Informationen finden Sie im folgenden Beispiel.

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
 Um einen Verstoß gegen diese Regel zu beheben, implementieren Sie den Gleichheitsoperator, damit sie mit den Operatoren für Addition und Subtraktion mathematisch konsistent ist.

## <a name="when-to-suppress-warnings"></a>Wenn Sie Warnungen unterdrücken
 Es ist sicher, um eine Warnung dieser Regel zu unterdrücken, wenn es sich bei der Standardimplementierung des Gleichheitsoperators das richtige Verhalten für den Typ bereitstellt.

## <a name="example"></a>Beispiel
 Das folgende Beispiel definiert einen Typ (`BadAddableType`), die gegen diese Regel verstößt. Dieser Typ sollte den Gleichheitsoperator, damit zwei Instanzen, die die Feldwerten testen implementieren `true` hinsichtlich ihrer Gleichheit. Der Typ `GoodAddableType` zeigt die korrigierte Implementierung. Beachten Sie, dass dieser Typ wird auch den Inequality-Operator implementiert und überschreibt <xref:System.Object.Equals%2A> zu anderen Regeln erfüllen. Eine vollständige Implementierung würde auch implementieren <xref:System.Object.GetHashCode%2A>.

 [!code-csharp[FxCop.Design.AddAndSubtract#1](../code-quality/codesnippet/CSharp/ca1013-overload-operator-equals-on-overloading-add-and-subtract_1.cs)]

## <a name="example"></a>Beispiel
 Im folgende Beispiel testet auf Gleichheit mit Instanzen der Typen, die zuvor in diesem Thema erläutern Sie den standardmäßigen und das richtige Verhalten für den Equality-Operator definiert wurden.

 [!code-csharp[FxCop.Design.TestAddAndSubtract#1](../code-quality/codesnippet/CSharp/ca1013-overload-operator-equals-on-overloading-add-and-subtract_2.cs)]

Dieses Beispiel erzeugt die folgende Ausgabe:

```txt
Bad type:  {2,2} {2,2} are equal? No
Good type: {3,3} {3,3} are equal? Yes
Good type: {3,3} {3,3} are == ?   Yes
Bad type:  {2,2} {9,9} are equal? No
Good type: {3,3} {9,9} are == ?   No
```

## <a name="see-also"></a>Siehe auch

- [Gleichheitsoperatoren](/dotnet/standard/design-guidelines/equality-operators)