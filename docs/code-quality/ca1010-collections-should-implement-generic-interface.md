---
title: 'CA1010: Sammlungen müssen eine generische Schnittstelle implementieren.'
ms.date: 03/11/2019
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
ms.openlocfilehash: 066b9d013847f5362ee0dd712002cf8578fb57a6
ms.sourcegitcommit: 0c2523d975d48926dd2b35bcd2d32a8ae14c06d8
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/24/2019
ms.locfileid: "71236443"
---
# <a name="ca1010-collections-should-implement-generic-interface"></a>CA1010: Sammlungen müssen eine generische Schnittstelle implementieren.

|||
|-|-|
|TypeName|CollectionsShouldImplementGenericInterface|
|CheckId|CA1010|
|Kategorie|Microsoft.Design|
|Unterbrechende Änderung|Nicht unterbrechend|

## <a name="cause"></a>Ursache

Ein Typ implementiert die <xref:System.Collections.IEnumerable?displayProperty=fullName> -Schnittstelle, implementiert aber <xref:System.Collections.Generic.IEnumerable%601?displayProperty=fullName> nicht die-Schnittstelle, und die enthaltende Assembly ist .net. Diese Regel ignoriert Typen, die <xref:System.Collections.IDictionary?displayProperty=fullName>implementieren.

Standardmäßig betrachtet diese Regel nur extern sichtbare Typen, aber dies ist [konfigurierbar](#configurability).

## <a name="rule-description"></a>Regelbeschreibung

Um die Verwendbarkeit einer Auflistung zu erweitern, implementieren Sie eine der generischen Auflistungsschnittstellen. Anschließend kann die Auflistung verwendet werden, um generische Auflistungs Typen wie die folgenden aufzufüllen:

- <xref:System.Collections.Generic.List%601?displayProperty=fullName>
- <xref:System.Collections.Generic.Queue%601?displayProperty=fullName>
- <xref:System.Collections.Generic.Stack%601?displayProperty=fullName>

## <a name="how-to-fix-violations"></a>Behandeln von Verstößen

Um einen Verstoß gegen diese Regel zu beheben, müssen Sie eine der folgenden generischen Auflistungs Schnittstellen implementieren:

- <xref:System.Collections.Generic.IEnumerable%601?displayProperty=fullName>
- <xref:System.Collections.Generic.ICollection%601?displayProperty=fullName>
- <xref:System.Collections.Generic.IList%601?displayProperty=fullName>

## <a name="when-to-suppress-warnings"></a>Wann sollten Warnungen unterdrückt werden?

Es ist sicher, eine Warnung aus dieser Regel zu unterdrücken. Allerdings ist die Verwendung der Sammlung eingeschränkter.

## <a name="configurability"></a>Konfigurierbarkeit

Wenn Sie diese Regel von [FxCop](install-fxcop-analyzers.md) Analyzer (und nicht mit der Legacy Analyse) ausführen, können Sie basierend auf ihrer Barrierefreiheit konfigurieren, für welche Teile Ihrer Codebasis diese Regel ausgeführt werden soll. Um z. b. anzugeben, dass die Regel nur für die nicht öffentliche API-Oberfläche ausgeführt werden soll, fügen Sie das folgende Schlüssel-Wert-Paar in eine Editor config-Datei in Ihrem Projekt ein:

```ini
dotnet_code_quality.ca1010.api_surface = private, internal
```

Sie können diese Option nur für diese Regel, für alle Regeln oder für alle Regeln in dieser Kategorie (Entwurf) konfigurieren. Weitere Informationen finden Sie unter [Konfigurieren von FxCop-Analysen](configure-fxcop-analyzers.md).

## <a name="example-violation"></a>Beispiel Verstoß

Im folgenden Beispiel wird eine Klasse (Verweistyp) gezeigt, die von der nicht generischen `CollectionBase` -Klasse abgeleitet wird, die gegen diese Regel verstößt.

[!code-csharp[FxCop.Design.CollectionsGenericViolation#1](../code-quality/codesnippet/CSharp/ca1010-collections-should-implement-generic-interface_1.cs)]

Führen Sie einen der folgenden Schritte aus, um einen Verstoß gegen diese Regel zu beheben:

- Implementieren Sie die generischen Schnittstellen.
- Ändern Sie die Basisklasse in einen Typ, der bereits sowohl die generischen als auch die nicht generischen Schnitt `Collection<T>` stellen implementiert, z. b. die-Klasse.

## <a name="fix-by-base-class-change"></a>Korrektur durch Basisklassen Änderung

Im folgenden Beispiel wird die Verletzung durch Ändern der-Basisklasse der-Auflistung von der nicht generischen `CollectionBase` -Klasse in die generische `Collection<T>` -Klasse (`Collection(Of T)` in Visual Basic) korrigiert.

[!code-csharp[FxCop.Design.CollectionsGenericBase#1](../code-quality/codesnippet/CSharp/ca1010-collections-should-implement-generic-interface_2.cs)]

Das Ändern der Basisklasse einer bereits freigegebenen Klasse wird als Breaking Change für vorhandene Consumer angesehen.

## <a name="fix-by-interface-implementation"></a>Korrektur nach Schnittstellen Implementierung

Im folgenden Beispiel wird die Verletzung durch Implementieren dieser generischen Schnitt `IEnumerable<T>`stellen `ICollection<T>`korrigiert: `IList<T>` ,`IEnumerable(Of T)`und `ICollection(Of T)`(, `IList(Of T)` und in Visual Basic).

[!code-csharp[FxCop.Design.CollectionsGenericInterface#1](../code-quality/codesnippet/CSharp/ca1010-collections-should-implement-generic-interface_3.cs)]

## <a name="related-rules"></a>Verwandte Regeln

- [CA1005: Übermäßige Parameter für generische Typen vermeiden](../code-quality/ca1005-avoid-excessive-parameters-on-generic-types.md)
- [CA1000: Statische Member nicht in generischen Typen deklarieren](../code-quality/ca1000-do-not-declare-static-members-on-generic-types.md)
- [CA1002: Generische Listen nicht verfügbar machen](../code-quality/ca1002-do-not-expose-generic-lists.md)
- [CA1006: Generische Typen in Element Signaturen nicht Schachteln](../code-quality/ca1006-do-not-nest-generic-types-in-member-signatures.md)
- [CA1004: Generische Methoden sollten Typparameter bereitstellen.](../code-quality/ca1004-generic-methods-should-provide-type-parameter.md)
- [CA1003: Generische Ereignishandlerinstanzen verwenden](../code-quality/ca1003-use-generic-event-handler-instances.md)
- [CA1007: Generika ggf. verwenden](../code-quality/ca1007-use-generics-where-appropriate.md)

## <a name="see-also"></a>Siehe auch

- [Generics](/dotnet/csharp/programming-guide/generics/index)