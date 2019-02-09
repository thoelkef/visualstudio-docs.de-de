---
title: 'CA1002: Generische Listen nicht verfügbar machen.'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- DoNotExposeGenericLists
- CA1002
helpviewer_keywords:
- CA1002
- DoNotExposeGenericLists
ms.assetid: 5caac810-1a79-47df-a27b-c46c5040bf34
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 4e2f7bba8f86ed1a2877fd622c5fd93560a9c5fa
ms.sourcegitcommit: 21d667104199c2493accec20c2388cf674b195c3
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2019
ms.locfileid: "55915829"
---
# <a name="ca1002-do-not-expose-generic-lists"></a>CA1002: Generische Listen nicht verfügbar machen.

|||
|-|-|
|TypeName|DoNotExposeGenericLists|
|CheckId|CA1002|
|Kategorie|Microsoft.Design|
|Unterbrechende Änderung|Breaking|

## <a name="cause"></a>Ursache
 Ein Typ enthält einen extern sichtbaren Member, die eine <xref:System.Collections.Generic.List%601?displayProperty=fullName> eingeben, gibt eine <xref:System.Collections.Generic.List%601?displayProperty=fullName> Typ oder enthält, deren Signatur ein <xref:System.Collections.Generic.List%601?displayProperty=fullName> Parameter.

## <a name="rule-description"></a>Regelbeschreibung
 <xref:System.Collections.Generic.List%601?displayProperty=fullName> ist eine generische Auflistung, die für die Leistung und nicht Vererbung entwickelt wurde. <xref:System.Collections.Generic.List%601?displayProperty=fullName> enthält keine virtuellen Member, die sie zum Ändern des Verhaltens von einer geerbten Klasse leichter machen. Die folgenden generischen Auflistungen dienen der Vererbung und verfügbar gemacht werden soll, anstelle von <xref:System.Collections.Generic.List%601?displayProperty=fullName>.

- <xref:System.Collections.ObjectModel.Collection%601?displayProperty=fullName>

- <xref:System.Collections.ObjectModel.ReadOnlyCollection%601?displayProperty=fullName>

- <xref:System.Collections.ObjectModel.KeyedCollection%602?displayProperty=fullName>

## <a name="how-to-fix-violations"></a>Behandeln von Verstößen
 Um einen Verstoß gegen diese Regel zu beheben, Ändern der <xref:System.Collections.Generic.List%601?displayProperty=fullName> Typ in eine der generischen Auflistungen, die für die Vererbung entwickelt wurde.

## <a name="when-to-suppress-warnings"></a>Wenn Sie Warnungen unterdrücken
 Unterdrücken Sie eine Warnung dieser Regel nicht, es sei denn, die Assembly, die diese Warnung löst keiner wiederverwendbaren Bibliothek sein soll. Beispielsweise wäre es sicher ist, unterdrücken diese Warnung in einer Anwendung für die Leistung optimiert, in denen ein Leistungsvorteil erzielt wurde aus der Verwendung von generische Listen.

## <a name="related-rules"></a>Verwandte Regeln
 [CA1005: Übermäßige Anzahl von Parametern in generischen Typen vermeiden](../code-quality/ca1005-avoid-excessive-parameters-on-generic-types.md)

 [CA1010: Auflistungen müssen eine generische Schnittstelle implementieren](../code-quality/ca1010-collections-should-implement-generic-interface.md)

 [CA1000: Statische Member in generischen Typen nicht deklarieren](../code-quality/ca1000-do-not-declare-static-members-on-generic-types.md)

 [CA1006: Generische Typen in Membersignaturen nicht schachteln](../code-quality/ca1006-do-not-nest-generic-types-in-member-signatures.md)

 [CA1004: Generische Methoden müssen den Typparameter angeben.](../code-quality/ca1004-generic-methods-should-provide-type-parameter.md)

 [CA1003: Generische Ereignishandlerinstanzen verwenden](../code-quality/ca1003-use-generic-event-handler-instances.md)

 [CA1007: Verwenden Sie Generika](../code-quality/ca1007-use-generics-where-appropriate.md)

## <a name="see-also"></a>Siehe auch
 [Generika](/dotnet/csharp/programming-guide/generics/index)