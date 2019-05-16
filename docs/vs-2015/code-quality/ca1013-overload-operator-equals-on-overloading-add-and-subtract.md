---
title: 'CA1013: Gleichheitsoperator beim Überladen von Addition und Subtraktion | Microsoft-Dokumentation'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
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
caps.latest.revision: 24
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 1b70085c83d842ccb5f8addc661af9109b5a5976
ms.sourcegitcommit: 08fc78516f1107b83f46e2401888df4868bb1e40
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/15/2019
ms.locfileid: "65695621"
---
# <a name="ca1013-overload-operator-equals-on-overloading-add-and-subtract"></a>CA1013: Gleichheitsoperator beim Überladen von Addition und Subtraktion überladen.
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

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

## <a name="when-to-suppress-warnings"></a>Wann sollten Warnungen unterdrückt werden?
 Es ist sicher, um eine Warnung dieser Regel zu unterdrücken, wenn es sich bei der Standardimplementierung des Gleichheitsoperators das richtige Verhalten für den Typ bereitstellt.

## <a name="example"></a>Beispiel
 Das folgende Beispiel definiert einen Typ (`BadAddableType`), die gegen diese Regel verstößt. Dieser Typ sollte den Gleichheitsoperator, damit zwei Instanzen, die die Feldwerten testen implementieren `true` hinsichtlich ihrer Gleichheit. Der Typ `GoodAddableType` zeigt die korrigierte Implementierung. Beachten Sie, dass dieser Typ wird auch den Inequality-Operator implementiert und überschreibt <xref:System.Object.Equals%2A> zu anderen Regeln erfüllen. Eine vollständige Implementierung würde auch implementieren <xref:System.Object.GetHashCode%2A>.

 [!code-csharp[FxCop.Design.AddAndSubtract#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.AddAndSubtract/cs/FxCop.Design.AddAndSubtract.cs#1)]

## <a name="example"></a>Beispiel
 Im folgende Beispiel testet auf Gleichheit mit Instanzen der Typen, die zuvor in diesem Thema erläutern Sie den standardmäßigen und das richtige Verhalten für den Equality-Operator definiert wurden.

 [!code-csharp[FxCop.Design.TestAddAndSubtract#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.TestAddAndSubtract/cs/FxCop.Design.TestAddAndSubtract.cs#1)]

 Folgende Ergebnisse werden zurückgegeben:

 **Ungültiger Typ: {2,2} {2,2} gleich sind? Keine**
**gute Typ: {3,3} {3,3} gleich sind? Ja**
**gute Typ: {3,3} {3,3} == werden?   Ja**
**Ungültiger Typ: {2,2} {9,9} gleich sind? Keine**
**gute Typ: {3,3} {9,9} == werden?   Nein**
## <a name="see-also"></a>Siehe auch
 [Gleichheitsoperatoren](https://msdn.microsoft.com/library/bc496a91-fefb-4ce0-ab4c-61f09964119a)
