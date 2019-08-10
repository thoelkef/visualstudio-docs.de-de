---
title: 'CA1007: Nach Möglichkeit Generics verwenden.'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- CA1007
- UseGenericsWhereAppropriate
helpviewer_keywords:
- CA1007
- UseGenericsWhereAppropriate
ms.assetid: eab780ea-3b1f-4d32-b15a-5d48da2df46b
author: gewarren
ms.author: gewarren
manager: jillfra
dev_langs:
- CSharp
- VB
ms.workload:
- multiple
ms.openlocfilehash: ffb18316b5f009a0f2854c8a158e528f15c92326
ms.sourcegitcommit: 5216c15e9f24d1d5db9ebe204ee0e7ad08705347
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/09/2019
ms.locfileid: "68923208"
---
# <a name="ca1007-use-generics-where-appropriate"></a>CA1007: Nach Möglichkeit Generics verwenden.

|||
|-|-|
|TypeName|UseGenericsWhereAppropriate|
|CheckId|CA1007|
|Kategorie|Microsoft.Design|
|Unterbrechende Änderung|Breaking|

## <a name="cause"></a>Ursache
Eine extern sichtbare Methode enthält einen Verweis Parameter vom Typ <xref:System.Object?displayProperty=fullName>, und die enthaltende Assembly zielt .NET Framework 2,0 ab.

## <a name="rule-description"></a>Regelbeschreibung
Ein Verweis Parameter ist ein Parameter, der mit dem `ref` Schlüsselwort (`ByRef` in [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)]) geändert wird. Der Argumenttyp, der für einen Verweis Parameter bereitgestellt wird, muss exakt mit dem Verweis Parametertyp übereinstimmen. Um einen Typ zu verwenden, der vom Verweis Parametertyp abgeleitet ist, muss der Typ zuerst umgewandelt und einer Variablen des Verweis Parameter Typs zugewiesen werden. Die Verwendung einer generischen Methode ermöglicht, dass alle Typen, die Einschränkungen unterliegen, an die Methode übergeben werden, ohne dass der Typ zuerst in den Verweis Parametertyp umgewandelt wird.

## <a name="how-to-fix-violations"></a>Behandeln von Verstößen
Um einen Verstoß gegen diese Regel zu beheben, legen Sie die-Methode als <xref:System.Object> generisch fest, und ersetzen Sie den-Parameter mithilfe eines Typparameters.

## <a name="when-to-suppress-warnings"></a>Wann sollten Warnungen unterdrückt werden?
Unterdrücken Sie keine Warnung dieser Regel.

## <a name="example"></a>Beispiel
Das folgende Beispiel zeigt eine allgemeine Austausch Routine, die sowohl als nicht generische als auch als generische Methoden implementiert ist. Beachten Sie, wie effizient die Zeichen folgen mithilfe der generischen-Methode im Vergleich zur nicht generischen-Methode ausgetauscht werden.

[!code-vb[FxCop.Design.UseGenerics#1](../code-quality/codesnippet/VisualBasic/ca1007-use-generics-where-appropriate_1.vb)]
[!code-csharp[FxCop.Design.UseGenerics#1](../code-quality/codesnippet/CSharp/ca1007-use-generics-where-appropriate_1.cs)]

## <a name="related-rules"></a>Verwandte Regeln
[CA1005: Übermäßige Parameter für generische Typen vermeiden](../code-quality/ca1005-avoid-excessive-parameters-on-generic-types.md)

[CA1010: Sammlungen sollten eine generische Schnittstelle implementieren.](../code-quality/ca1010-collections-should-implement-generic-interface.md)

[CA1000: Statische Member nicht in generischen Typen deklarieren](../code-quality/ca1000-do-not-declare-static-members-on-generic-types.md)

[CA1002: Generische Listen nicht verfügbar machen](../code-quality/ca1002-do-not-expose-generic-lists.md)

[CA1006: Generische Typen in Element Signaturen nicht Schachteln](../code-quality/ca1006-do-not-nest-generic-types-in-member-signatures.md)

[CA1004: Generische Methoden sollten Typparameter bereitstellen.](../code-quality/ca1004-generic-methods-should-provide-type-parameter.md)

[CA1003: Generische Ereignishandlerinstanzen verwenden](../code-quality/ca1003-use-generic-event-handler-instances.md)

## <a name="see-also"></a>Siehe auch
[Generika](/dotnet/csharp/programming-guide/generics/index)