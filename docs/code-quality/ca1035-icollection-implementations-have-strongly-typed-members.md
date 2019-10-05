---
title: 'CA1035: ICollection-Implementierungen weisen Member mit starker Typisierung auf.'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- ICollectionImplementationsHaveStronglyTypedMembers
- CA1035
helpviewer_keywords:
- CA1035
- ICollectionImplementationsHaveStronglyTypedMembers
ms.assetid: ad404eb5-cf6a-44b7-b78a-8ebfb654bc7f
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 8d9e74daa464a55a543b5eb8c189c9ddf1295301
ms.sourcegitcommit: 0c2523d975d48926dd2b35bcd2d32a8ae14c06d8
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/24/2019
ms.locfileid: "71236028"
---
# <a name="ca1035-icollection-implementations-have-strongly-typed-members"></a>CA1035: ICollection-Implementierungen weisen Member mit starker Typisierung auf.

|||
|-|-|
|TypeName|ICollectionImplementationsHaveStronglyTypedMembers|
|CheckId|CA1035|
|Kategorie|Microsoft.Design|
|Unterbrechende Änderung|Breaking|

## <a name="cause"></a>Ursache
Ein öffentlicher oder geschützter Typ implementiert <xref:System.Collections.ICollection?displayProperty=fullName> , stellt jedoch keine stark typisierte Methode für <xref:System.Collections.ICollection.CopyTo%2A?displayProperty=fullName>bereit. Die stark typisierte Version <xref:System.Collections.ICollection.CopyTo%2A> von muss zwei Parameter annehmen und darf kein <xref:System.Array?displayProperty=fullName> -oder-Array <xref:System.Object?displayProperty=fullName> von als ersten Parameter aufweisen.

## <a name="rule-description"></a>Regelbeschreibung
Diese Regel erfordert <xref:System.Collections.ICollection> , dass-Implementierungen stark typisierte Member bereitstellen, sodass Benutzer keine Argumente in den <xref:System.Object> -Typ umwandeln müssen, wenn Sie die Funktionalität verwenden, die von der-Schnittstelle bereitgestellt wird. Diese Regel setzt voraus, dass der Typ <xref:System.Collections.ICollection> , der implementiert, eine Auflistung von Instanzen eines Typs verwaltet, der größer als <xref:System.Object>ist.

 <xref:System.Collections.ICollection> implementiert die <xref:System.Collections.IEnumerable?displayProperty=fullName>-Schnittstelle. Wenn die Objekte in der Auflistung erweitert <xref:System.ValueType?displayProperty=fullName>werden, müssen Sie einen stark typisierten Member <xref:System.Collections.IEnumerable.GetEnumerator%2A> für bereitstellen, um die Verringerung der Leistung zu vermeiden, die durch Boxing verursacht wird. Dies ist nicht erforderlich, wenn es sich bei den Objekten der Auflistung um einen Verweistyp handelt.

Wenn Sie eine stark typisierte Version eines Schnittstellenmembers implementieren möchten, implementieren Sie die Schnittstellenmember explizit, `InterfaceName.InterfaceMemberName`indem Sie Namen <xref:System.Collections.ICollection.CopyTo%2A>in der Form verwenden, z. b. Die expliziten Schnittstellenmember verwenden die Datentypen, die von der-Schnittstelle deklariert werden. Implementieren Sie die stark typisierten Member mithilfe des Schnittstellenmember-namens <xref:System.Collections.ICollection.CopyTo%2A>, z. b. Deklarieren Sie die stark typisierten Member als öffentlich, und deklarieren Sie Parameter und Rückgabewerte in den starken Typ, der von der Auflistung verwaltet wird. Die starken Typen ersetzen schwächere Typen, wie <xref:System.Object> z <xref:System.Array> . b. und, die von der-Schnittstelle deklariert werden.

## <a name="how-to-fix-violations"></a>Behandeln von Verstößen
Um einen Verstoß gegen diese Regel zu beheben, implementieren Sie den Schnittstellenmember explizit ( <xref:System.Collections.ICollection.CopyTo%2A>deklarieren Sie ihn als). Fügen Sie den öffentlichen Member mit starker Typisierung `CopyTo`hinzu, der als deklariert wurde, und verwenden Sie ein stark typisiertes Array als ersten Parameter.

## <a name="when-to-suppress-warnings"></a>Wann sollten Warnungen unterdrückt werden?
Unterdrückt eine Warnung aus dieser Regel, wenn Sie eine neue objektbasierte Auflistung implementieren, z. b. eine binäre Struktur, in der Typen, die die neue Auflistung erweitern, den starken Typ bestimmen. Diese Typen sollten dieser Regel entsprechen und stark typisierte Member verfügbar machen.

## <a name="example"></a>Beispiel
Im folgenden Beispiel wird die richtige Methode zum Implementieren <xref:System.Collections.ICollection>von veranschaulicht.

[!code-csharp[FxCop.Design.ICollectionStrongTypes#1](../code-quality/codesnippet/CSharp/ca1035-icollection-implementations-have-strongly-typed-members_1.cs)]

## <a name="related-rules"></a>Verwandte Regeln
[CA1038: Enumeratoren sollten stark typisiert sein.](../code-quality/ca1038-enumerators-should-be-strongly-typed.md)

[CA1039: Listen weisen eine starke Typisierung auf](../code-quality/ca1039-lists-are-strongly-typed.md)

## <a name="see-also"></a>Siehe auch

- <xref:System.Array?displayProperty=fullName>
- <xref:System.Collections.IEnumerable?displayProperty=fullName>
- <xref:System.Collections.ICollection?displayProperty=fullName>
- <xref:System.Object?displayProperty=fullName>