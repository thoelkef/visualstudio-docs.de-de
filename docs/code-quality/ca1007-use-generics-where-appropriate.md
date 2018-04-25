---
title: 'CA1007: Nach Möglichkeit Generika verwenden'
ms.date: 11/04/2016
ms.technology: vs-ide-code-analysis
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
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 4aa1bb976cdbcc3d3b97e463ce0076bccdd26ba6
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/19/2018
---
# <a name="ca1007-use-generics-where-appropriate"></a>CA1007: Nach Möglichkeit Generika verwenden
|||
|-|-|
|TypeName|UseGenericsWhereAppropriate|
|CheckId|CA1007|
|Kategorie|Microsoft.Design|
|Unterbrechende Änderung|Breaking|

## <a name="cause"></a>Ursache
 Eine extern sichtbare Methode enthält einen Verweisparameter vom Typ <xref:System.Object?displayProperty=fullName>, und die enthaltende Assembly Ziele [!INCLUDE[dnprdnlong](../code-quality/includes/dnprdnlong_md.md)].

## <a name="rule-description"></a>Regelbeschreibung
 Ein Verweisparameter ist ein Parameter, die mit geändert werden die `ref` (`ByRef` in [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)]) Schlüsselwort. Der Argumenttyp, der für einen Verweisparameter übergeben wird muss genau mit dem Typ des Verweisparameters entsprechen. Um einen Typ verwenden, der von dem Typ des Verweisparameters abgeleitet ist, muss der Typ zuerst umgewandelt und eine Variable vom Typ Verweisparameters zugewiesen werden. Verwenden einer generischen Methode kann alle Typen mit gewissen Einschränkungen an die Methode übergeben werden, ohne die zuvor in den Typ dem Typ des Verweisparameters umgewandelt.

## <a name="how-to-fix-violations"></a>Behandeln von Verstößen
 Um einen Verstoß gegen diese Regel zu beheben, die Sie eine generische Methode, und Ersetzen Sie die <xref:System.Object> Parameter mit einem Typparameter.

## <a name="when-to-suppress-warnings"></a>Wann sollten Warnungen unterdrückt werden?
 Unterdrücken Sie keine Warnung dieser Regel.

## <a name="example"></a>Beispiel
 Das folgende Beispiel zeigt eine allgemeine Swap-Routine, die als nicht generische und generische Methoden implementiert wird. Beachten Sie, wie effizient die Zeichenfolgen mit der generischen Methode, die im Vergleich zu nicht generischen Methode ausgetauscht werden.

 [!code-vb[FxCop.Design.UseGenerics#1](../code-quality/codesnippet/VisualBasic/ca1007-use-generics-where-appropriate_1.vb)]
 [!code-csharp[FxCop.Design.UseGenerics#1](../code-quality/codesnippet/CSharp/ca1007-use-generics-where-appropriate_1.cs)]

## <a name="related-rules"></a>Verwandte Regeln
 [CA1005: Übermäßige Anzahl von Parametern in generischen Typen vermeiden](../code-quality/ca1005-avoid-excessive-parameters-on-generic-types.md)

 [CA1010: Auflistungen müssen eine generische Schnittstelle implementieren](../code-quality/ca1010-collections-should-implement-generic-interface.md)

 [CA1000: Statische Member nicht in generischen Typen deklarieren](../code-quality/ca1000-do-not-declare-static-members-on-generic-types.md)

 [CA1002: Generische Listen nicht verfügbar machen](../code-quality/ca1002-do-not-expose-generic-lists.md)

 [CA1006: Generische Typen in Membersignaturen nicht schachteln](../code-quality/ca1006-do-not-nest-generic-types-in-member-signatures.md)

 [CA1004: Generische Methoden müssen den Typparameter angeben](../code-quality/ca1004-generic-methods-should-provide-type-parameter.md)

 [CA1003: Generische Ereignishandlerinstanzen verwenden](../code-quality/ca1003-use-generic-event-handler-instances.md)

## <a name="see-also"></a>Siehe auch
 [Generika](/dotnet/csharp/programming-guide/generics/index)