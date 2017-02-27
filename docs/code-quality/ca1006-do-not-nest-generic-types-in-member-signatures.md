---
title: "CA1006: Generische Typen in Membersignaturen nicht schachteln | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "DoNotNestGenericTypesInMemberSignatures"
  - "CA1006"
helpviewer_keywords: 
  - "CA1006"
  - "DoNotNestGenericTypesInMemberSignatures"
ms.assetid: dfc867bc-f4af-45d7-b071-db04a248f9fc
caps.latest.revision: 17
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
caps.handback.revision: 17
---
# CA1006: Generische Typen in Membersignaturen nicht schachteln
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|DoNotNestGenericTypesInMemberSignatures|  
|CheckId|CA1006|  
|Kategorie \(Category\)|Microsoft.Design|  
|Unterbrechende Änderung|Breaking|  
  
## Ursache  
 Ein extern sichtbarer Member weist eine Signatur auf, die ein geschachteltes Typargument enthält.  
  
## Regelbeschreibung  
 Ein geschachteltes Typargument ist ein Typargument, das auch ein generischer Typ ist.  Um einen Member aufzurufen, dessen Signatur ein geschachteltes Typargument enthält, muss der Benutzer einen generischen Typ instanziieren und diesen an den Konstruktor eines zweiten generischen Typs übergeben.  Die erforderliche Prozedur und die Syntax sind komplex, und diese Vorgehensweise sollte daher vermieden werden.  
  
## Behandeln von Verstößen  
 Um einen Verstoß gegen diese Regel zu korrigieren, ändern Sie den Entwurf, indem Sie das geschachtelte Typargument entfernen.  
  
## Wann sollten Warnungen unterdrückt werden?  
 Unterdrücken Sie keine Warnung dieser Regel.  Durch die Bereitstellung von Generika in einer einfach zu verstehenden und verwendenden Syntax wird die Zeit, die Sie zum Erlernen benötigen, reduziert und die Übernahmerate neuer Bibliotheken erhöht.  
  
## Beispiel  
 Das folgende Beispiel zeigt eine Methode, die gegen die Regel verstößt, sowie die Syntax, die zum Aufrufen dieser Methode erforderlich ist.  
  
 [!code-vb[FxCop.Design.NestedGenerics#1](../code-quality/codesnippet/VisualBasic/ca1006-do-not-nest-generic-types-in-member-signatures_1.vb)]
 [!code-cs[FxCop.Design.NestedGenerics#1](../code-quality/codesnippet/CSharp/ca1006-do-not-nest-generic-types-in-member-signatures_1.cs)]  
  
## Verwandte Regeln  
 [CA1005: Übermäßige Anzahl von Parametern in generischen Typen vermeiden](../code-quality/ca1005-avoid-excessive-parameters-on-generic-types.md)  
  
 [CA1010: Auflistungen müssen eine generische Schnittstelle implementieren](../code-quality/ca1010-collections-should-implement-generic-interface.md)  
  
 [CA1000: Statische Member nicht in generischen Typen deklarieren](../code-quality/ca1000-do-not-declare-static-members-on-generic-types.md)  
  
 [CA1002: Generische Listen nicht verfügbar machen](../code-quality/ca1002-do-not-expose-generic-lists.md)  
  
 [CA1004: Generische Methoden müssen den Typparameter angeben](../code-quality/ca1004-generic-methods-should-provide-type-parameter.md)  
  
 [CA1003: Generische Ereignishandlerinstanzen verwenden](../code-quality/ca1003-use-generic-event-handler-instances.md)  
  
 [CA1007: Nach Möglichkeit Generika verwenden](../code-quality/ca1007-use-generics-where-appropriate.md)  
  
## Siehe auch  
 [Generika](/dotnet/csharp/programming-guide/generics/index)