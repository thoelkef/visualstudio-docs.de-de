---
title: 'CA1039: Listen weisen eine starke Typisierung auf.'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- CA1039
- ListsAreStronglyTyped
helpviewer_keywords:
- CA1039
- ListsAreStronglyTyped
ms.assetid: 5ac366c4-fd87-4d5c-95d5-f755510c8e5c
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 94b1e8134eb89e4ae78ec0ad6f07fd7406215185
ms.sourcegitcommit: 5216c15e9f24d1d5db9ebe204ee0e7ad08705347
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/09/2019
ms.locfileid: "68922844"
---
# <a name="ca1039-lists-are-strongly-typed"></a>CA1039: Listen weisen eine starke Typisierung auf.

|||
|-|-|
|TypeName|ListsAreStronglyTyped|
|CheckId|CA1039|
|Kategorie|Microsoft.Design|
|Unterbrechende Änderung|Breaking|

## <a name="cause"></a>Ursache

Der öffentliche oder geschützte Typ implementiert <xref:System.Collections.IList?displayProperty=fullName> , stellt jedoch keine stark typisierte Methode für eine oder mehrere der folgenden Methoden bereit:

- IList. Item

- IList. Add

- IList.Contains

- IList. IndexOf

- IList. Insert

- IList.Remove

## <a name="rule-description"></a>Regelbeschreibung

Diese Regel erfordert <xref:System.Collections.IList> , dass-Implementierungen stark typisierte Member bereitstellen, sodass Benutzer keine Argumente in den <xref:System.Object?displayProperty=fullName> -Typ umwandeln müssen, wenn Sie die Funktionalität verwenden, die von der-Schnittstelle bereitgestellt wird. Die <xref:System.Collections.IList> -Schnittstelle wird durch Auflistungen von Objekten implementiert, auf die über einen Index zugegriffen werden kann. Diese Regel geht davon aus, dass der <xref:System.Collections.IList> Typ, der implementiert, eine Auflistung von Instanzen eines Typs verwaltet <xref:System.Object>, der größer als ist.

<xref:System.Collections.IList>implementiert die <xref:System.Collections.ICollection?displayProperty=fullName> Schnitt <xref:System.Collections.IEnumerable?displayProperty=fullName> stellen und. Wenn Sie implementieren <xref:System.Collections.IList>, müssen Sie die erforderlichen stark typisierten Member für <xref:System.Collections.ICollection>bereitstellen. Wenn die Objekte in der Auflistung erweitert <xref:System.ValueType?displayProperty=fullName>werden, müssen Sie einen stark typisierten Member <xref:System.Collections.IEnumerable.GetEnumerator%2A> für bereitstellen, um die Verringerung der Leistung zu vermeiden, die durch Boxing verursacht wird. Dies ist nicht erforderlich, wenn die Objekte der Auflistung ein Verweistyp sind.

Um diese Regel einzuhalten, implementieren Sie die Schnittstellenmember explizit, indem Sie Namen in der Form InterfaceName. interfacemembership Name verwenden <xref:System.Collections.IList.Add%2A>, z. b. Die expliziten Schnittstellenmember verwenden die Datentypen, die von der-Schnittstelle deklariert werden. Implementieren Sie die stark typisierten Member mithilfe des Schnittstellenmember-namens `Add`, z. b. Deklarieren Sie die stark typisierten Member als öffentlich, und deklarieren Sie Parameter und Rückgabewerte in den starken Typ, der von der Auflistung verwaltet wird. Die starken Typen ersetzen schwächere Typen, wie <xref:System.Object> z <xref:System.Array> . b. und, die von der-Schnittstelle deklariert werden.

## <a name="how-to-fix-violations"></a>Behandeln von Verstößen
Um einen Verstoß gegen diese Regel zu beheben, müssen <xref:System.Collections.IList> Sie explizit Member implementieren und stark typisierte Alternativen für die Member bereitstellen, die zuvor notiert wurden. Informationen zu Code, der die <xref:System.Collections.IList> -Schnittstelle ordnungsgemäß implementiert und die erforderlichen stark typisierten Member bereitstellt, finden Sie im folgenden Beispiel.

## <a name="when-to-suppress-warnings"></a>Wann sollten Warnungen unterdrückt werden?
Unterdrückt eine Warnung aus dieser Regel, wenn Sie eine neue objektbasierte Auflistung implementieren, z. b. eine verknüpfte Liste, in der Typen, die die neue Auflistung erweitern, den starken Typ bestimmen. Diese Typen sollten dieser Regel entsprechen und stark typisierte Member verfügbar machen.

## <a name="example"></a>Beispiel
Im folgenden Beispiel erweitert `YourType` <xref:System.Collections.CollectionBase?displayProperty=fullName>der-Typ, wie alle stark typisierten Auflistungen. <xref:System.Collections.CollectionBase>stellt die explizite Implementierung <xref:System.Collections.IList> der-Schnittstelle für Sie bereit. Daher müssen Sie nur die stark typisierten Member für <xref:System.Collections.IList> und <xref:System.Collections.ICollection>angeben.

[!code-csharp[FxCop.Design.IListStrongTypes#1](../code-quality/codesnippet/CSharp/ca1039-lists-are-strongly-typed_1.cs)]

## <a name="related-rules"></a>Verwandte Regeln
[CA1035: ICollection-Implementierungen weisen Member mit starker Typisierung auf](../code-quality/ca1035-icollection-implementations-have-strongly-typed-members.md)

[CA1038: Enumeratoren sollten stark typisiert sein.](../code-quality/ca1038-enumerators-should-be-strongly-typed.md)

## <a name="see-also"></a>Siehe auch

- <xref:System.Collections.CollectionBase?displayProperty=fullName>
- <xref:System.Collections.ICollection?displayProperty=fullName>
- <xref:System.Collections.IEnumerable?displayProperty=fullName>
- <xref:System.Collections.IList?displayProperty=fullName>
- <xref:System.Object?displayProperty=fullName>