---
title: "CA1002: Generische Listen nicht verf&#252;gbar machen | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "DoNotExposeGenericLists"
  - "CA1002"
helpviewer_keywords: 
  - "CA1002"
  - "DoNotExposeGenericLists"
ms.assetid: 5caac810-1a79-47df-a27b-c46c5040bf34
caps.latest.revision: 20
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
caps.handback.revision: 20
---
# CA1002: Generische Listen nicht verf&#252;gbar machen
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|DoNotExposeGenericLists|  
|CheckId|CA1002|  
|Kategorie \(Category\)|Microsoft.Design|  
|Unterbrechende Änderung|Breaking|  
  
## Ursache  
 Ein Typ enthält einen extern sichtbaren Member, der ein <xref:System.Collections.Generic.List%601?displayProperty=fullName>\-Typ ist, einen <xref:System.Collections.Generic.List%601?displayProperty=fullName>\-Typ zurückgibt oder dessen Signatur einen <xref:System.Collections.Generic.List%601?displayProperty=fullName>\-Parameter enthält.  
  
## Regelbeschreibung  
 <xref:System.Collections.Generic.List%601?displayProperty=fullName> ist eine generische Auflistung, die für eine möglichst hohe Leistung und nicht für Vererbung optimiert wurde.  <xref:System.Collections.Generic.List%601?displayProperty=fullName> enthält keine virtuellen Member, die Änderungen am Verhalten einer geerbten Klasse erleichtern würden.  Die folgenden generischen Auflistungen wurden mit Blick auf Vererbung entworfen und sollten anstelle von <xref:System.Collections.Generic.List%601?displayProperty=fullName> verfügbar gemacht werden.  
  
-   <xref:System.Collections.ObjectModel.Collection%601?displayProperty=fullName>  
  
-   <xref:System.Collections.ObjectModel.ReadOnlyCollection%601?displayProperty=fullName>  
  
-   <xref:System.Collections.ObjectModel.KeyedCollection%602?displayProperty=fullName>  
  
## Behandeln von Verstößen  
 Um einen Verstoß gegen diese Regel zu beheben, ändern Sie den <xref:System.Collections.Generic.List%601?displayProperty=fullName>\-Typ in eine der mit Blick auf Vererbung entworfenen generischen Auflistungen.  
  
## Wann sollten Warnungen unterdrückt werden?  
 Unterdrücken Sie keine Warnung dieser Regel, es sei denn, die Assembly, die diese Warnung auslöst, ist nicht als wiederverwendbare Bibliothek bestimmt.  Es wäre z. B. sicher, die Warnung in einer leistungsoptimierten Anwendung zu unterdrücken, in der durch die Verwendung generischer Listen Leistungsvorteile erzielt werden können.  
  
## Verwandte Regeln  
 [CA1005: Übermäßige Anzahl von Parametern in generischen Typen vermeiden](../code-quality/ca1005-avoid-excessive-parameters-on-generic-types.md)  
  
 [CA1010: Auflistungen müssen eine generische Schnittstelle implementieren](../code-quality/ca1010-collections-should-implement-generic-interface.md)  
  
 [CA1000: Statische Member nicht in generischen Typen deklarieren](../code-quality/ca1000-do-not-declare-static-members-on-generic-types.md)  
  
 [CA1006: Generische Typen in Membersignaturen nicht schachteln](../code-quality/ca1006-do-not-nest-generic-types-in-member-signatures.md)  
  
 [CA1004: Generische Methoden müssen den Typparameter angeben](../code-quality/ca1004-generic-methods-should-provide-type-parameter.md)  
  
 [CA1003: Generische Ereignishandlerinstanzen verwenden](../code-quality/ca1003-use-generic-event-handler-instances.md)  
  
 [CA1007: Nach Möglichkeit Generika verwenden](../code-quality/ca1007-use-generics-where-appropriate.md)  
  
## Siehe auch  
 [Generika](/dotnet/csharp/programming-guide/generics/index)