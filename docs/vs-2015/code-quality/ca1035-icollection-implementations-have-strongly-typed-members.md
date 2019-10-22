---
title: 'CA1035: ICollection-Implementierungen weisen Member mit starker Typisierung auf | Microsoft-Dokumentation'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- ICollectionImplementationsHaveStronglyTypedMembers
- CA1035
helpviewer_keywords:
- CA1035
- ICollectionImplementationsHaveStronglyTypedMembers
ms.assetid: ad404eb5-cf6a-44b7-b78a-8ebfb654bc7f
caps.latest.revision: 18
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: d112e2dfb704a785db6bbc5becd2b369d90605b2
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/19/2019
ms.locfileid: "72661846"
---
# <a name="ca1035-icollection-implementations-have-strongly-typed-members"></a>CA1035: ICollection-Implementierungen weisen Member mit starker Typisierung auf
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|ICollectionImplementationsHaveStronglyTypedMembers|
|CheckId|CA1035|
|Kategorie|Microsoft. Design|
|Unterbrechende Änderung|Breaking|

## <a name="cause"></a>Ursache
 Ein öffentlicher oder geschützter Typ implementiert <xref:System.Collections.ICollection?displayProperty=fullName>, stellt jedoch keine stark typisierte Methode für <xref:System.Collections.ICollection.CopyTo%2A?displayProperty=fullName> bereit. Die stark typisierte Version von <xref:System.Collections.ICollection.CopyTo%2A> muss zwei Parameter annehmen und darf keine <xref:System.Array?displayProperty=fullName> oder ein Array von <xref:System.Object?displayProperty=fullName> als ersten Parameter aufweisen.

## <a name="rule-description"></a>Regelbeschreibung
 Diese Regel erfordert, dass <xref:System.Collections.ICollection>-Implementierungen stark typisierte Member bereitstellen, sodass Benutzer keine Argumente in den <xref:System.Object>-Typ umwandeln müssen, wenn Sie die Funktionalität verwenden, die von der-Schnittstelle bereitgestellt wird. Diese Regel setzt voraus, dass der Typ, der <xref:System.Collections.ICollection> implementiert, eine Auflistung von Instanzen eines Typs verwaltet, der stärker als <xref:System.Object> ist.

 <xref:System.Collections.ICollection> implementiert die <xref:System.Collections.IEnumerable?displayProperty=fullName>-Schnittstelle. Wenn die Objekte in der Auflistung <xref:System.ValueType?displayProperty=fullName> erweitern, müssen Sie einen stark typisierten Member für <xref:System.Collections.IEnumerable.GetEnumerator%2A> bereitstellen, um die Verringerung der Leistung zu vermeiden, die durch Boxing verursacht wird. Dies ist nicht erforderlich, wenn es sich bei den Objekten der Auflistung um einen Verweistyp handelt.

 Wenn Sie eine stark typisierte Version eines Schnittstellenmembers implementieren möchten, implementieren Sie die Schnittstellenmember explizit mithilfe von Namen in der Form `InterfaceName.InterfaceMemberName`, z. b. <xref:System.Collections.ICollection.CopyTo%2A>. Die expliziten Schnittstellenmember verwenden die Datentypen, die von der-Schnittstelle deklariert werden. Implementieren Sie die stark typisierten Member mithilfe des Schnittstellenmember-namens, z. b. <xref:System.Collections.ICollection.CopyTo%2A>. Deklarieren Sie die stark typisierten Member als öffentlich, und deklarieren Sie Parameter und Rückgabewerte in den starken Typ, der von der Auflistung verwaltet wird. Die starken Typen ersetzen schwächere Typen, z. b. <xref:System.Object> und <xref:System.Array>, die von der-Schnittstelle deklariert werden.

## <a name="how-to-fix-violations"></a>Behandeln von Verstößen
 Um einen Verstoß gegen diese Regel zu beheben, implementieren Sie den Schnittstellenmember explizit (deklarieren Sie ihn als <xref:System.Collections.ICollection.CopyTo%2A>). Fügen Sie das öffentliche, stark typisierte Element hinzu, das als `CopyTo` deklariert ist, und verwenden Sie ein Array mit starker Typisierung als ersten Parameter.

## <a name="when-to-suppress-warnings"></a>Wann sollten Warnungen unterdrückt werden?
 Unterdrückt eine Warnung aus dieser Regel, wenn Sie eine neue objektbasierte Auflistung implementieren, z. b. eine binäre Struktur, in der Typen, die die neue Auflistung erweitern, den starken Typ bestimmen. Diese Typen sollten dieser Regel entsprechen und stark typisierte Member verfügbar machen.

## <a name="example"></a>Beispiel
 Im folgenden Beispiel wird die richtige Methode zum Implementieren von <xref:System.Collections.ICollection> veranschaulicht.

 [!code-csharp[FxCop.Design.ICollectionStrongTypes#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.ICollectionStrongTypes/cs/FxCop.Design.ICollectionStrongTypes.cs#1)]

## <a name="related-rules"></a>Verwandte Regeln
 [CA1038: Enumeratoren sollten eine starke Typisierung aufweisen](../code-quality/ca1038-enumerators-should-be-strongly-typed.md)

 [CA1039: Listen weisen eine starke Typisierung auf](../code-quality/ca1039-lists-are-strongly-typed.md)

## <a name="see-also"></a>Siehe auch
 <xref:System.Array?displayProperty=fullName> <xref:System.Collections.IEnumerable?displayProperty=fullName>
 <xref:System.Collections.ICollection?displayProperty=fullName>
 <xref:System.Object?displayProperty=fullName>
