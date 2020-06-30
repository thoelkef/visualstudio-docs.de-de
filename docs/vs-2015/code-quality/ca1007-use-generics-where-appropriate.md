---
title: 'CA1007: Generika ggf. verwenden | Microsoft-Dokumentation'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA1007
- UseGenericsWhereAppropriate
helpviewer_keywords:
- CA1007
- UseGenericsWhereAppropriate
ms.assetid: eab780ea-3b1f-4d32-b15a-5d48da2df46b
caps.latest.revision: 21
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 4ee33305c1ae0f15e5d8f390a4b65d62c87b6904
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/30/2020
ms.locfileid: "85547939"
---
# <a name="ca1007-use-generics-where-appropriate"></a>CA1007: Nach Möglichkeit Generics verwenden.
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|Element|Wert|
|-|-|
|TypName|UseGenericsWhereAppropriate|
|CheckId|CA1007|
|Category|Microsoft. Design|
|Unterbrechende Änderung|Breaking|

## <a name="cause"></a>Ursache
 Eine extern sichtbare Methode enthält einen Verweis Parameter vom Typ <xref:System.Object?displayProperty=fullName> und die enthaltende Assembly-Ziele [!INCLUDE[dnprdnlong](../includes/dnprdnlong-md.md)] .

## <a name="rule-description"></a>Beschreibung der Regel
 Ein Verweis Parameter ist ein Parameter, der mit dem `ref` `ByRef` Schlüsselwort (in [!INCLUDE[vbprvb](../includes/vbprvb-md.md)] ) geändert wird. Der Argumenttyp, der für einen Verweis Parameter bereitgestellt wird, muss exakt mit dem Verweis Parametertyp übereinstimmen. Um einen Typ zu verwenden, der vom Verweis Parametertyp abgeleitet ist, muss der Typ zuerst umgewandelt und einer Variablen des Verweis Parameter Typs zugewiesen werden. Die Verwendung einer generischen Methode ermöglicht, dass alle Typen, die Einschränkungen unterliegen, an die Methode übergeben werden, ohne dass der Typ zuerst in den Verweis Parametertyp umgewandelt wird.

## <a name="how-to-fix-violations"></a>Behandeln von Verstößen
 Um einen Verstoß gegen diese Regel zu beheben, legen Sie die-Methode als generisch fest, und ersetzen Sie den- <xref:System.Object> Parameter mithilfe eines Typparameters.

## <a name="when-to-suppress-warnings"></a>Wann sollten Warnungen unterdrückt werden?
 Unterdrücken Sie keine Warnung dieser Regel.

## <a name="example"></a>Beispiel
 Das folgende Beispiel zeigt eine allgemeine Austausch Routine, die sowohl als nicht generische als auch als generische Methoden implementiert ist. Beachten Sie, wie effizient die Zeichen folgen mithilfe der generischen-Methode im Vergleich zur nicht generischen-Methode ausgetauscht werden.

 [!code-csharp[FxCop.Design.UseGenerics#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.UseGenerics/cs/FxCop.Design.UseGenerics.cs#1)]
 [!code-vb[FxCop.Design.UseGenerics#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Design.UseGenerics/vb/FxCop.Design.UseGenerics.vb#1)]

## <a name="related-rules"></a>Verwandte Regeln
 [CA1005: Übermäßige Anzahl von Parametern in generischen Typen vermeiden.](../code-quality/ca1005-avoid-excessive-parameters-on-generic-types.md)

 [CA1010: Sammlungen müssen eine generische Schnittstelle implementieren.](../code-quality/ca1010-collections-should-implement-generic-interface.md)

 [CA1000: Statische Member nicht in generischen Typen deklarieren.](../code-quality/ca1000-do-not-declare-static-members-on-generic-types.md)

 [CA1002: Generische Listen nicht verfügbar machen.](../code-quality/ca1002-do-not-expose-generic-lists.md)

 [CA1006: Generische Typen in Membersignaturen nicht schachteln.](../code-quality/ca1006-do-not-nest-generic-types-in-member-signatures.md)

 [CA1004: Generische Methoden müssen den Typparameter angeben.](../code-quality/ca1004-generic-methods-should-provide-type-parameter.md)

 [CA1003: Generische Ereignishandlerinstanzen verwenden.](../code-quality/ca1003-use-generic-event-handler-instances.md)

## <a name="see-also"></a>Weitere Informationen
 [Generics](https://msdn.microsoft.com/library/75ea8509-a4ea-4e7a-a2b3-cf72482e9282)
