---
title: 'CA1038: Enumeratoren sollten stark typisiert sein | Microsoft-Dokumentation'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- EnumeratorsShouldBeStronglyTyped
- CA1038
helpviewer_keywords:
- EnumeratorsShouldBeStronglyTyped
- CA1038
ms.assetid: 8919f526-d487-42a4-87dc-2b2ee25260c4
caps.latest.revision: 18
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: e660b1af58dca8d0d69ce2844076382c4a5a1f12
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "85548264"
---
# <a name="ca1038-enumerators-should-be-strongly-typed"></a>CA1038: Enumeratoren sollten eine starke Typisierung aufweisen.
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|Element|value|
|-|-|
|TypName|EnumeratorsShouldBeStronglyTyped|
|CheckId|CA1038|
|Category|Microsoft. Design|
|Unterbrechende Änderung|Breaking|

## <a name="cause"></a>Ursache
 Ein öffentlicher oder geschützter Typ implementiert, stellt <xref:System.Collections.IEnumerator?displayProperty=fullName> jedoch keine stark typisierte Version der <xref:System.Collections.IEnumerator.Current%2A?displayProperty=fullName> Eigenschaft bereit. Typen, die von den folgenden Typen abgeleitet werden, sind von dieser Regel ausgenommen:

- <xref:System.Collections.CollectionBase?displayProperty=fullName>

- <xref:System.Collections.DictionaryBase?displayProperty=fullName>

- <xref:System.Collections.ReadOnlyCollectionBase?displayProperty=fullName>

## <a name="rule-description"></a>Beschreibung der Regel
 Diese Regel erfordert, <xref:System.Collections.IEnumerator> dass Implementierungen auch eine stark typisierte Version der-Eigenschaft bereitstellen, <xref:System.Collections.IEnumerator.Current%2A> damit Benutzer den Rückgabewert nicht in den starken Typ umwandeln müssen, wenn Sie die Funktionalität verwenden, die von der-Schnittstelle bereitgestellt wird. Diese Regel geht davon aus, dass der Typ, der implementiert, <xref:System.Collections.IEnumerator> eine Auflistung von Instanzen eines Typs enthält, der größer als ist <xref:System.Object> .

## <a name="how-to-fix-violations"></a>Behandeln von Verstößen
 Um einen Verstoß gegen diese Regel zu beheben, implementieren Sie die Schnittstellen Eigenschaft explizit (deklarieren Sie Sie als `IEnumerator.Current` ). Fügen Sie eine öffentliche, stark typisierte Version der Eigenschaft hinzu, die als deklariert `Current` wurde, und geben Sie ein stark typisiertes Objekt zurück.

## <a name="when-to-suppress-warnings"></a>Wann sollten Warnungen unterdrückt werden?
 Unterdrückt eine Warnung aus dieser Regel, wenn Sie einen objektbasierten Enumerator für die Verwendung mit einer objektbasierten Auflistung implementieren, z. b. eine binäre Struktur. Typen, die die neue Auflistung erweitern, definieren den stark typisierten Enumerator und machen die stark typisierte Eigenschaft verfügbar.

## <a name="example"></a>Beispiel
 Im folgenden Beispiel wird die richtige Methode zum Implementieren eines stark typisierten <xref:System.Collections.IEnumerator> Typs veranschaulicht.

 [!code-csharp[FxCop.Design.IEnumeratorStrongTypes#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.IEnumeratorStrongTypes/cs/FxCop.Design.IEnumeratorStrongTypes.cs#1)]

## <a name="related-rules"></a>Verwandte Regeln
 [CA1035: ICollection-Implementierungen weisen Member mit starker Typisierung auf.](../code-quality/ca1035-icollection-implementations-have-strongly-typed-members.md)

 [CA1039: Listen weisen eine starke Typisierung auf.](../code-quality/ca1039-lists-are-strongly-typed.md)

## <a name="see-also"></a>Weitere Informationen
 <xref:System.Collections.IEnumerator?displayProperty=fullName> <xref:System.Collections.CollectionBase?displayProperty=fullName>
 <xref:System.Collections.DictionaryBase?displayProperty=fullName>
 <xref:System.Collections.ReadOnlyCollectionBase?displayProperty=fullName>
