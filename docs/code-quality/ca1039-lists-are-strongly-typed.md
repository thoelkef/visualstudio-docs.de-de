---
title: 'CA1039: Listen weisen eine starke Typisierung auf'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-code-analysis
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
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 70bc0065957321894c53726790b73b432dfdea6f
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/26/2018
---
# <a name="ca1039-lists-are-strongly-typed"></a>CA1039: Listen weisen eine starke Typisierung auf
|||
|-|-|
|TypeName|ListsAreStronglyTyped|
|CheckId|CA1039|
|Kategorie|Microsoft.Design|
|Unterbrechende Änderung|Breaking|

## <a name="cause"></a>Ursache
 Öffentlicher oder geschützter Typ implementiert <xref:System.Collections.IList?displayProperty=fullName> jedoch bietet keine stark typisierte Methode für eine oder mehrere der folgenden:

-   IList.Item

-   IList.Add

-   IList.Contains

-   IList.IndexOf

-   IList.Insert

-   IList.Remove

## <a name="rule-description"></a>Regelbeschreibung
 Nach dieser Regel müssen <xref:System.Collections.IList> Implementierungen angeben, stark typisierte Member, damit Benutzer nicht erforderlich, wandeln Sie die Argumente für die <xref:System.Object?displayProperty=fullName> eingeben, wenn sie die Funktionen, die bereitgestellt wird verwenden, wird von der Schnittstelle. Die <xref:System.Collections.IList> Schnittstelle wird implementiert, anhand von Sammlungen von Objekten, die über einen Index zugegriffen werden können. Diese Regel setzt voraus, dass der Typ, der implementiert <xref:System.Collections.IList> ist diese Option, um die Verwaltung einer Auflistung von Instanzen eines Typs, der stärker ist als <xref:System.Object>.

 <xref:System.Collections.IList> implementiert die <xref:System.Collections.ICollection?displayProperty=fullName> und <xref:System.Collections.IEnumerable?displayProperty=fullName> Schnittstellen. Wenn Sie implementieren <xref:System.Collections.IList>, müssen Sie angeben, die stark typisierte erforderliche Member für <xref:System.Collections.ICollection>. Wenn die Objekte in der Auflistung erweitern <xref:System.ValueType?displayProperty=fullName>, müssen Sie für einen stark typisierten Member angeben <xref:System.Collections.IEnumerable.GetEnumerator%2A> um Leistungseinbußen zu vermeiden, der durch Boxing verursacht wird; dies ist nicht erforderlich, wenn die Objekte der Auflistung einen Referenztyp darstellt.

 Mit dieser Regel implementieren Sie die Schnittstellenmember explizit mithilfe von Namen in der Form Schnittstellenname.SchnittstelleMemberName, z. B. <xref:System.Collections.IList.Add%2A>. Die explizite Mitglieder verwenden die Datentypen, die deklariert werden durch die Schnittstelle. Implementieren Sie die stark typisierte Member mithilfe der Benutzeroberfläche der Elementname, z. B. `Add`. Die stark typisierte Member als öffentlich deklariert und deklarieren die Parameter und Rückgabewerte, die den starken Typ aufweisen, der von der Auflistung verwaltet wird. Die starke Typen ersetzen schwächere wie <xref:System.Object> und <xref:System.Array> , die von der Schnittstelle deklariert werden.

## <a name="how-to-fix-violations"></a>Behandeln von Verstößen
 Um einen Verstoß gegen diese Regel zu beheben, implementieren Sie explizit <xref:System.Collections.IList> Member und Bereitstellen von stark typisierten Alternativen für die Elemente, die bereits erwähnt wurden. Für Code, der ordnungsgemäß implementiert die <xref:System.Collections.IList> Schnittstelle, und bietet die erforderliche stark typisierte Member finden Sie im folgende Beispiel.

## <a name="when-to-suppress-warnings"></a>Wann sollten Warnungen unterdrückt werden?
 Unterdrücken Sie eine Warnung dieser Regel, wenn Sie eine neue objektbasierte Auflistung, z. B. eine verknüpfte Liste implementieren, in denen Typen, die erweitern die neue Sammlung, zu, den starken Typ bestimmen. Diese Typen sollten diese Regel erfüllen und stark typisierte Member verfügbar machen.

## <a name="example"></a>Beispiel
 Im folgenden Beispiel den Typ `YourType` erweitert <xref:System.Collections.CollectionBase?displayProperty=fullName>, wie alle stark typisierte Auflistungen sollten. Beachten Sie, dass <xref:System.Collections.CollectionBase> stellt die explizite Implementierung von der <xref:System.Collections.IList> Schnittstelle für Sie. Aus diesem Grund müssen Sie nur für die stark typisierte Member angeben <xref:System.Collections.IList> und <xref:System.Collections.ICollection>.

 [!code-csharp[FxCop.Design.IListStrongTypes#1](../code-quality/codesnippet/CSharp/ca1039-lists-are-strongly-typed_1.cs)]

## <a name="related-rules"></a>Verwandte Regeln
 [CA1035: ICollection-Implementierungen weisen Member mit starker Typisierung auf](../code-quality/ca1035-icollection-implementations-have-strongly-typed-members.md)

 [CA1038: Enumeratoren sollten eine starke Typisierung aufweisen](../code-quality/ca1038-enumerators-should-be-strongly-typed.md)

## <a name="see-also"></a>Siehe auch
 <xref:System.Collections.CollectionBase?displayProperty=fullName> <xref:System.Collections.ICollection?displayProperty=fullName> <xref:System.Collections.IEnumerable?displayProperty=fullName> <xref:System.Collections.IList?displayProperty=fullName> <xref:System.Object?displayProperty=fullName>