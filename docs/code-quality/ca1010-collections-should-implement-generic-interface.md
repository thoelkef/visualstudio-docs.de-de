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
ms.openlocfilehash: a62120babe98ead6d78b568bc630f46a386edf02
ms.sourcegitcommit: 2ee11676af4f3fc5729934d52541e9871fb43ee9
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/17/2019
ms.locfileid: "65842647"
---
# <a name="ca1010-collections-should-implement-generic-interface"></a>CA1010: Sammlungen müssen eine generische Schnittstelle implementieren.

|||
|-|-|
|TypeName|CollectionsShouldImplementGenericInterface|
|CheckId|CA1010|
|Kategorie|Microsoft.Design|
|Unterbrechende Änderung|Nicht unterbrechend|

## <a name="cause"></a>Ursache

Ein Typ implementiert die <xref:System.Collections.IEnumerable?displayProperty=fullName> Schnittstelle implementiert aber nicht die <xref:System.Collections.Generic.IEnumerable%601?displayProperty=fullName> -Schnittstelle und der enthaltenden Assembly Ziele. Mit dieser Regel werden ignoriert, Typen, die implementieren <xref:System.Collections.IDictionary?displayProperty=fullName>.

Diese Regel nur sucht standardmäßig an extern sichtbare Typen, aber dies ist [konfigurierbare](#configurability).

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

Es ist sicher ist, unterdrücken Sie eine Warnung dieser Regel. die Verwendung der Auflistung wird jedoch stärker eingeschränkt sein.

## <a name="configurability"></a>Konfigurierbarkeit

Wenn Sie diese Regel aus ausführen, [FxCop-Analysen](install-fxcop-analyzers.md) (und nicht über die Analyse von statischem Code), können Sie konfigurieren, welche Teile Ihrer Codebasis, um die Ausführung dieser Regel auf, um basierend auf deren Barrierefreiheit. Z. B. um anzugeben, dass die Regel nur für die nicht öffentlichen API-Oberfläche ausgeführt werden soll, fügen Sie die folgenden Schlüssel-Wert-Paar in einer editorconfig-Datei in Ihrem Projekt:

```ini
dotnet_code_quality.ca1010.api_surface = private, internal
```

Sie können diese Option, die für diese eine Regel, für alle Regeln oder für alle Regeln in dieser Kategorie (Entwurf) konfigurieren. Weitere Informationen finden Sie unter [konfigurieren FxCop-Analysetools](configure-fxcop-analyzers.md).

## <a name="example-violation"></a>Beispiel für einen Verstoß

Das folgende Beispiel zeigt eine Klasse (Referenztyp), die abgeleitet, die nicht generische `CollectionBase` -Klasse, die gegen diese Regel verstößt.

[!code-csharp[FxCop.Design.CollectionsGenericViolation#1](../code-quality/codesnippet/CSharp/ca1010-collections-should-implement-generic-interface_1.cs)]

Führen Sie eine der folgenden Schritte aus, um einen Verstoß gegen diese Regel zu beheben:

- Implementieren Sie die generischen Schnittstellen.
- Ändern Sie die Basisklasse in einen Typ, der bereits sowohl die generische und nicht generischen Schnittstellen, wie z. B. implementiert die `Collection<T>` Klasse.

## <a name="fix-by-base-class-change"></a>Beheben Sie, indem die Änderung der Basisklasse

Im folgende Beispiel wird der Verstoß korrigiert, ändern Sie die Basisklasse der Auflistung aus der nicht generischen `CollectionBase` Klasse, um die generische `Collection<T>` (`Collection(Of T)` in Visual Basic) Klasse.

[!code-csharp[FxCop.Design.CollectionsGenericBase#1](../code-quality/codesnippet/CSharp/ca1010-collections-should-implement-generic-interface_2.cs)]

Ändern die Basisklasse einer Klasse bereits veröffentlichten gilt eine wichtige Änderung für vorhandene Benutzer.

## <a name="fix-by-interface-implementation"></a>Beheben Sie die schnittstellenimplementierung

Im folgende Beispiel wird der Verstoß korrigiert, durch diese generischen Schnittstellen implementieren: `IEnumerable<T>`, `ICollection<T>`, und `IList<T>` (`IEnumerable(Of T)`, `ICollection(Of T)`, und `IList(Of T)` in Visual Basic).

[!code-csharp[FxCop.Design.CollectionsGenericInterface#1](../code-quality/codesnippet/CSharp/ca1010-collections-should-implement-generic-interface_3.cs)]

## <a name="related-rules"></a>Verwandte Regeln

- [CA1005: Übermäßige Anzahl von Parametern in generischen Typen vermeiden](../code-quality/ca1005-avoid-excessive-parameters-on-generic-types.md)
- [CA1000: Statische Member in generischen Typen nicht deklarieren](../code-quality/ca1000-do-not-declare-static-members-on-generic-types.md)
- [CA1002: Generische Listen nicht verfügbar machen](../code-quality/ca1002-do-not-expose-generic-lists.md)
- [CA1006: Generische Typen in Membersignaturen nicht schachteln](../code-quality/ca1006-do-not-nest-generic-types-in-member-signatures.md)
- [CA1004: Generische Methoden müssen den Typparameter angeben.](../code-quality/ca1004-generic-methods-should-provide-type-parameter.md)
- [CA1003: Generische Ereignishandlerinstanzen verwenden](../code-quality/ca1003-use-generic-event-handler-instances.md)
- [CA1007: Verwenden Sie Generika](../code-quality/ca1007-use-generics-where-appropriate.md)

## <a name="see-also"></a>Siehe auch

- [Generika](/dotnet/csharp/programming-guide/generics/index)