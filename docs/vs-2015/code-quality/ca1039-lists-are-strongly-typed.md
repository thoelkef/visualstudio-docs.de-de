---
title: 'CA1039: Listen weisen eine starke Typisierung auf | Microsoft-Dokumentation'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA1039
- ListsAreStronglyTyped
helpviewer_keywords:
- CA1039
- ListsAreStronglyTyped
ms.assetid: 5ac366c4-fd87-4d5c-95d5-f755510c8e5c
caps.latest.revision: 17
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 4e485375c12564b5416c79bd3a41dedb1da76dc0
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "85533444"
---
# <a name="ca1039-lists-are-strongly-typed"></a>CA1039: Listen weisen eine starke Typisierung auf.
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|Element|Wert|
|-|-|
|TypName|ListsAreStronglyTyped|
|CheckId|CA1039|
|Category|Microsoft. Design|
|Unterbrechende Änderung|Breaking|

## <a name="cause"></a>Ursache
 Der öffentliche oder geschützte Typ implementiert, stellt <xref:System.Collections.IList?displayProperty=fullName> jedoch keine stark typisierte Methode für eine oder mehrere der folgenden Methoden bereit:

- IList. Item

- IList. Add

- IList. enthält

- IList. IndexOf

- IList. Insert

- IList. Remove

## <a name="rule-description"></a>Beschreibung der Regel
 Diese Regel erfordert, <xref:System.Collections.IList> dass-Implementierungen stark typisierte Member bereitstellen, sodass Benutzer keine Argumente in den-Typ umwandeln müssen, <xref:System.Object?displayProperty=fullName> Wenn Sie die Funktionalität verwenden, die von der-Schnittstelle bereitgestellt wird. Die- <xref:System.Collections.IList> Schnittstelle wird durch Auflistungen von Objekten implementiert, auf die über einen Index zugegriffen werden kann. Diese Regel geht davon aus, dass der Typ, der implementiert, dies bewirkt, <xref:System.Collections.IList> um eine Auflistung von Instanzen eines Typs zu verwalten, der größer als ist <xref:System.Object> .

 <xref:System.Collections.IList> implementiert die <xref:System.Collections.ICollection?displayProperty=fullName> <xref:System.Collections.IEnumerable?displayProperty=fullName> Schnittstellen und. Wenn Sie implementieren <xref:System.Collections.IList> , müssen Sie die erforderlichen stark typisierten Member für bereitstellen <xref:System.Collections.ICollection> . Wenn die Objekte in der Auflistung erweitert <xref:System.ValueType?displayProperty=fullName> werden, müssen Sie einen stark typisierten Member für bereitstellen, <xref:System.Collections.IEnumerable.GetEnumerator%2A> um die Verringerung der Leistung zu vermeiden, die durch Boxing verursacht wird. Dies ist nicht erforderlich, wenn die Objekte der Auflistung ein Verweistyp sind.

 Um diese Regel einzuhalten, implementieren Sie die Schnittstellenmember explizit, indem Sie Namen in der Form InterfaceName. interfacemembership Name verwenden, z <xref:System.Collections.IList.Add%2A> . b.. Die expliziten Schnittstellenmember verwenden die Datentypen, die von der-Schnittstelle deklariert werden. Implementieren Sie die stark typisierten Member mithilfe des Schnittstellenmember-namens, z `Add` . b.. Deklarieren Sie die stark typisierten Member als öffentlich, und deklarieren Sie Parameter und Rückgabewerte in den starken Typ, der von der Auflistung verwaltet wird. Die starken Typen ersetzen schwächere Typen, wie <xref:System.Object> z <xref:System.Array> . b. und, die von der-Schnittstelle deklariert werden.

## <a name="how-to-fix-violations"></a>Behandeln von Verstößen
 Um einen Verstoß gegen diese Regel zu beheben, müssen Sie explizit Member implementieren <xref:System.Collections.IList> und stark typisierte Alternativen für die Member bereitstellen, die zuvor notiert wurden. Informationen zu Code, der die <xref:System.Collections.IList> -Schnittstelle ordnungsgemäß implementiert und die erforderlichen stark typisierten Member bereitstellt, finden Sie im folgenden Beispiel.

## <a name="when-to-suppress-warnings"></a>Wann sollten Warnungen unterdrückt werden?
 Unterdrückt eine Warnung aus dieser Regel, wenn Sie eine neue objektbasierte Auflistung implementieren, z. b. eine verknüpfte Liste, in der Typen, die die neue Auflistung erweitern, den starken Typ bestimmen. Diese Typen sollten dieser Regel entsprechen und stark typisierte Member verfügbar machen.

## <a name="example"></a>Beispiel
 Im folgenden Beispiel erweitert der-Typ `YourType` <xref:System.Collections.CollectionBase?displayProperty=fullName> , wie alle stark typisierten Auflistungen. Beachten Sie, dass <xref:System.Collections.CollectionBase> die explizite Implementierung der- <xref:System.Collections.IList> Schnittstelle für Sie bereitstellt. Daher müssen Sie nur die stark typisierten Member für <xref:System.Collections.IList> und angeben <xref:System.Collections.ICollection> .

 [!code-csharp[FxCop.Design.IListStrongTypes#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.IListStrongTypes/cs/FxCop.Design.IListStrongTypes.cs#1)]

## <a name="related-rules"></a>Verwandte Regeln
 [CA1035: ICollection-Implementierungen weisen Member mit starker Typisierung auf.](../code-quality/ca1035-icollection-implementations-have-strongly-typed-members.md)

 [CA1038: Enumeratoren sollten eine starke Typisierung aufweisen.](../code-quality/ca1038-enumerators-should-be-strongly-typed.md)

## <a name="see-also"></a>Weitere Informationen
 <xref:System.Collections.CollectionBase?displayProperty=fullName> <xref:System.Collections.ICollection?displayProperty=fullName>
 <xref:System.Collections.IEnumerable?displayProperty=fullName>
 <xref:System.Collections.IList?displayProperty=fullName>
 <xref:System.Object?displayProperty=fullName>
