---
title: 'CA1038: Enumeratoren sollten eine starke Typisierung aufweisen.'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- EnumeratorsShouldBeStronglyTyped
- CA1038
helpviewer_keywords:
- EnumeratorsShouldBeStronglyTyped
- CA1038
ms.assetid: 8919f526-d487-42a4-87dc-2b2ee25260c4
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 56c2281f76b9064427d1d651523b9cda441eb029
ms.sourcegitcommit: 0c2523d975d48926dd2b35bcd2d32a8ae14c06d8
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/24/2019
ms.locfileid: "71236016"
---
# <a name="ca1038-enumerators-should-be-strongly-typed"></a>CA1038: Enumeratoren sollten eine starke Typisierung aufweisen.

|||
|-|-|
|TypeName|EnumeratorsShouldBeStronglyTyped|
|CheckId|CA1038|
|Kategorie|Microsoft.Design|
|Unterbrechende Änderung|Breaking|

## <a name="cause"></a>Ursache
Ein öffentlicher oder geschützter Typ implementiert <xref:System.Collections.IEnumerator?displayProperty=fullName> , stellt jedoch keine stark typisierte Version <xref:System.Collections.IEnumerator.Current%2A?displayProperty=fullName> der Eigenschaft bereit. Typen, die von den folgenden Typen abgeleitet werden, sind von dieser Regel ausgenommen:

- <xref:System.Collections.CollectionBase?displayProperty=fullName>

- <xref:System.Collections.DictionaryBase?displayProperty=fullName>

- <xref:System.Collections.ReadOnlyCollectionBase?displayProperty=fullName>

## <a name="rule-description"></a>Regelbeschreibung
Diese Regel erfordert <xref:System.Collections.IEnumerator> , dass Implementierungen auch eine stark typisierte Version <xref:System.Collections.IEnumerator.Current%2A> der-Eigenschaft bereitstellen, damit Benutzer den Rückgabewert nicht in den starken Typ umwandeln müssen, wenn Sie die Funktionalität verwenden, die von der-Schnittstelle bereitgestellt wird. Diese Regel geht davon aus, dass der <xref:System.Collections.IEnumerator> Typ, der implementiert, eine Auflistung von Instanzen eines Typs enthält <xref:System.Object>, der größer als ist.

## <a name="how-to-fix-violations"></a>Behandeln von Verstößen
Um einen Verstoß gegen diese Regel zu beheben, implementieren Sie die Schnittstellen Eigenschaft explizit (deklarieren Sie Sie als `IEnumerator.Current`). Fügen Sie eine öffentliche, stark typisierte Version der Eigenschaft hinzu `Current`, die als deklariert wurde, und geben Sie ein stark typisiertes Objekt zurück.

## <a name="when-to-suppress-warnings"></a>Wann sollten Warnungen unterdrückt werden?
Unterdrückt eine Warnung aus dieser Regel, wenn Sie einen objektbasierten Enumerator für die Verwendung mit einer objektbasierten Auflistung implementieren, z. b. eine binäre Struktur. Typen, die die neue Auflistung erweitern, definieren den stark typisierten Enumerator und machen die stark typisierte Eigenschaft verfügbar.

## <a name="example"></a>Beispiel
Im folgenden Beispiel wird die richtige Methode zum Implementieren eines stark typisierten <xref:System.Collections.IEnumerator> Typs veranschaulicht.

[!code-csharp[FxCop.Design.IEnumeratorStrongTypes#1](../code-quality/codesnippet/CSharp/ca1038-enumerators-should-be-strongly-typed_1.cs)]

## <a name="related-rules"></a>Verwandte Regeln
[CA1035: ICollection-Implementierungen weisen Member mit starker Typisierung auf](../code-quality/ca1035-icollection-implementations-have-strongly-typed-members.md)

[CA1039: Listen weisen eine starke Typisierung auf](../code-quality/ca1039-lists-are-strongly-typed.md)

## <a name="see-also"></a>Siehe auch

- <xref:System.Collections.IEnumerator?displayProperty=fullName>
- <xref:System.Collections.CollectionBase?displayProperty=fullName>
- <xref:System.Collections.DictionaryBase?displayProperty=fullName>
- <xref:System.Collections.ReadOnlyCollectionBase?displayProperty=fullName>