---
title: 'CA1013: Überladen des Gleichheits Operators beim Überladen von Add und subtrahieren | Microsoft-Dokumentation'
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
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: dd1c144f04150e3965e2c0264b80147cbd9b8f19
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/19/2019
ms.locfileid: "72663210"
---
# <a name="ca1013-overload-operator-equals-on-overloading-add-and-subtract"></a>CA1013: Gleichheitsoperator beim Überladen von Addition und Subtraktion überladen
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|OverloadOperatorEqualsOnOverloadingAddAndSubtract|
|CheckId|CA1013|
|Kategorie|Microsoft. Design|
|Unterbrechende Änderung|Nicht unterbrechend|

## <a name="cause"></a>Ursache
 Ein öffentlicher oder geschützter Typ implementiert den Additions- oder Subtraktionsoperator, ohne den Gleichheitsoperator zu implementieren.

## <a name="rule-description"></a>Regelbeschreibung
 Wenn Instanzen eines Typs mithilfe von Vorgängen wie Addition und Subtraktion kombiniert werden können, sollten Sie fast immer Gleichheit definieren, um `true` für zwei Instanzen zurückzugeben, die dieselben Werte aufweisen.

 Der Standard Gleichheits Operator kann nicht in einer überladenen Implementierung des Gleichheits Operators verwendet werden. Dies führt zu einem Stapelüberlauf. Um den Gleichheits Operator zu implementieren, verwenden Sie die Object. gleich-Methode in der Implementierung. Weitere Informationen finden Sie im folgenden Beispiel.

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
 Um einen Verstoß gegen diese Regel zu beheben, implementieren Sie den Gleichheits Operator, sodass er mathematisch mit den Additions-und Subtraktions Operatoren übereinstimmt.

## <a name="when-to-suppress-warnings"></a>Wann sollten Warnungen unterdrückt werden?
 Es ist sicher, eine Warnung aus dieser Regel zu unterdrücken, wenn die Standard Implementierung des Gleichheits Operators das richtige Verhalten für den Typ bereitstellt.

## <a name="example"></a>Beispiel
 Im folgenden Beispiel wird ein Typ (`BadAddableType`) definiert, der gegen diese Regel verstößt. Dieser Typ sollte den Gleichheits Operator implementieren, damit zwei Instanzen, für die der gleiche Feldwert getestet wurde, auf Gleichheit `true` werden. Der Typ `GoodAddableType` der die korrigierte Implementierung anzeigt. Beachten Sie, dass dieser Typ auch den Ungleichheits Operator implementiert und <xref:System.Object.Equals%2A>, um andere Regeln zu erfüllen. Eine komplette Implementierung würde auch <xref:System.Object.GetHashCode%2A> implementieren.

 [!code-csharp[FxCop.Design.AddAndSubtract#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.AddAndSubtract/cs/FxCop.Design.AddAndSubtract.cs#1)]

## <a name="example"></a>Beispiel
 Im folgenden Beispiel wird auf Gleichheit getestet, indem Instanzen der Typen verwendet werden, die zuvor in diesem Thema definiert wurden, um das standardmäßige und korrekte Verhalten für den Gleichheits Operator zu veranschaulichen.

 [!code-csharp[FxCop.Design.TestAddAndSubtract#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.TestAddAndSubtract/cs/FxCop.Design.TestAddAndSubtract.cs#1)]

 Folgende Ergebnisse werden zurückgegeben:

 **Ungültiger Typ: {2,2} {2,2} gleich? Kein** 
**guter Typ: {3,3} {3,3} sind gleich? Ja** 
**guter Typ: {3,3} 0 sind = =?   Ja** 1**Ungültiger Typ: 3 4 sind gleich? Kein** 5**guter Typ: 7 8 sind = =?   Nein**
## <a name="see-also"></a>Siehe auch
 [Gleichheitsoperatoren](https://msdn.microsoft.com/library/bc496a91-fefb-4ce0-ab4c-61f09964119a)
