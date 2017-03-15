---
title: "CA1039: Listen weisen eine starke Typisierung auf | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CA1039"
  - "ListsAreStronglyTyped"
helpviewer_keywords: 
  - "CA1039"
  - "ListsAreStronglyTyped"
ms.assetid: 5ac366c4-fd87-4d5c-95d5-f755510c8e5c
caps.latest.revision: 15
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
caps.handback.revision: 15
---
# CA1039: Listen weisen eine starke Typisierung auf
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|ListsAreStronglyTyped|  
|CheckId|CA1039|  
|Kategorie \(Category\)|Microsoft.Design|  
|Unterbrechende Änderung|Breaking|  
  
## Ursache  
 Der öffentliche oder geschützte Typ implementiert <xref:System.Collections.IList?displayProperty=fullName>, stellt jedoch keine stark typisierte Methode für mindestens eines der folgenden Elemente bereit:  
  
-   IList.Item  
  
-   IList.Add  
  
-   IList.Contains  
  
-   IList.IndexOf  
  
-   IList.Insert  
  
-   IList.Remove  
  
## Regelbeschreibung  
 Nach dieser Regel müssen <xref:System.Collections.IList>\-Implementierungen stark typisierte Member angeben, damit die Benutzer keine Argumente in den <xref:System.Object?displayProperty=fullName>\-Typ umwandeln müssen, wenn sie die durch die Schnittstelle zur Verfügung gestellten Funktionen verwenden.  Die <xref:System.Collections.IList>\-Schnittstelle wird durch Auflistungen von Objekten implementiert, auf die per Index zugegriffen werden kann.  Diese Regel setzt voraus, dass der Typ, der <xref:System.Collections.IList> implementiert, diese Implementierung zur Verwaltung einer Auflistung von Instanzen eines Typs vornimmt, der stärker ist als <xref:System.Object>.  
  
 <xref:System.Collections.IList> implementiert die <xref:System.Collections.ICollection?displayProperty=fullName>\-Schnittstelle und die <xref:System.Collections.IEnumerable?displayProperty=fullName>\-Schnittstelle.  Wenn Sie <xref:System.Collections.IList> implementieren, müssen Sie die erforderlichen stark typisierten Member für <xref:System.Collections.ICollection> angeben.  Wenn die Objekte in der Auflistung <xref:System.ValueType?displayProperty=fullName> erweitern, müssen Sie einen stark typisierten Member für <xref:System.Collections.IEnumerable.GetEnumerator%2A> angeben, um durch Boxing verursachte Leistungseinbußen zu vermeiden. Dies ist nicht erforderlich, wenn es sich bei den Objekten der Auflistung um einen Verweistyp handelt.  
  
 Implementieren Sie die Schnittstellenmember zwecks Einhaltung dieser Regel explizit, und verwenden Sie dabei Namen der Form SchnittstellenName.SchnittstellenMemberName, z. B. <xref:System.Collections.IList.Add%2A>.  Die expliziten Schnittstellenmember verwenden die von der Schnittstelle deklarierten Datentypen.  Implementieren Sie die stark typisierten Member mithilfe des Schnittstellenmembernamens, z. B. `Add`.  Deklarieren Sie die stark typisierten Member als öffentlich, und deklarieren Sie Parameter sowie Rückgabewerte mit dem von der Auflistung verwalteten starken Typ.  Die starken Typen ersetzen schwächere Typen, z. B. <xref:System.Object> und <xref:System.Array>, die von der Schnittstelle deklariert werden.  
  
## Behandeln von Verstößen  
 Um einen Verstoß gegen diese Regel zu beheben, implementieren Sie <xref:System.Collections.IList>\-Member explizit, und geben Sie für die zuvor genannten Member stark typisierte Alternativen an.  Im folgenden Beispiel ist Code enthalten, durch den die <xref:System.Collections.IList>\-Schnittstelle ordnungsgemäß implementiert wird und der die erforderlichen stark typisierten Member angibt.  
  
## Wann sollten Warnungen unterdrückt werden?  
 Unterdrücken Sie eine Warnung dieser Regel, wenn Sie eine neue objektbasierte Auflistung implementieren, beispielsweise eine verknüpfte Liste, in der Typen, die die neue Auflistung erweitern, den starken Typ bestimmen.  Diese Typen sollten dieser Regel entsprechen und stark typisierte Member verfügbar machen.  
  
## Beispiel  
 Im folgenden Beispiel wird <xref:System.Collections.CollectionBase?displayProperty=fullName> durch den `YourType`\-Typ erweitert, wie dies bei allen stark typisierten Auflistungen geschehen sollte.  Beachten Sie, dass <xref:System.Collections.CollectionBase> die explizite Implementierung der <xref:System.Collections.IList>\-Schnittstelle für Sie bereitstellt.  Daher müssen Sie nur die stark typisierten Member für <xref:System.Collections.IList> und <xref:System.Collections.ICollection> bereitstellen.  
  
 [!code-cs[FxCop.Design.IListStrongTypes#1](../code-quality/codesnippet/CSharp/ca1039-lists-are-strongly-typed_1.cs)]  
  
## Verwandte Regeln  
 [CA1035: ICollection\-Implementierungen weisen Member mit starker Typisierung auf](../code-quality/ca1035-icollection-implementations-have-strongly-typed-members.md)  
  
 [CA1038: Enumeratoren sollten eine starke Typisierung aufweisen](../code-quality/ca1038-enumerators-should-be-strongly-typed.md)  
  
## Siehe auch  
 <xref:System.Collections.CollectionBase?displayProperty=fullName>   
 <xref:System.Collections.ICollection?displayProperty=fullName>   
 <xref:System.Collections.IEnumerable?displayProperty=fullName>   
 <xref:System.Collections.IList?displayProperty=fullName>   
 <xref:System.Object?displayProperty=fullName>