---
title: 'CA1038: Enumeratoren sollten stark typisiert | Microsoft Docs'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- EnumeratorsShouldBeStronglyTyped
- CA1038
helpviewer_keywords:
- EnumeratorsShouldBeStronglyTyped
- CA1038
ms.assetid: 8919f526-d487-42a4-87dc-2b2ee25260c4
caps.latest.revision: "16"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: c08d8ce661e46f76da6d2880bd6b4e833f0b4d1d
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/31/2017
---
# <a name="ca1038-enumerators-should-be-strongly-typed"></a>CA1038: Enumeratoren sollten eine starke Typisierung aufweisen
|||  
|-|-|  
|TypeName|EnumeratorsShouldBeStronglyTyped|  
|CheckId|CA1038|  
|Kategorie|Microsoft.Design|  
|Unterbrechende Änderung|Breaking|  
  
## <a name="cause"></a>Ursache  
 Ein öffentlicher oder geschützter Typ implementiert <xref:System.Collections.IEnumerator?displayProperty=fullName> jedoch keine stark typisierte Version von bietet die <xref:System.Collections.IEnumerator.Current%2A?displayProperty=fullName> Eigenschaft. Typen, die aus den folgenden Typen abgeleitet sind, die von dieser Regel ausgenommen sind:  
  
-   <xref:System.Collections.CollectionBase?displayProperty=fullName>  
  
-   <xref:System.Collections.DictionaryBase?displayProperty=fullName>  
  
-   <xref:System.Collections.ReadOnlyCollectionBase?displayProperty=fullName>  
  
## <a name="rule-description"></a>Regelbeschreibung  
 Nach dieser Regel müssen <xref:System.Collections.IEnumerator> Implementierungen für eine stark typisierte Version des auch angeben, die <xref:System.Collections.IEnumerator.Current%2A> Eigenschaft, damit Benutzer nicht erforderlich sind, den Rückgabewert in den starken Typ umwandeln, wenn sie die bereitgestellte Funktionalität durch die Schnittstelle verwenden. Diese Regel setzt voraus, dass der Typ, der implementiert <xref:System.Collections.IEnumerator> enthält eine Auflistung von Instanzen eines Typs, der stärker ist als <xref:System.Object>.  
  
## <a name="how-to-fix-violations"></a>Behandeln von Verstößen  
 Um einen Verstoß gegen diese Regel zu beheben, implementieren Sie die Schnittstelleneigenschaft explizit (deklarieren Sie es als `IEnumerator.Current`). Fügen Sie eine öffentliche stark typisierte Version der Eigenschaft, die als deklariert `Current`, und lassen Sie diese ein stark typisiertes Objekt zurückgeben.  
  
## <a name="when-to-suppress-warnings"></a>Wann sollten Warnungen unterdrückt werden?  
 Unterdrücken Sie eine Warnung dieser Regel, wenn Sie einen objektbasierten Enumerator für die Verwendung mit einem objektbasierten Auflistung, z. B. einer binären Struktur implementieren. Typen, die erweitern die neue Sammlung, definieren den stark typisierten Enumerator und stark typisierte Eigenschaft verfügbar machen.  
  
## <a name="example"></a>Beispiel  
 Das folgende Beispiel zeigt die korrekte Methode zum Implementieren eines stark typisierten <xref:System.Collections.IEnumerator> Typ.  
  
 [!code-csharp[FxCop.Design.IEnumeratorStrongTypes#1](../code-quality/codesnippet/CSharp/ca1038-enumerators-should-be-strongly-typed_1.cs)]  
  
## <a name="related-rules"></a>Verwandte Regeln  
 [CA1035: ICollection-Implementierungen weisen Member mit starker Typisierung auf](../code-quality/ca1035-icollection-implementations-have-strongly-typed-members.md)  
  
 [CA1039: Listen weisen eine starke Typisierung auf](../code-quality/ca1039-lists-are-strongly-typed.md)  
  
## <a name="see-also"></a>Siehe auch  
 <xref:System.Collections.IEnumerator?displayProperty=fullName>   
 <xref:System.Collections.CollectionBase?displayProperty=fullName>   
 <xref:System.Collections.DictionaryBase?displayProperty=fullName>   
 <xref:System.Collections.ReadOnlyCollectionBase?displayProperty=fullName>