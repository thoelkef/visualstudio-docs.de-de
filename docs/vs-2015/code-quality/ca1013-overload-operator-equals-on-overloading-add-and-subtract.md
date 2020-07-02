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
ms.openlocfilehash: 2304b78073b806dfc4aec9686f061d946b379ded
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/30/2020
ms.locfileid: "85545417"
---
# <a name="ca1013-overload-operator-equals-on-overloading-add-and-subtract"></a>CA1013: Gleichheitsoperator beim Überladen von Addition und Subtraktion überladen.
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|Element|Wert|
|-|-|
|TypName|OverloadOperatorEqualsOnOverloadingAddAndSubtract|
|CheckId|CA1013|
|Kategorie|Microsoft. Design|
|Unterbrechende Änderung|Nicht unterbrechend|

## <a name="cause"></a>Ursache
 Ein öffentlicher oder geschützter Typ implementiert den Additions- oder Subtraktionsoperator, ohne den Gleichheitsoperator zu implementieren.

## <a name="rule-description"></a>Beschreibung der Regel
 Wenn Instanzen eines Typs mithilfe von Vorgängen wie Addition und Subtraktion kombiniert werden können, sollten Sie fast immer Gleichheit definieren, um `true` für zwei Instanzen zurückzugeben, die dieselben Werte aufweisen.

 Der Standard Gleichheits Operator kann nicht in einer überladenen Implementierung des Gleichheits Operators verwendet werden. Dies führt zu einem Stapelüberlauf. Um den Gleichheits Operator zu implementieren, verwenden Sie die Object. gleich-Methode in der Implementierung. Siehe folgendes Beispiel.

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
 Im folgenden Beispiel wird ein Typ ( `BadAddableType` ) definiert, der gegen diese Regel verstößt. Dieser Typ sollte den Gleichheits Operator implementieren, damit zwei Instanzen, die dieselben Feldwerte aufweisen, `true` auf Gleichheit überprüft werden. Der Typ `GoodAddableType` zeigt die korrigierte Implementierung. Beachten Sie, dass dieser Typ auch den Ungleichheits Operator und über schreibungen implementiert <xref:System.Object.Equals%2A> , um andere Regeln zu erfüllen. Eine komplette Implementierung würde ebenfalls implementieren <xref:System.Object.GetHashCode%2A> .

 [!code-csharp[FxCop.Design.AddAndSubtract#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.AddAndSubtract/cs/FxCop.Design.AddAndSubtract.cs#1)]

## <a name="example"></a>Beispiel
 Im folgenden Beispiel wird auf Gleichheit getestet, indem Instanzen der Typen verwendet werden, die zuvor in diesem Thema definiert wurden, um das standardmäßige und korrekte Verhalten für den Gleichheits Operator zu veranschaulichen.

 [!code-csharp[FxCop.Design.TestAddAndSubtract#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.TestAddAndSubtract/cs/FxCop.Design.TestAddAndSubtract.cs#1)]

 Folgende Ergebnisse werden zurückgegeben:

 Ungültiger **Typ: {2,2} {2,2} sind gleich? Kein** 
 **guter Typ: {3,3} {3,3} sind gleich? Ja**, 
 **guter Typ: {3,3} {3,3} sind = =?   Ja**, 
 ** {2,2} {9,9} Ungültiger Typ: sind gleich? Kein** 
 **guter Typ: {3,3} {9,9} sind = =?   Nein**
## <a name="see-also"></a>Weitere Informationen
 [Gleichheits Operatoren](https://msdn.microsoft.com/library/bc496a91-fefb-4ce0-ab4c-61f09964119a)
