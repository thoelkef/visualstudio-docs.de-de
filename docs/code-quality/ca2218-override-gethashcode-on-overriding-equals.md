---
title: 'CA2218: GetHashCode beim Überschreiben von Equals überschreiben.'
ms.date: 11/04/2016
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
ms.openlocfilehash: 8699e3434dc9c4cf9d3eccc37916c20ff7f34015
ms.sourcegitcommit: 0c2523d975d48926dd2b35bcd2d32a8ae14c06d8
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/24/2019
ms.locfileid: "71231190"
---
# <a name="ca2218-override-gethashcode-on-overriding-equals"></a>CA2218: GetHashCode beim Überschreiben von Equals überschreiben.

|||
|-|-|
|TypeName|OverrideGetHashCodeOnOverridingEquals|
|CheckId|CA2218|
|Kategorie|Microsoft.Usage|
|Unterbrechende Änderung|Nicht unterbrechend|

## <a name="cause"></a>Ursache
Ein öffentlicher Typ überschreibt <xref:System.Object.Equals%2A?displayProperty=fullName> , aber nicht außer <xref:System.Object.GetHashCode%2A?displayProperty=fullName>Kraft.

## <a name="rule-description"></a>Regelbeschreibung
 <xref:System.Object.GetHashCode%2A>gibt basierend auf der aktuellen Instanz einen-Wert zurück, der sich für Hash Algorithmen und Datenstrukturen eignet, z. b. eine Hash Tabelle. Zwei Objekte, die denselben Typ und gleich sind, müssen denselben Hashcode zurückgeben, um sicherzustellen, dass Instanzen der folgenden Typen ordnungsgemäß funktionieren:

- <xref:System.Collections.Hashtable?displayProperty=fullName>

- <xref:System.Collections.SortedList?displayProperty=fullName>

- <xref:System.Collections.Generic.Dictionary%602?displayProperty=fullName>

- <xref:System.Collections.Generic.SortedDictionary%602?displayProperty=fullName>

- <xref:System.Collections.Generic.SortedList%602?displayProperty=fullName>

- <xref:System.Collections.Specialized.HybridDictionary?displayProperty=fullName>

- <xref:System.Collections.Specialized.ListDictionary?displayProperty=fullName>

- <xref:System.Collections.Specialized.OrderedDictionary?displayProperty=fullName>

- Typen, die implementieren<xref:System.Collections.Generic.IEqualityComparer%601?displayProperty=fullName>

## <a name="how-to-fix-violations"></a>Behandeln von Verstößen
Um einen Verstoß gegen diese Regel zu beheben, stellen Sie eine <xref:System.Object.GetHashCode%2A>Implementierung von bereit. Bei einem Paar von Objekten desselben Typs müssen Sie sicherstellen, dass die Implementierung denselben Wert zurückgibt, wenn die Implementierung von <xref:System.Object.Equals%2A> für `true` das Paar zurückgibt.

## <a name="when-to-suppress-warnings"></a>Wann sollten Warnungen unterdrückt werden?
Unterdrücken Sie keine Warnung dieser Regel.

## <a name="class-example"></a>Klassen Beispiel

### <a name="description"></a>Beschreibung
Das folgende Beispiel zeigt eine Klasse (Verweistyp), die gegen diese Regel verstößt.

### <a name="code"></a>Code
[!code-csharp[FxCop.Usage.GetHashCodeErrorClass#1](../code-quality/codesnippet/CSharp/ca2218-override-gethashcode-on-overriding-equals_1.cs)]

### <a name="comments"></a>Kommentare
Im folgenden Beispiel wird die Verletzung durch über <xref:System.Object.GetHashCode>schreiben behoben.

### <a name="code"></a>Code
[!code-csharp[FxCop.Usage.GetHashCodeFixedClass#1](../code-quality/codesnippet/CSharp/ca2218-override-gethashcode-on-overriding-equals_2.cs)]

## <a name="structure-example"></a>Struktur Beispiel

### <a name="description"></a>Beschreibung
Das folgende Beispiel zeigt eine Struktur (Werttyp), die gegen diese Regel verstößt.

### <a name="code"></a>Code
[!code-csharp[FxCop.Usage.GetHashCodeErrorStruct#1](../code-quality/codesnippet/CSharp/ca2218-override-gethashcode-on-overriding-equals_3.cs)]

### <a name="comments"></a>Kommentare
Im folgenden Beispiel wird die Verletzung durch über <xref:System.Object.GetHashCode>schreiben behoben.

### <a name="code"></a>Code
[!code-csharp[FxCop.Usage.GetHashCodeFixedStruct#1](../code-quality/codesnippet/CSharp/ca2218-override-gethashcode-on-overriding-equals_4.cs)]

## <a name="related-rules"></a>Verwandte Regeln
[CA1046: Gleichheits Operator für Referenztypen nicht überladen](../code-quality/ca1046-do-not-overload-operator-equals-on-reference-types.md)

[CA2225: Operator Überladungen weisen benannte Alternativen auf](../code-quality/ca2225-operator-overloads-have-named-alternates.md)

[CA2226: Operatoren sollten symmetrische über Ladungen aufweisen](../code-quality/ca2226-operators-should-have-symmetrical-overloads.md)

[CA2224: Überschreiben von Gleichheits beim Überladen von Operatoren](../code-quality/ca2224-override-equals-on-overloading-operator-equals.md)

[CA2231: Überladen Sie den Gleichheitsoperator beim Überschreiben von ValueType.Equals](../code-quality/ca2231-overload-operator-equals-on-overriding-valuetype-equals.md)

## <a name="see-also"></a>Siehe auch

- <xref:System.Object.Equals%2A?displayProperty=fullName>
- <xref:System.Object.GetHashCode%2A?displayProperty=fullName>
- <xref:System.Collections.Hashtable?displayProperty=fullName>
- [Gleichheitsoperatoren](/dotnet/standard/design-guidelines/equality-operators)