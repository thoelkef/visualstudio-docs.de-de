---
title: 'CA1039: Listen weisen eine starke Typisierung auf.'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
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
ms.openlocfilehash: 5e5a9f99bb89e78da34860cb5470627bcc5c8574
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/25/2019
ms.locfileid: "54980491"
---
# <a name="ca1039-lists-are-strongly-typed"></a>CA1039: Listen weisen eine starke Typisierung auf.

|||
|-|-|
|TypeName|ListsAreStronglyTyped|
|CheckId|CA1039|
|Kategorie|Microsoft.Design|
|Unterbrechende Änderung|Breaking|

## <a name="cause"></a>Ursache

Öffentlicher oder geschützter Typ implementiert <xref:System.Collections.IList?displayProperty=fullName> bietet jedoch keine stark typisierte Methode für eine oder mehrere der folgenden:

- IList.Item

- IList.Add

- IList.Contains

- IList.IndexOf

- IList.Insert

- IList.Remove

## <a name="rule-description"></a>Regelbeschreibung

Diese Regel muss <xref:System.Collections.IList> Implementierungen angeben, stark typisierte Member,, damit Benutzer nicht umwandeln müssen, Argumente, die die <xref:System.Object?displayProperty=fullName> eingeben, wenn sie die Funktionen verwenden, die bereitgestellt wird von der Schnittstelle. Die <xref:System.Collections.IList> Schnittstelle wird implementiert, anhand von Sammlungen von Objekten, die über einen Index zugegriffen werden können. Mit dieser Regel wird davon ausgegangen, dass der Typ, der implementiert <xref:System.Collections.IList> verwaltet eine Auflistung von Instanzen eines Typs, der stärker ist als <xref:System.Object>.

<xref:System.Collections.IList> implementiert die <xref:System.Collections.ICollection?displayProperty=fullName> und <xref:System.Collections.IEnumerable?displayProperty=fullName> Schnittstellen. Wenn Sie implementieren <xref:System.Collections.IList>, müssen Sie angeben, die stark typisierte erforderliche Member für <xref:System.Collections.ICollection>. Wenn die Objekte in der Auflistung erweitern <xref:System.ValueType?displayProperty=fullName>, müssen Sie für einen stark typisierten Member angeben <xref:System.Collections.IEnumerable.GetEnumerator%2A> um Leistungseinbußen zu vermeiden, der durch Boxing verursacht werden; dies ist nicht erforderlich, wenn die Objekte der Auflistung einen Verweistyp handelt.

Mit dieser Regel implementieren Sie den Schnittstellenmember explizit unter Verwendung der Form Schnittstellenname.SchnittstelleMemberName, z. B. <xref:System.Collections.IList.Add%2A>. Die explizite Schnittstellenmember werden die Datentypen, die deklariert werden durch die Schnittstelle verwenden. Die stark typisierte Member implementieren, indem Sie den Namen des Schnittstellenmembers, wie `Add`. Die stark typisierte Member als öffentlich deklariert und deklarieren Sie die Parameter und Rückgabewerte, um den starken Typ aufweisen, der von der Sammlung verwaltet wird. Die starke Typen ersetzen schwächere Typen wie z. B. <xref:System.Object> und <xref:System.Array> , die von der Schnittstelle deklariert werden.

## <a name="how-to-fix-violations"></a>Behandeln von Verstößen
 Um einen Verstoß gegen diese Regel zu beheben, implementieren Sie explizit <xref:System.Collections.IList> Mitglieder und stark typisierte Alternativen für die Elemente, die zuvor erwähnten bereitstellen. Für Code, der ordnungsgemäß implementiert die <xref:System.Collections.IList> Schnittstelle, und bietet die erforderliche stark typisierte Member, siehe folgendes Beispiel.

## <a name="when-to-suppress-warnings"></a>Wenn Sie Warnungen unterdrücken
 Unterdrücken Sie eine Warnung dieser Regel, wenn Sie eine neue objektbasierte Sammlung, z. B. eine verknüpfte Liste implementieren, in dem der Typen, die die neue Auflistung erweitern den starken Typ bestimmen. Diese Typen sollten mit dieser Regel entsprechen und stark typisierte Member verfügbar machen.

## <a name="example"></a>Beispiel
 Im folgenden Beispiel den Typ `YourType` erweitert <xref:System.Collections.CollectionBase?displayProperty=fullName>, wie alle stark typisierte Auflistungen sollte. <xref:System.Collections.CollectionBase> Stellt die explizite Implementierung von der <xref:System.Collections.IList> Schnittstelle für Sie. Aus diesem Grund müssen Sie nur für die stark typisierte Member angeben <xref:System.Collections.IList> und <xref:System.Collections.ICollection>.

 [!code-csharp[FxCop.Design.IListStrongTypes#1](../code-quality/codesnippet/CSharp/ca1039-lists-are-strongly-typed_1.cs)]

## <a name="related-rules"></a>Verwandte Regeln
 [CA1035: ICollection-Implementierungen weisen Member mit starker Typisierung](../code-quality/ca1035-icollection-implementations-have-strongly-typed-members.md)

 [CA1038: Enumeratoren sollten eine starke Typisierung aufweisen](../code-quality/ca1038-enumerators-should-be-strongly-typed.md)

## <a name="see-also"></a>Siehe auch

- <xref:System.Collections.CollectionBase?displayProperty=fullName>
- <xref:System.Collections.ICollection?displayProperty=fullName>
- <xref:System.Collections.IEnumerable?displayProperty=fullName>
- <xref:System.Collections.IList?displayProperty=fullName>
- <xref:System.Object?displayProperty=fullName>