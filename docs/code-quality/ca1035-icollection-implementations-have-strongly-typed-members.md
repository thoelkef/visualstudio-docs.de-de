---
title: 'CA1035: ICollection-Implementierungen weisen Member mit starker Typisierung auf'
ms.date: 11/04/2016
ms.technology: vs-ide-code-analysis
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
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 40a81ea09c672728445ee4e25f82adecaa42ae79
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/19/2018
---
# <a name="ca1035-icollection-implementations-have-strongly-typed-members"></a>CA1035: ICollection-Implementierungen weisen Member mit starker Typisierung auf
|||
|-|-|
|TypeName|ICollectionImplementationsHaveStronglyTypedMembers|
|CheckId|CA1035|
|Kategorie|Microsoft.Design|
|Unterbrechende Änderung|Breaking|

## <a name="cause"></a>Ursache
 Ein öffentlicher oder geschützter Typ implementiert <xref:System.Collections.ICollection?displayProperty=fullName> jedoch nicht für eine stark typisierte Methode bietet <xref:System.Collections.ICollection.CopyTo%2A?displayProperty=fullName>. Die stark typisierte Version des <xref:System.Collections.ICollection.CopyTo%2A> muss zwei Parameter annehmen und darf keine <xref:System.Array?displayProperty=fullName> oder ein Array von <xref:System.Object?displayProperty=fullName> als ersten Parameter.

## <a name="rule-description"></a>Regelbeschreibung
 Nach dieser Regel müssen <xref:System.Collections.ICollection> Implementierungen angeben, stark typisierte Member, damit Benutzer nicht erforderlich, wandeln Sie die Argumente für die <xref:System.Object> eingeben, wenn sie die Funktionen, die bereitgestellt wird verwenden, wird von der Schnittstelle. Diese Regel setzt voraus, dass der Typ, der implementiert <xref:System.Collections.ICollection> verfügt, damit die Verwaltung einer Auflistung von Instanzen eines Typs, der stärker ist als <xref:System.Object>.

 <xref:System.Collections.ICollection> implementiert die <xref:System.Collections.IEnumerable?displayProperty=fullName>-Schnittstelle. Wenn die Objekte in der Auflistung erweitern <xref:System.ValueType?displayProperty=fullName>, müssen Sie für einen stark typisierten Member angeben <xref:System.Collections.IEnumerable.GetEnumerator%2A> um Leistungseinbußen zu vermeiden, die durch Boxing verursacht wird. Dies ist nicht erforderlich, wenn die Objekte der Auflistung einen Referenztyp darstellt.

 Um eine stark typisierte Version eines Schnittstellenmembers implementieren, implementieren Sie die Schnittstellenmember explizit mithilfe von Namen in der Form `InterfaceName.InterfaceMemberName`, wie z. B. <xref:System.Collections.ICollection.CopyTo%2A>. Die explizite Mitglieder verwenden die Datentypen, die deklariert werden durch die Schnittstelle. Implementieren Sie die stark typisierte Member mithilfe der Benutzeroberfläche der Elementname, z. B. <xref:System.Collections.ICollection.CopyTo%2A>. Die stark typisierte Member als öffentlich deklariert und deklarieren die Parameter und Rückgabewerte, die den starken Typ aufweisen, der von der Auflistung verwaltet wird. Die starke Typen ersetzen schwächere wie <xref:System.Object> und <xref:System.Array> , die von der Schnittstelle deklariert werden.

## <a name="how-to-fix-violations"></a>Behandeln von Verstößen
 Um einen Verstoß gegen diese Regel zu beheben, implementieren Sie den Schnittstellenmember explizit (deklarieren Sie es als <xref:System.Collections.ICollection.CopyTo%2A>). Hinzufügen den öffentlichen stark typisierten Member, die als deklariert `CopyTo`, und lassen Sie diesen ein stark typisiertes Array als ersten Parameter annehmen.

## <a name="when-to-suppress-warnings"></a>Wann sollten Warnungen unterdrückt werden?
 Unterdrücken Sie eine Warnung dieser Regel, wenn Sie eine neue objektbasierte Auflistung, z. B. einer binären Struktur implementieren, in denen Typen, die die neue Sammlung erweitern den starken Typ bestimmt. Diese Typen sollten diese Regel erfüllen und stark typisierte Member verfügbar machen.

## <a name="example"></a>Beispiel
 Das folgende Beispiel veranschaulicht die richtige Methode zum Implementieren <xref:System.Collections.ICollection>.

 [!code-csharp[FxCop.Design.ICollectionStrongTypes#1](../code-quality/codesnippet/CSharp/ca1035-icollection-implementations-have-strongly-typed-members_1.cs)]

## <a name="related-rules"></a>Verwandte Regeln
 [CA1038: Enumeratoren sollten eine starke Typisierung aufweisen](../code-quality/ca1038-enumerators-should-be-strongly-typed.md)

 [CA1039: Listen weisen eine starke Typisierung auf](../code-quality/ca1039-lists-are-strongly-typed.md)

## <a name="see-also"></a>Siehe auch
 <xref:System.Array?displayProperty=fullName> <xref:System.Collections.IEnumerable?displayProperty=fullName> <xref:System.Collections.ICollection?displayProperty=fullName> <xref:System.Object?displayProperty=fullName>