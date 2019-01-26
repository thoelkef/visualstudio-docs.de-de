---
title: 'CA2218: GetHashCode beim Überschreiben von Equals überschreiben.'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.topic: reference
f1_keywords:
- CA2218
- OverrideGetHashCodeOnOverridingEquals
helpviewer_keywords:
- OverrideGetHashCodeOnOverridingEquals
- CA2218
ms.assetid: 69b020cd-29e8-45a6-952e-32cf3ce2e21d
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 750a574eec5beedadce387109a5bd941d4e0e413
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/25/2019
ms.locfileid: "54971575"
---
# <a name="ca2218-override-gethashcode-on-overriding-equals"></a>CA2218: GetHashCode beim Überschreiben von Equals überschreiben.

|||
|-|-|
|TypeName|OverrideGetHashCodeOnOverridingEquals|
|CheckId|CA2218|
|Kategorie|Microsoft.Usage|
|Unterbrechende Änderung|Nicht unterbrechende Änderung|

## <a name="cause"></a>Ursache
 Ein öffentlicher Typ überschreibt <xref:System.Object.Equals%2A?displayProperty=fullName> , nicht jedoch <xref:System.Object.GetHashCode%2A?displayProperty=fullName>.

## <a name="rule-description"></a>Regelbeschreibung
 <xref:System.Object.GetHashCode%2A> Gibt einen Wert, der basierend auf der aktuellen Instanz, die für die Verwendung in Hashalgorithmen und Datenstrukturen wie Hashtabellen geeignet ist. Zwei Objekte, die den gleichen Typ aufweisen und gleich sind, müssen den gleichen Hashcode, um sicherzustellen, dass die Instanzen der folgenden Typen ordnungsgemäß zurückgeben:

- <xref:System.Collections.Hashtable?displayProperty=fullName>

- <xref:System.Collections.SortedList?displayProperty=fullName>

- <xref:System.Collections.Generic.Dictionary%602?displayProperty=fullName>

- <xref:System.Collections.Generic.SortedDictionary%602?displayProperty=fullName>

- <xref:System.Collections.Generic.SortedList%602?displayProperty=fullName>

- <xref:System.Collections.Specialized.HybridDictionary?displayProperty=fullName>

- <xref:System.Collections.Specialized.ListDictionary?displayProperty=fullName>

- <xref:System.Collections.Specialized.OrderedDictionary?displayProperty=fullName>

- Typen, die implementieren <xref:System.Collections.Generic.IEqualityComparer%601?displayProperty=fullName>

## <a name="how-to-fix-violations"></a>Behandeln von Verstößen
 Um einen Verstoß gegen diese Regel zu beheben, stellen Sie eine Implementierung der <xref:System.Object.GetHashCode%2A>. Für ein Paar von Objekten desselben Typs, müssen Sie sicherstellen, dass es sich bei der Implementierung den gleichen Wert zurückgegeben, wenn die Implementierung von <xref:System.Object.Equals%2A> gibt `true` für das Paar.

## <a name="when-to-suppress-warnings"></a>Wenn Sie Warnungen unterdrücken
 Unterdrücken Sie keine Warnung dieser Regel.

## <a name="class-example"></a>Beispiel:

### <a name="description"></a>Beschreibung
 Das folgende Beispiel zeigt eine Klasse (Referenztyp), die gegen diese Regel verstößt.

### <a name="code"></a>Code
 [!code-csharp[FxCop.Usage.GetHashCodeErrorClass#1](../code-quality/codesnippet/CSharp/ca2218-override-gethashcode-on-overriding-equals_1.cs)]

### <a name="comments"></a>Kommentare
 Im folgenden Beispiel wird der Verstoß durch Überschreiben korrigiert <xref:System.Object.GetHashCode>.

### <a name="code"></a>Code
 [!code-csharp[FxCop.Usage.GetHashCodeFixedClass#1](../code-quality/codesnippet/CSharp/ca2218-override-gethashcode-on-overriding-equals_2.cs)]

## <a name="structure-example"></a>Struktur-Beispiel

### <a name="description"></a>Beschreibung
 Das folgende Beispiel zeigt eine Struktur (Werttyp), die gegen diese Regel verstößt.

### <a name="code"></a>Code
 [!code-csharp[FxCop.Usage.GetHashCodeErrorStruct#1](../code-quality/codesnippet/CSharp/ca2218-override-gethashcode-on-overriding-equals_3.cs)]

### <a name="comments"></a>Kommentare
 Im folgenden Beispiel wird der Verstoß durch Überschreiben korrigiert <xref:System.Object.GetHashCode>.

### <a name="code"></a>Code
 [!code-csharp[FxCop.Usage.GetHashCodeFixedStruct#1](../code-quality/codesnippet/CSharp/ca2218-override-gethashcode-on-overriding-equals_4.cs)]

## <a name="related-rules"></a>Verwandte Regeln
 [CA1046: Gleichheitsoperator für Referenztypen nicht überladen](../code-quality/ca1046-do-not-overload-operator-equals-on-reference-types.md)

 [CA2225: Operatorüberladungen weisen benannte alternativen auf](../code-quality/ca2225-operator-overloads-have-named-alternates.md)

 [CA2226: Operatoren sollten symmetrische Überladungen aufweisen.](../code-quality/ca2226-operators-should-have-symmetrical-overloads.md)

 [CA2224: Außerkraftsetzung equals, Equals beim Überladen](../code-quality/ca2224-override-equals-on-overloading-operator-equals.md)

 [CA2231: Überladen Sie den Gleichheitsoperator beim Überschreiben von ValueType.Equals](../code-quality/ca2231-overload-operator-equals-on-overriding-valuetype-equals.md)

## <a name="see-also"></a>Siehe auch

- <xref:System.Object.Equals%2A?displayProperty=fullName>
- <xref:System.Object.GetHashCode%2A?displayProperty=fullName>
- <xref:System.Collections.Hashtable?displayProperty=fullName>
- [Gleichheitsoperatoren](/dotnet/standard/design-guidelines/equality-operators)