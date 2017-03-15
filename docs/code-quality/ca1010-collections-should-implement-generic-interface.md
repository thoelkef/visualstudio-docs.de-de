---
title: "CA1010: Auflistungen m&#252;ssen eine generische Schnittstelle implementieren | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CA1010"
  - "CollectionsShouldImplementGenericInterface"
helpviewer_keywords: 
  - "CA1010"
  - "CollectionsShouldImplementGenericInterface"
ms.assetid: c7d7126f-fa70-40be-8f93-3243e1760dc5
caps.latest.revision: 24
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
caps.handback.revision: 24
---
# CA1010: Auflistungen m&#252;ssen eine generische Schnittstelle implementieren
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|CollectionsShouldImplementGenericInterface|  
|CheckId|CA1010|  
|Kategorie \(Category\)|Microsoft.Design|  
|Unterbrechende Änderung|Nicht unterbrechend|  
  
## Ursache  
 Ein extern sichtbarer Typ implementiert die <xref:System.Collections.IEnumerable?displayProperty=fullName>\-Schnittstelle, jedoch nicht die <xref:System.Collections.Generic.IEnumerable%601?displayProperty=fullName>\-Schnittstelle, und das Ziel der enthaltenden Assembly ist [!INCLUDE[dnprdnlong](../code-quality/includes/dnprdnlong_md.md)].  Bei dieser Regel werden Typen ignoriert, die <xref:System.Collections.IDictionary?displayProperty=fullName> implementieren.  
  
## Regelbeschreibung  
 Um die Verwendbarkeit einer Auflistung zu erweitern, implementieren Sie eine der generischen Auflistungsschnittstellen.  Anschließend kann die Auflistung verwendet werden, um generische Auflistungstypen wie die folgenden aufzufüllen:  
  
-   <xref:System.Collections.Generic.List%601?displayProperty=fullName>  
  
-   <xref:System.Collections.Generic.Queue%601?displayProperty=fullName>  
  
-   <xref:System.Collections.Generic.Stack%601?displayProperty=fullName>  
  
## Behandeln von Verstößen  
 Um einen Verstoß gegen diese Regel zu korrigieren, implementieren Sie eine der folgenden generischen Auflistungsschnittstellen:  
  
-   <xref:System.Collections.Generic.IEnumerable%601?displayProperty=fullName>  
  
-   <xref:System.Collections.Generic.ICollection%601?displayProperty=fullName>  
  
-   <xref:System.Collections.Generic.IList%601?displayProperty=fullName>  
  
## Wann sollten Warnungen unterdrückt werden?  
 Warnungen dieser Regel können gefahrlos unterdrückt werden; allerdings wird damit die Verwendbarkeit der Auflistung eingeschränkt.  
  
## Beispiel für einen Verstoß  
  
### **Beschreibung**  
 Im folgenden Beispiel wird eine Klasse \(Referenztyp\) veranschaulicht, die von der nicht generischen `CollectionBase`\-Klasse abgeleitet wird, die gegen diese Regel verstößt.  
  
### Code  
 [!code-cs[FxCop.Design.CollectionsGenericViolation#1](../code-quality/codesnippet/CSharp/ca1010-collections-should-implement-generic-interface_1.cs)]  
  
### Kommentare  
 Um einen Verstoß gegen diese Regel zu beheben, sollten Sie entweder die generischen Schnittstellen implementieren oder die Basisklasse in einen Typ ändern, durch den sowohl generische als auch nicht generische Schnittstellen bereits implementiert werden, z. B. die `Collection<T>`\-Klasse.  
  
## Korrektur durch Änderung der Basisklasse  
  
### **Beschreibung**  
 Im folgenden Beispiel wird der Verstoß korrigiert, indem die Basisklasse der Auflistung von der nicht generischen `CollectionBase`\-Klasse in die generische `Collection<T>`\-Klasse \(`Collection(Of T)` in [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)]\) geändert wird.  
  
### Code  
 [!code-cs[FxCop.Design.CollectionsGenericBase#1](../code-quality/codesnippet/CSharp/ca1010-collections-should-implement-generic-interface_2.cs)]  
  
### Kommentare  
 Wenn die Basisklasse einer bereits freigegebenen Klasse geändert wird, gilt dies als unterbrechende Änderung vorhandener Consumer.  
  
## Korrektur durch Schnittstellenimplementierung  
  
### **Beschreibung**  
 Im folgenden Beispiel wird der Verstoß korrigiert, indem folgende generische Schnittstellen implementiert werden: `IEnumerable<T>`, `ICollection<T>` und `IList<T>` \(`IEnumerable(Of T)`, `ICollection(Of T)` und `IList(Of T)` in [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)]\).  
  
### Code  
 [!code-cs[FxCop.Design.CollectionsGenericInterface#1](../code-quality/codesnippet/CSharp/ca1010-collections-should-implement-generic-interface_3.cs)]  
  
## Verwandte Regeln  
 [CA1005: Übermäßige Anzahl von Parametern in generischen Typen vermeiden](../code-quality/ca1005-avoid-excessive-parameters-on-generic-types.md)  
  
 [CA1000: Statische Member nicht in generischen Typen deklarieren](../code-quality/ca1000-do-not-declare-static-members-on-generic-types.md)  
  
 [CA1002: Generische Listen nicht verfügbar machen](../code-quality/ca1002-do-not-expose-generic-lists.md)  
  
 [CA1006: Generische Typen in Membersignaturen nicht schachteln](../code-quality/ca1006-do-not-nest-generic-types-in-member-signatures.md)  
  
 [CA1004: Generische Methoden müssen den Typparameter angeben](../code-quality/ca1004-generic-methods-should-provide-type-parameter.md)  
  
 [CA1003: Generische Ereignishandlerinstanzen verwenden](../code-quality/ca1003-use-generic-event-handler-instances.md)  
  
 [CA1007: Nach Möglichkeit Generika verwenden](../code-quality/ca1007-use-generics-where-appropriate.md)  
  
## Siehe auch  
 [Generika](/dotnet/csharp/programming-guide/generics/index)