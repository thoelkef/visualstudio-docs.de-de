---
title: "CA1000: Statische Member nicht in generischen Typen deklarieren | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CA1000"
  - "DoNotDeclareStaticMembersOnGenericTypes"
helpviewer_keywords: 
  - "CA1000"
  - "DoNotDeclareStaticMembersOnGenericTypes"
ms.assetid: 5c0da594-f8d0-4f40-953d-56bf7fbd2087
caps.latest.revision: 17
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
caps.handback.revision: 17
---
# CA1000: Statische Member nicht in generischen Typen deklarieren
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|DoNotDeclareStaticMembersOnGenericTypes|  
|CheckId|CA1000|  
|Kategorie \(Category\)|Microsoft.Design|  
|Unterbrechende Änderung|Breaking|  
  
## Ursache  
 Ein extern sichtbarer generischer Typ enthält einen `static`\-Member \(`Shared` in Visual Basic\).  
  
## Regelbeschreibung  
 Wenn ein `static`\-Member eines generischen Typs aufgerufen wird, muss das Typargument für den Typ angegeben werden.  Wenn ein generischer Instanzmember, der keine Unterstützung für Rückschlüsse bietet, aufgerufen wird, muss das Typargument für den Member angegeben werden.  Die Syntax zum Angeben des Typarguments in diesen beiden Fällen ist unterschiedlich und kann schnell verwechselt werden, wie die folgenden Aufrufe verdeutlichen:  
  
```vb  
' Shared method in a generic type.  
GenericType(Of Integer).SharedMethod()  
  
' Generic instance method that does not support inference.  
someObject.GenericMethod(Of Integer)()  
```  
  
```c#  
// Static method in a generic type.  
GenericType<int>.StaticMethod();  
  
// Generic instance method that does not support inference.  
someObject.GenericMethod<int>();  
```  
  
 Im Prinzip sollten beide vorherigen Deklarationen vermieden werden, sodass das Typargument nicht angegeben werden muss, wenn der Member aufgerufen wird.  Daraus ergibt sich eine Syntax zum Aufrufen von Membern in Generika, die sich nicht von der Syntax für nicht generische Typen unterscheidet.  Weitere Informationen finden Sie unter [CA1004: Generische Methoden müssen den Typparameter angeben](../code-quality/ca1004-generic-methods-should-provide-type-parameter.md).  
  
## Behandeln von Verstößen  
 Um einen Verstoß gegen diese Regel zu beheben, entfernen Sie den statischen Member, oder ändern Sie ihn in einen Instanzmember.  
  
## Wann sollten Warnungen unterdrückt werden?  
 Unterdrücken Sie keine Warnung dieser Regel.  Durch die Bereitstellung von Generika in einer einfach zu verstehenden und verwendenden Syntax wird die Zeit, die Sie zum Erlernen benötigen, reduziert und die Übernahmerate neuer Bibliotheken erhöht.  
  
## Verwandte Regeln  
 [CA1005: Übermäßige Anzahl von Parametern in generischen Typen vermeiden](../code-quality/ca1005-avoid-excessive-parameters-on-generic-types.md)  
  
 [CA1010: Auflistungen müssen eine generische Schnittstelle implementieren](../code-quality/ca1010-collections-should-implement-generic-interface.md)  
  
 [CA1002: Generische Listen nicht verfügbar machen](../code-quality/ca1002-do-not-expose-generic-lists.md)  
  
 [CA1006: Generische Typen in Membersignaturen nicht schachteln](../code-quality/ca1006-do-not-nest-generic-types-in-member-signatures.md)  
  
 [CA1004: Generische Methoden müssen den Typparameter angeben](../code-quality/ca1004-generic-methods-should-provide-type-parameter.md)  
  
 [CA1003: Generische Ereignishandlerinstanzen verwenden](../code-quality/ca1003-use-generic-event-handler-instances.md)  
  
 [CA1007: Nach Möglichkeit Generika verwenden](../code-quality/ca1007-use-generics-where-appropriate.md)  
  
## Siehe auch  
 [Generika](/dotnet/csharp/programming-guide/generics/index)