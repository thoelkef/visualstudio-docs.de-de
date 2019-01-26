---
title: 'CA1010: Sammlungen müssen eine generische Schnittstelle implementieren.'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.topic: reference
f1_keywords:
- CA1010
- CollectionsShouldImplementGenericInterface
helpviewer_keywords:
- CA1010
- CollectionsShouldImplementGenericInterface
ms.assetid: c7d7126f-fa70-40be-8f93-3243e1760dc5
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: af0d88b2d9a17595fdfcabb27ba90f601a836635
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/25/2019
ms.locfileid: "54935618"
---
# <a name="ca1010-collections-should-implement-generic-interface"></a>CA1010: Sammlungen müssen eine generische Schnittstelle implementieren.

|||
|-|-|
|TypeName|CollectionsShouldImplementGenericInterface|
|CheckId|CA1010|
|Kategorie|Microsoft.Design|
|Unterbrechende Änderung|Nicht unterbrechend|

## <a name="cause"></a>Ursache
 Ein extern sichtbarer Typ implementiert die <xref:System.Collections.IEnumerable?displayProperty=fullName> Schnittstelle implementiert aber nicht die <xref:System.Collections.Generic.IEnumerable%601?displayProperty=fullName> Schnittstelle und die Ziele der enthaltenden Assembly [!INCLUDE[dnprdnlong](../code-quality/includes/dnprdnlong_md.md)]. Mit dieser Regel werden ignoriert, Typen, die implementieren <xref:System.Collections.IDictionary?displayProperty=fullName>.

## <a name="rule-description"></a>Regelbeschreibung
 Um die Verwendbarkeit einer Auflistung zu erweitern, implementieren Sie eine der generischen Auflistungsschnittstellen. Klicken Sie dann kann die Auflistung verwendet werden, zum Auffüllen generischer Auflistungstypen, z. B. Folgendes:

- <xref:System.Collections.Generic.List%601?displayProperty=fullName>

- <xref:System.Collections.Generic.Queue%601?displayProperty=fullName>

- <xref:System.Collections.Generic.Stack%601?displayProperty=fullName>

## <a name="how-to-fix-violations"></a>Behandeln von Verstößen
 Um einen Verstoß gegen diese Regel zu beheben, implementieren Sie eine der folgenden generischen Auflistungsschnittstellen:

- <xref:System.Collections.Generic.IEnumerable%601?displayProperty=fullName>

- <xref:System.Collections.Generic.ICollection%601?displayProperty=fullName>

- <xref:System.Collections.Generic.IList%601?displayProperty=fullName>

## <a name="when-to-suppress-warnings"></a>Wenn Sie Warnungen unterdrücken
 Es ist sicher ist, unterdrücken Sie eine Warnung dieser Regel. jedoch müssen die Auflistung eine eingeschränktere verwenden.

## <a name="example-violation"></a>Beispiel für einen Verstoß

### <a name="description"></a>Beschreibung
 Das folgende Beispiel zeigt eine Klasse (Referenztyp), die abgeleitet, die nicht generische `CollectionBase` -Klasse, die gegen diese Regel verstößt.

### <a name="code"></a>Code
 [!code-csharp[FxCop.Design.CollectionsGenericViolation#1](../code-quality/codesnippet/CSharp/ca1010-collections-should-implement-generic-interface_1.cs)]

### <a name="comments"></a>Kommentare
 Um einen Verstoß gegen diese Regel zu beheben, sollten Sie entweder die generische Schnittstellen implementieren oder ändern Sie die Basisklasse in einen Typ, der bereits sowohl die generische und nicht generischen Schnittstellen, wie z. B. implementiert die `Collection<T>` Klasse.

## <a name="fix-by-base-class-change"></a>Beheben Sie, indem die Änderung der Basisklasse

### <a name="description"></a>Beschreibung
 Im folgende Beispiel wird der Verstoß korrigiert, ändern Sie die Basisklasse der Auflistung aus der nicht generischen `CollectionBase` Klasse, um die generische `Collection<T>` (`Collection(Of T)` in [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)]) Klasse.

### <a name="code"></a>Code
 [!code-csharp[FxCop.Design.CollectionsGenericBase#1](../code-quality/codesnippet/CSharp/ca1010-collections-should-implement-generic-interface_2.cs)]

### <a name="comments"></a>Kommentare
 Ändern die Basisklasse einer Klasse bereits veröffentlichten gilt eine wichtige Änderung für vorhandene Benutzer.

## <a name="fix-by-interface-implementation"></a>Beheben Sie die schnittstellenimplementierung

### <a name="description"></a>Beschreibung
 Im folgende Beispiel wird der Verstoß korrigiert, durch diese generischen Schnittstellen implementieren: `IEnumerable<T>`, `ICollection<T>`, und `IList<T>` (`IEnumerable(Of T)`, `ICollection(Of T)`, und `IList(Of T)` in [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)]).

### <a name="code"></a>Code
 [!code-csharp[FxCop.Design.CollectionsGenericInterface#1](../code-quality/codesnippet/CSharp/ca1010-collections-should-implement-generic-interface_3.cs)]

## <a name="related-rules"></a>Verwandte Regeln
 [CA1005: Übermäßige Anzahl von Parametern in generischen Typen vermeiden](../code-quality/ca1005-avoid-excessive-parameters-on-generic-types.md)

 [CA1000: Statische Member in generischen Typen nicht deklarieren](../code-quality/ca1000-do-not-declare-static-members-on-generic-types.md)

 [CA1002: Generische Listen nicht verfügbar machen](../code-quality/ca1002-do-not-expose-generic-lists.md)

 [CA1006: Generische Typen in Membersignaturen nicht schachteln](../code-quality/ca1006-do-not-nest-generic-types-in-member-signatures.md)

 [CA1004: Generische Methoden müssen den Typparameter angeben.](../code-quality/ca1004-generic-methods-should-provide-type-parameter.md)

 [CA1003: Generische Ereignishandlerinstanzen verwenden](../code-quality/ca1003-use-generic-event-handler-instances.md)

 [CA1007: Verwenden Sie Generika](../code-quality/ca1007-use-generics-where-appropriate.md)

## <a name="see-also"></a>Siehe auch
 [Generika](/dotnet/csharp/programming-guide/generics/index)