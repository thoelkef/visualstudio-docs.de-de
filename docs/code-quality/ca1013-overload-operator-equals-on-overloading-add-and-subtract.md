---
title: 'CA1013: Gleichheitsoperator beim Überladen von Addition und Subtraktion überladen'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-code-analysis
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
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 11841248192bc9b726076641e1219f54ab526447
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/26/2018
---
# <a name="ca1013-overload-operator-equals-on-overloading-add-and-subtract"></a>CA1013: Gleichheitsoperator beim Überladen von Addition und Subtraktion überladen
|||
|-|-|
|TypeName|OverloadOperatorEqualsOnOverloadingAddAndSubtract|
|CheckId|CA1013|
|Kategorie|Microsoft.Design|
|Unterbrechende Änderung|Nicht unterbrechend|

## <a name="cause"></a>Ursache
 Ein öffentlicher oder geschützter Typ implementiert den Additions- oder Subtraktionsoperator, ohne den Gleichheitsoperator zu implementieren.

## <a name="rule-description"></a>Regelbeschreibung
 Wenn Instanzen eines Typs mithilfe von Operationen wie Addition und Subtraktion kombiniert werden können, sollten Sie fast immer Gleichheit zurückzugebenden definieren `true` zwei Instanzen, die die gleichen konstituierenden Werte aufweisen.

 Sie können nicht den Gleichheitsoperator standardmäßig in einer überladenen Implementierung des Gleichheitsoperators verwenden. Auf diese Weise wird einen Stapelüberlauf verursachen. Um den Gleichheitsoperator zu implementieren, verwenden Sie die Object.Equals-Methode in Ihrer Implementierung. Weitere Informationen finden Sie im folgenden Beispiel.

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

## <a name="when-to-suppress-warnings"></a>Wann sollten Warnungen unterdrückt werden?
 Sie können ruhig auf eine Warnung dieser Regel zu unterdrücken, wenn die Standardimplementierung des Gleichheitsoperators das richtige Verhalten für den Typ enthält.

## <a name="example"></a>Beispiel
 Das folgende Beispiel definiert einen Typ (`BadAddableType`), die mit dieser Regel verletzt. Dieser Typ sollte den Gleichheitsoperator, damit zwei Instanzen, die die gleichen Feldwerte Testen haben implementieren `true` Gleichheit. Der Typ `GoodAddableType` zeigt die korrigierte Implementierung. Beachten Sie, dass dieser Typ auch den Ungleichheitsoperator implementiert und überschreibt <xref:System.Object.Equals%2A> andere Regeln nicht erfüllen. Eine vollständige Implementierung würde auch implementieren <xref:System.Object.GetHashCode%2A>.

 [!code-csharp[FxCop.Design.AddAndSubtract#1](../code-quality/codesnippet/CSharp/ca1013-overload-operator-equals-on-overloading-add-and-subtract_1.cs)]

## <a name="example"></a>Beispiel
 Das folgende Beispiel testet auf Gleichheit mit Instanzen von Typen, die zuvor in diesem Thema veranschaulichen die Standard- und das richtige Verhalten für den Gleichheitsoperator definiert wurden.

 [!code-csharp[FxCop.Design.TestAddAndSubtract#1](../code-quality/codesnippet/CSharp/ca1013-overload-operator-equals-on-overloading-add-and-subtract_2.cs)]

 Folgende Ergebnisse werden zurückgegeben:

 **Ungültiger Typ: {2,2} {2,2} sind gleich? Nicht**
**gute Typ: {3,3} {3,3} sind gleich? Ja**
**gute Typ: {3,3} {3,3} == werden?   Ja**
**Ungültiger Typ: {2,2} {9,9} sind gleich? Nicht**
**gute Typ: {3,3} {9,9} == werden?   Nein**
## <a name="see-also"></a>Siehe auch
 [Gleichheitsoperatoren](/dotnet/standard/design-guidelines/equality-operators)