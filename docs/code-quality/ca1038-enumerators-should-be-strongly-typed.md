---
title: "CA1038: Enumeratoren sollten eine starke Typisierung aufweisen | Microsoft Docs"
ms.custom: ""
ms.date: "12/02/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "EnumeratorsShouldBeStronglyTyped"
  - "CA1038"
helpviewer_keywords: 
  - "CA1038"
  - "EnumeratorsShouldBeStronglyTyped"
ms.assetid: 8919f526-d487-42a4-87dc-2b2ee25260c4
caps.latest.revision: 16
caps.handback.revision: 16
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# CA1038: Enumeratoren sollten eine starke Typisierung aufweisen
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|EnumeratorsShouldBeStronglyTyped|  
|CheckId|CA1038|  
|Kategorie \(Category\)|Microsoft.Design|  
|Unterbrechende Änderung|Breaking|  
  
## Ursache  
 Ein öffentlicher oder geschützter Typ implementiert <xref:System.Collections.IEnumerator?displayProperty=fullName>, gibt jedoch keine stark typisierte Version der <xref:System.Collections.IEnumerator.Current%2A?displayProperty=fullName>\-Eigenschaft an.  Typen, die von den folgenden Typen abgeleitet sind, sind von dieser Regel ausgenommen:  
  
-   <xref:System.Collections.CollectionBase?displayProperty=fullName>  
  
-   <xref:System.Collections.DictionaryBase?displayProperty=fullName>  
  
-   <xref:System.Collections.ReadOnlyCollectionBase?displayProperty=fullName>  
  
## Regelbeschreibung  
 Nach dieser Regel müssen <xref:System.Collections.IEnumerator>\-Implementierungen für die <xref:System.Collections.IEnumerator.Current%2A>\-Eigenschaft auch eine Version mit starker Typisierung angeben, damit die Benutzer den Rückgabewert nicht in den starken Typ umwandeln müssen, wenn sie die durch die Schnittstelle zur Verfügung gestellten Funktionen verwenden.  Diese Regel setzt voraus, dass der Typ, der <xref:System.Collections.IEnumerator> implementiert, eine Auflistung von Instanzen eines Typs enthält, der stärker ist als <xref:System.Object>.  
  
## Behandeln von Verstößen  
 Um einen Verstoß gegen diese Regel zu beheben, implementieren Sie die Schnittstelleneigenschaft explizit \(deklarieren Sie sie als `IEnumerator.Current`\).  Fügen Sie eine öffentliche stark typisierte Version der Eigenschaft hinzu, die als `Current` deklariert ist, und lassen Sie diese ein stark typisiertes Objekt zurückgeben.  
  
## Wann sollten Warnungen unterdrückt werden?  
 Unterdrücken Sie eine Warnung dieser Regel, wenn Sie einen objektbasierten Enumerator implementieren, der zur Verwendung mit einer objektbasierten Auflistung, z. B. einer binären Struktur, vorgesehen ist.  Typen, die die neue Auflistung erweitern, definieren den stark typisierten Enumerator und stellen die Eigenschaft mit starker Typisierung zur Verfügung.  
  
## Beispiel  
 Im folgenden Beispiel wird das richtige Verfahren zur Implementierung eines <xref:System.Collections.IEnumerator>\-Typs mit starker Typisierung dargestellt.  
  
 [!code-cs[FxCop.Design.IEnumeratorStrongTypes#1](../code-quality/codesnippet/CSharp/ca1038-enumerators-should-be-strongly-typed_1.cs)]  
  
## Verwandte Regeln  
 [CA1035: ICollection\-Implementierungen weisen Member mit starker Typisierung auf](../code-quality/ca1035-icollection-implementations-have-strongly-typed-members.md)  
  
 [CA1039: Listen weisen eine starke Typisierung auf](../code-quality/ca1039-lists-are-strongly-typed.md)  
  
## Siehe auch  
 <xref:System.Collections.IEnumerator?displayProperty=fullName>   
 <xref:System.Collections.CollectionBase?displayProperty=fullName>   
 <xref:System.Collections.DictionaryBase?displayProperty=fullName>   
 <xref:System.Collections.ReadOnlyCollectionBase?displayProperty=fullName>