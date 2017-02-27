---
title: "CA2227: Auflistungseigenschaften sollten schreibgesch&#252;tzt sein | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CA2227"
  - "CollectionPropertiesShouldBeReadOnly"
helpviewer_keywords: 
  - "CA2227"
  - "CollectionPropertiesShouldBeReadOnly"
ms.assetid: 26967aaf-6fbe-438a-b4d3-ac579b5dc0f9
caps.latest.revision: 17
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
caps.handback.revision: 17
---
# CA2227: Auflistungseigenschaften sollten schreibgesch&#252;tzt sein
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|CollectionPropertiesShouldBeReadOnly|  
|CheckId|CA2227|  
|Kategorie \(Category\)|Microsoft.Usage|  
|Unterbrechende Änderung|Breaking|  
  
## Ursache  
 Eine extern sichtbare schreibbare Eigenschaft ist ein Typ, der <xref:System.Collections.ICollection?displayProperty=fullName> implementiert.  Arrays, Indexer \(Eigenschaften mit dem Namen 'Item'\) und Berechtigungssätze werden von der Regel ignoriert.  
  
## Regelbeschreibung  
 Eine schreibbare Auflistungseigenschaft ermöglicht einem Benutzer, die Auflistung durch eine vollkommen andere Auflistung zu ersetzen.  Eine schreibgeschützte Eigenschaft sorgt dafür, dass die Auflistung nicht mehr ersetzt wird, lässt aber dennoch das Festlegen einzelner Member zu.  Wenn das Ziel darin besteht, die Auflistung zu ersetzen, sollte in das Entwurfsmuster eine Methode eingefügt werden, die alle Elemente aus der Auflistung entfernt, sowie eine Methode, mit der die Auflistung neu aufgefüllt wird.  Ein Beispiel für dieses Muster finden Sie in der <xref:System.Collections.ArrayList.Clear%2A>\-Methode und der <xref:System.Collections.ArrayList.AddRange%2A>\-Methode der <xref:System.Collections.ArrayList?displayProperty=fullName>\-Klasse.  
  
 Sowohl die binäre als auch die XML\-Serialisierung unterstützen schreibgeschützte Eigenschaften, bei denen es sich um Auflistungen handelt.  Für die <xref:System.Xml.Serialization.XmlSerializer?displayProperty=fullName>\-Klasse bestehen bestimmte Anforderungen für Typen, die <xref:System.Collections.ICollection> und <xref:System.Collections.IEnumerable?displayProperty=fullName> implementieren, um serialisierbar zu sein.  
  
## Behandeln von Verstößen  
 Um einen Verstoß gegen diese Regel zu beheben, definieren Sie die Eigenschaft als schreibgeschützt, und – falls erforderlich für das Design – fügen Sie Methoden zum Leeren und erneuten Auffüllen der Auflistung hinzu.  
  
## Wann sollten Warnungen unterdrückt werden?  
 Unterdrücken Sie keine Warnung dieser Regel.  
  
## Beispiel  
 Das folgende Beispiel zeigt einen Typ mit einer schreibbaren Auflistungseigenschaft und verdeutlicht, wie die Auflistung direkt ersetzt werden kann.  Zudem wird die bevorzugte Methode des Ersetzens einer schreibgeschützten Auflistungseigenschaft mit der `Clear`\-Methode und der `AddRange`\-Methode veranschaulicht.  
  
 [!code-cs[FxCop.Usage.PropertiesReturningCollections#1](../code-quality/codesnippet/CSharp/ca2227-collection-properties-should-be-read-only_1.cs)]
 [!code-vb[FxCop.Usage.PropertiesReturningCollections#1](../code-quality/codesnippet/VisualBasic/ca2227-collection-properties-should-be-read-only_1.vb)]
 [!code-cpp[FxCop.Usage.PropertiesReturningCollections#1](../code-quality/codesnippet/CPP/ca2227-collection-properties-should-be-read-only_1.cpp)]  
  
## Verwandte Regeln  
 [CA1819: Eigenschaften sollten keine Arrays zurückgeben](../code-quality/ca1819-properties-should-not-return-arrays.md)