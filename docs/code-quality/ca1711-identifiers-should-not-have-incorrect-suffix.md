---
title: "CA1711: Bezeichner sollten kein falsches Suffix aufweisen | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CA1711"
  - "IdentifiersShouldNotHaveIncorrectSuffix"
helpviewer_keywords: 
  - "CA1711"
  - "IdentifiersShouldNotHaveIncorrectSuffix"
ms.assetid: a63359ab-386d-44ae-b381-ee3a983aca29
caps.latest.revision: 18
caps.handback.revision: 18
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# CA1711: Bezeichner sollten kein falsches Suffix aufweisen
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|IdentifiersShouldNotHaveIncorrectSuffix|  
|CheckId|CA1711|  
|Kategorie \(Category\)|Microsoft.Naming|  
|Unterbrechende Änderung|Breaking|  
  
## Ursache  
 Ein Bezeichner weist ein falsches Suffix auf.  
  
## Regelbeschreibung  
 Nur die Namen von Typen, die bestimmte Basistypen erweitern oder bestimmte Schnittstellen bzw. Typen implementieren, die von diesen Typen abgeleitet werden, sollten stets mit bestimmten reservierten Suffixen enden.  Für andere Typnamen sollten diese reservierten Suffixe nicht verwendet werden.  
  
 In der folgenden Tabelle werden die reservierten Suffixe sowie die Basistypen und die Schnittstellen aufgeführt, denen die Suffixe zugeordnet sind.  
  
|Suffix|Basistyp\/Schnittstelle|  
|------------|-----------------------------|  
|Attribute|<xref:System.Attribute?displayProperty=fullName>|  
|Auflistung|<xref:System.Collections.ICollection?displayProperty=fullName><br /><br /> <xref:System.Collections.IEnumerable?displayProperty=fullName><br /><br /> <xref:System.Collections.Queue?displayProperty=fullName><br /><br /> <xref:System.Collections.Stack?displayProperty=fullName><br /><br /> <xref:System.Collections.Generic.ICollection%601?displayProperty=fullName><br /><br /> <xref:System.Data.DataSet?displayProperty=fullName><br /><br /> <xref:System.Data.DataTable?displayProperty=fullName>|  
|Dictionary|<xref:System.Collections.IDictionary?displayProperty=fullName><br /><br /> <xref:System.Collections.Generic.IDictionary%602?displayProperty=fullName>|  
|EventArgs|<xref:System.EventArgs?displayProperty=fullName>|  
|EventHandler|Ein Ereignishandlerdelegat.|  
|Ausnahme|<xref:System.Exception?displayProperty=fullName>|  
|Berechtigung|<xref:System.Security.IPermission?displayProperty=fullName>|  
|Warteschlange|<xref:System.Collections.Queue?displayProperty=fullName>|  
|Stapel|<xref:System.Collections.Stack?displayProperty=fullName>|  
|Stream|<xref:System.IO.Stream?displayProperty=fullName>|  
  
 Außerdem sollten die folgenden Suffixe **nicht** verwendet werden:  
  
-   Delegate  
  
-   Enum  
  
-   Impl – Verwenden Sie stattdessen 'Core'.  
  
-   "Ex" oder ein ähnliches Suffix zur Unterscheidung von einer früheren Version desselben Typs  
  
 Durch Benennungskonventionen erhalten Bibliotheken, die auf die Common Language Runtime abzielen, ein einheitliches Erscheinungsbild.  Dadurch wird der Lernaufwand für neue Softwarebibliotheken verringert. Zudem wird das Kundenvertrauen dahingehend gestärkt, dass die Bibliothek von einem erfahrenen Entwickler für verwalteten Code erstellt wurde.  
  
## Behandeln von Verstößen  
 Entfernen Sie das Suffix aus dem Typnamen.  
  
## Wann sollten Warnungen unterdrückt werden?  
 Unterdrücken Sie keine Warnung dieser Regel, es sei denn, das Suffix hat eine eindeutige Bedeutung in der Anwendungsdomäne.  
  
## Verwandte Regeln  
 [CA1710: Bezeichner sollten ein richtiges Suffix aufweisen](../code-quality/ca1710-identifiers-should-have-correct-suffix.md)  
  
## Siehe auch  
 [Attribute](../Topic/Attributes1.md)   
 [Ereignisse und Delegaten](http://msdn.microsoft.com/de-de/d98fd58b-fa4f-4598-8378-addf4355a115)