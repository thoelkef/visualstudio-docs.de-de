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
ms.openlocfilehash: 2e679fb3cc62ba80cfb7b56dfd7fa6590375565e
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "85546613"
---
# <a name="ca1035-icollection-implementations-have-strongly-typed-members"></a>CA1035: ICollection-Implementierungen weisen Member mit starker Typisierung auf.
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|Element|Wert|
|-|-|
|TypName|ICollectionImplementationsHaveStronglyTypedMembers|
|CheckId|CA1035|
|Category|Microsoft. Design|
|Unterbrechende Änderung|Breaking|

## <a name="cause"></a>Ursache
 Ein öffentlicher oder geschützter Typ implementiert, stellt <xref:System.Collections.ICollection?displayProperty=fullName> jedoch keine stark typisierte Methode für bereit <xref:System.Collections.ICollection.CopyTo%2A?displayProperty=fullName> . Die stark typisierte Version von <xref:System.Collections.ICollection.CopyTo%2A> muss zwei Parameter annehmen und darf kein- <xref:System.Array?displayProperty=fullName> oder-Array von <xref:System.Object?displayProperty=fullName> als ersten Parameter aufweisen.

## <a name="rule-description"></a>Beschreibung der Regel
 Diese Regel erfordert, <xref:System.Collections.ICollection> dass-Implementierungen stark typisierte Member bereitstellen, sodass Benutzer keine Argumente in den-Typ umwandeln müssen, <xref:System.Object> Wenn Sie die Funktionalität verwenden, die von der-Schnittstelle bereitgestellt wird. Diese Regel setzt voraus, dass der Typ, der implementiert, <xref:System.Collections.ICollection> eine Auflistung von Instanzen eines Typs verwaltet, der größer als ist <xref:System.Object> .

 <xref:System.Collections.ICollection> implementiert die <xref:System.Collections.IEnumerable?displayProperty=fullName>-Schnittstelle. Wenn die Objekte in der Auflistung erweitert <xref:System.ValueType?displayProperty=fullName> werden, müssen Sie einen stark typisierten Member für bereitstellen, <xref:System.Collections.IEnumerable.GetEnumerator%2A> um die Verringerung der Leistung zu vermeiden, die durch Boxing verursacht wird. Dies ist nicht erforderlich, wenn es sich bei den Objekten der Auflistung um einen Verweistyp handelt.

 Wenn Sie eine stark typisierte Version eines Schnittstellenmembers implementieren möchten, implementieren Sie die Schnittstellenmember explizit, indem Sie Namen in der Form verwenden `InterfaceName.InterfaceMemberName` , z <xref:System.Collections.ICollection.CopyTo%2A> . b.. Die expliziten Schnittstellenmember verwenden die Datentypen, die von der-Schnittstelle deklariert werden. Implementieren Sie die stark typisierten Member mithilfe des Schnittstellenmember-namens, z <xref:System.Collections.ICollection.CopyTo%2A> . b.. Deklarieren Sie die stark typisierten Member als öffentlich, und deklarieren Sie Parameter und Rückgabewerte in den starken Typ, der von der Auflistung verwaltet wird. Die starken Typen ersetzen schwächere Typen, wie <xref:System.Object> z <xref:System.Array> . b. und, die von der-Schnittstelle deklariert werden.

## <a name="how-to-fix-violations"></a>Behandeln von Verstößen
 Um einen Verstoß gegen diese Regel zu beheben, implementieren Sie den Schnittstellenmember explizit (deklarieren Sie ihn als <xref:System.Collections.ICollection.CopyTo%2A> ). Fügen Sie den öffentlichen Member mit starker Typisierung hinzu, der als deklariert `CopyTo` wurde, und verwenden Sie ein stark typisiertes Array als ersten Parameter.

## <a name="when-to-suppress-warnings"></a>Wann sollten Warnungen unterdrückt werden?
 Unterdrückt eine Warnung aus dieser Regel, wenn Sie eine neue objektbasierte Auflistung implementieren, z. b. eine binäre Struktur, in der Typen, die die neue Auflistung erweitern, den starken Typ bestimmen. Diese Typen sollten dieser Regel entsprechen und stark typisierte Member verfügbar machen.

## <a name="example"></a>Beispiel
 Im folgenden Beispiel wird die richtige Methode zum Implementieren von veranschaulicht <xref:System.Collections.ICollection> .

 [!code-csharp[FxCop.Design.ICollectionStrongTypes#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.ICollectionStrongTypes/cs/FxCop.Design.ICollectionStrongTypes.cs#1)]

## <a name="related-rules"></a>Verwandte Regeln
 [CA1038: Enumeratoren sollten eine starke Typisierung aufweisen.](../code-quality/ca1038-enumerators-should-be-strongly-typed.md)

 [CA1039: Listen weisen eine starke Typisierung auf.](../code-quality/ca1039-lists-are-strongly-typed.md)

## <a name="see-also"></a>Weitere Informationen
 <xref:System.Array?displayProperty=fullName> <xref:System.Collections.IEnumerable?displayProperty=fullName>
 <xref:System.Collections.ICollection?displayProperty=fullName>
 <xref:System.Object?displayProperty=fullName>
