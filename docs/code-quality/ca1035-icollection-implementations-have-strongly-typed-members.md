---
title: "CA1035: ICollection-Implementierungen weisen Member mit starker Typisierung auf | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "ICollectionImplementationsHaveStronglyTypedMembers"
  - "CA1035"
helpviewer_keywords: 
  - "CA1035"
  - "ICollectionImplementationsHaveStronglyTypedMembers"
ms.assetid: ad404eb5-cf6a-44b7-b78a-8ebfb654bc7f
caps.latest.revision: 16
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
caps.handback.revision: 16
---
# CA1035: ICollection-Implementierungen weisen Member mit starker Typisierung auf
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|ICollectionImplementationsHaveStronglyTypedMembers|  
|CheckId|CA1035|  
|Kategorie \(Category\)|Microsoft.Design|  
|Unterbrechende Änderung|Breaking|  
  
## Ursache  
 Ein öffentlicher oder geschützter Typ implementiert <xref:System.Collections.ICollection?displayProperty=fullName>, gibt jedoch keine stark typisierte Methode für <xref:System.Collections.ICollection.CopyTo%2A?displayProperty=fullName> an.  Die stark typisierte Version von <xref:System.Collections.ICollection.CopyTo%2A> muss zwei Parameter annehmen und kann kein <xref:System.Array?displayProperty=fullName> oder ein Array von <xref:System.Object?displayProperty=fullName> als ersten Parameter aufweisen.  
  
## Regelbeschreibung  
 Nach dieser Regel müssen <xref:System.Collections.ICollection>\-Implementierungen stark typisierte Member angeben, damit die Benutzer keine Argumente in den <xref:System.Object>\-Typ umwandeln müssen, wenn sie die durch die Schnittstelle zur Verfügung gestellten Funktionen verwenden.  Diese Regel setzt voraus, dass der Typ, der <xref:System.Collections.ICollection> implementiert, diese Implementierung zur Verwaltung einer Auflistung von Instanzen eines Typs vornimmt, der stärker ist als <xref:System.Object>.  
  
 <xref:System.Collections.ICollection> implementiert die <xref:System.Collections.IEnumerable?displayProperty=fullName>\-Schnittstelle.  Wenn die Objekte in der Auflistung <xref:System.ValueType?displayProperty=fullName> erweitern, müssen Sie einen stark typisierten Member bereitstellen, damit <xref:System.Collections.IEnumerable.GetEnumerator%2A> die Abnahme an der Leistung verhindert, die von Boxing verursacht wird.  Dies ist nicht erforderlich, wenn die Objekte der Auflistung einen Verweistyp aufweisen.  
  
 Wenn Sie eine stark typisierte Version eines Schnittstellenmembers implementieren möchten, implementieren Sie die Schnittstellenmember explizit. Verwenden Sie dazu Namen mit der Form `InterfaceName.InterfaceMemberName`, z. B. <xref:System.Collections.ICollection.CopyTo%2A>.  Die expliziten Schnittstellenmember verwenden die von der Schnittstelle deklarierten Datentypen.  Implementieren Sie die stark typisierten Member mithilfe des Schnittstellenmembernamens, z. B. <xref:System.Collections.ICollection.CopyTo%2A>.  Deklarieren Sie die stark typisierten Member als öffentlich, und deklarieren Sie Parameter sowie Rückgabewerte mit dem von der Auflistung verwalteten starken Typ.  Die starken Typen ersetzen schwächere Typen, z. B. <xref:System.Object> und <xref:System.Array>, die von der Schnittstelle deklariert werden.  
  
## Behandeln von Verstößen  
 Um einen Verstoß gegen diese Regel zu beheben, implementieren Sie den Schnittstellenmember explizit \(deklarieren Sie ihn als <xref:System.Collections.ICollection.CopyTo%2A>\).  Fügen Sie den als `CopyTo` deklarierten öffentlichen stark typisierten Member hinzu, und lassen Sie diesen ein stark typisiertes Array als ersten Parameter annehmen.  
  
## Wann sollten Warnungen unterdrückt werden?  
 Unterdrücken Sie eine Warnung dieser Regel, wenn Sie eine neue objektbasierte Auflistung implementieren, beispielsweise eine Binärstruktur, in der Typen, die die neue Auflistung erweitern, den starken Typ bestimmen.  Diese Typen sollten dieser Regel entsprechen und stark typisierte Member verfügbar machen.  
  
## Beispiel  
 Im folgenden Beispiel wird die richtige Implementierung von <xref:System.Collections.ICollection> veranschaulicht.  
  
 [!code-cs[FxCop.Design.ICollectionStrongTypes#1](../code-quality/codesnippet/CSharp/ca1035-icollection-implementations-have-strongly-typed-members_1.cs)]  
  
## Verwandte Regeln  
 [CA1038: Enumeratoren sollten eine starke Typisierung aufweisen](../code-quality/ca1038-enumerators-should-be-strongly-typed.md)  
  
 [CA1039: Listen weisen eine starke Typisierung auf](../code-quality/ca1039-lists-are-strongly-typed.md)  
  
## Siehe auch  
 <xref:System.Array?displayProperty=fullName>   
 <xref:System.Collections.IEnumerable?displayProperty=fullName>   
 <xref:System.Collections.ICollection?displayProperty=fullName>   
 <xref:System.Object?displayProperty=fullName>