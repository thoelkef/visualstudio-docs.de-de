---
title: "CA1710: Bezeichner sollten ein richtiges Suffix aufweisen | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CA1710"
  - "IdentifiersShouldHaveCorrectSuffix"
helpviewer_keywords: 
  - "IdentifiersShouldHaveCorrectSuffix"
  - "CA1710"
ms.assetid: 2b8e6dce-b4e8-4a66-ba9a-6b79be5bfe8c
caps.latest.revision: 20
caps.handback.revision: 20
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# CA1710: Bezeichner sollten ein richtiges Suffix aufweisen
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|IdentifiersShouldHaveCorrectSuffix|  
|CheckId|CA1710|  
|Kategorie \(Category\)|Microsoft.Naming|  
|Unterbrechende Änderung|Breaking|  
  
## Ursache  
 Ein Bezeichner verfügt nicht über das richtige Suffix.  
  
## Regelbeschreibung  
 Die Namen von Typen, die bestimmte Basistypen erweitern oder bestimmte Schnittstellen implementieren, bzw. von diesen Typen abgeleitete Typen weisen stets ein Suffix auf, das mit dem Basistyp oder der Schnittstelle verknüpft ist.  
  
 Durch Benennungskonventionen erhalten Bibliotheken, die auf die Common Language Runtime abzielen, ein einheitliches Erscheinungsbild.  Dadurch wird der Lernaufwand für neue Softwarebibliotheken verringert. Zudem wird das Kundenvertrauen dahingehend gestärkt, dass die Bibliothek von einem erfahrenen Entwickler für verwalteten Code erstellt wurde.  
  
 In der folgenden Tabelle werden die Basistypen und Schnittstellen aufgeführt, denen Suffixe zugeordnet sind.  
  
|Basistyp\/Schnittstelle|Suffix|  
|-----------------------------|------------|  
|<xref:System.Attribute?displayProperty=fullName>|Attribute|  
|<xref:System.EventArgs?displayProperty=fullName>|EventArgs|  
|<xref:System.Exception?displayProperty=fullName>|Ausnahme|  
|<xref:System.Collections.ICollection?displayProperty=fullName>|Auflistung|  
|<xref:System.Collections.IDictionary?displayProperty=fullName>|Dictionary|  
|<xref:System.Collections.IEnumerable?displayProperty=fullName>|Auflistung|  
|<xref:System.Collections.Queue?displayProperty=fullName>|Collection oder Queue|  
|<xref:System.Collections.Stack?displayProperty=fullName>|Collection oder Stack|  
|<xref:System.Collections.Generic.ICollection%601?displayProperty=fullName>|Auflistung|  
|<xref:System.Collections.Generic.IDictionary%602?displayProperty=fullName>|Dictionary|  
|<xref:System.Data.DataSet?displayProperty=fullName>|DataSet|  
|<xref:System.Data.DataTable?displayProperty=fullName>|Collection oder DataTable|  
|<xref:System.IO.Stream?displayProperty=fullName>|Stream|  
|<xref:System.Security.IPermission?displayProperty=fullName>|Berechtigung|  
|<xref:System.Security.Policy.IMembershipCondition?displayProperty=fullName>|Bedingung|  
|Ein Ereignishandlerdelegat.|EventHandler|  
  
 Für Typen, die <xref:System.Collections.ICollection> implementieren und bei denen es sich um einen verallgemeinerten Datenstrukturtyp handelt, etwa um ein Wörterbuch, einen Stapel oder eine Warteschlange, sind Namen zulässig, aus denen die beabsichtigte Verwendung des Typs hervorgeht.  
  
 Typen, die <xref:System.Collections.ICollection> implementieren und bei denen es sich um eine Auflistung bestimmter Elemente handelt, haben Namen, die mit dem Wort "Collection" enden.  Zum Beispiel hätte eine Auflistung von <xref:System.Collections.Queue>\-Objekten den Namen "QueueCollection".  Das Suffix "Collection" signalisiert, dass die Member der Auflistung mithilfe der `foreach`\-Anweisung \(`For Each` in [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)]\) aufgelistet werden können.  
  
 Typen, die <xref:System.Collections.IDictionary> implementieren, haben Namen, die mit dem Wort "Dictionary" enden, auch wenn der Typ zusätzlich <xref:System.Collections.IEnumerable> oder <xref:System.Collections.ICollection> implementiert.  Durch die Namenskonventionen für die Suffixe "Collection" und "Dictionary" können die Benutzer zwischen den beiden folgenden Enumerationsmustern unterscheiden.  
  
 Typen mit dem Suffix "Collection" weisen folgendes Enumerationsmuster auf:  
  
```  
foreach(SomeType x in SomeCollection) { }  
```  
  
 Typen mit dem Suffix "Dictionary" weisen folgendes Enumerationsmuster auf:  
  
```  
foreach(SomeType x in SomeDictionary.Values) { }  
```  
  
 Ein <xref:System.Data.DataSet>\-Objekt besteht aus einer Auflistung von <xref:System.Data.DataTable>\-Objekten, die sich wiederum u. a. aus Auflistungen von <xref:System.Data.DataColumn?displayProperty=fullName>\-Objekten und <xref:System.Data.DataRow?displayProperty=fullName>\-Objekten zusammensetzen.  Diese Auflistungen implementieren <xref:System.Collections.ICollection> durch die <xref:System.Data.InternalDataCollectionBase?displayProperty=fullName>\-Basisklasse.  
  
## Behandeln von Verstößen  
 Benennen Sie den Typ um, damit er mit dem richtigen Suffix versehen wird.  
  
## Wann sollten Warnungen unterdrückt werden?  
 Eine Warnung zur Verwendung des Suffix "Collection" kann gefahrlos unterdrückt werden, wenn es sich bei dem Typ um eine verallgemeinerte Datenstruktur handelt, die erweitert werden kann oder die einen beliebigen Satz verschiedener Elemente enthält.  In diesem Fall ist es unter Umständen sinnvoll, einen Namen zu verwenden, der aussagekräftige Informationen hinsichtlich der Implementierung, Leistung oder anderer Eigenschaften der Datenstruktur enthält \(z. B. BinaryTree\).  Wenn der Typ eine Auflistung eines bestimmten Typs \(z. B. StringCollection\) darstellt, sollten Sie keine Warnung dieser Regel unterdrücken, da das Suffix angibt, dass der Typ mit einer `foreach`\-Anweisung aufgelistet werden kann.  
  
 Unterdrücken Sie bei anderen Suffixen keine Warnung dieser Regel.  Dank des Suffix geht die beabsichtigte Verwendung aus dem Typnamen hervor.  
  
## Verwandte Regeln  
 [CA1711: Bezeichner sollten kein falsches Suffix aufweisen](../code-quality/ca1711-identifiers-should-not-have-incorrect-suffix.md)  
  
## Siehe auch  
 [Attribute](../Topic/Attributes1.md)   
 [Ereignisse und Delegaten](http://msdn.microsoft.com/de-de/d98fd58b-fa4f-4598-8378-addf4355a115)