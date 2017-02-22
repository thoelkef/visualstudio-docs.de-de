---
title: "CA1004: Generische Methoden m&#252;ssen den Typparameter angeben | Microsoft Docs"
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
  - "CA1004"
  - "GenericMethodsShouldProvideTypeParameter"
helpviewer_keywords: 
  - "CA1004"
  - "GenericMethodsShouldProvideTypeParameter"
ms.assetid: 38755f6a-fb45-4bf2-932e-0354ad826499
caps.latest.revision: 17
caps.handback.revision: 17
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# CA1004: Generische Methoden m&#252;ssen den Typparameter angeben
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|GenericMethodsShouldProvideTypeParameter|  
|CheckId|CA1004|  
|Kategorie \(Category\)|Microsoft.Design|  
|Unterbrechende Änderung|Breaking|  
  
## Ursache  
 Die Parametersignatur einer extern sichtbaren generischen Methode enthält keine Typen, die allen Typparametern der Methode entsprechen.  
  
## Regelbeschreibung  
 Mithilfe eines Rückschlusses wird das Typargument einer generischen Methode nach dem Typ des an die Methode übergebenen Arguments festgelegt, anstatt nach der expliziten Spezifikation des Typarguments.  Um den Rückschluss zu aktivieren, muss die Parametersignatur einer generischen Methode einen Parameter einschließen, der vom selben Typ wie der Typparameter für die Methode ist.  In diesem Fall muss das Typargument nicht angegeben werden.  Wenn für alle Typparameter der Rückschluss verwendet wird, sind die Syntaxen zum Aufrufen von generischen und nicht generischen Instanzenmethoden identisch.  Dies vereinfacht die Verwendbarkeit generischer Methoden.  
  
## Behandeln von Verstößen  
 Um einen Verstoß gegen diese Regel zu beheben, ändern Sie das Design dahingehend, dass die Parametersignatur den gleichen Typ für jeden Typparameter der Methode enthält.  
  
## Wann sollten Warnungen unterdrückt werden?  
 Unterdrücken Sie keine Warnung dieser Regel.  Durch die Bereitstellung von Generika in einer einfach zu verstehenden und verwendenden Syntax wird die Zeit, die Sie zum Erlernen benötigen, reduziert und die Übernahmerate neuer Bibliotheken erhöht.  
  
## Beispiel  
 Im folgenden Beispiel wird die Syntax zum Aufrufen von zwei generischen Methoden veranschaulicht.  Das Typargument für `InferredTypeArgument` wird abgeleitet, und das Typargument für `NotInferredTypeArgument` muss explizit angegeben werden.  
  
 [!code-vb[FxCop.Design.Inference#1](../code-quality/codesnippet/VisualBasic/ca1004-generic-methods-should-provide-type-parameter_1.vb)]
 [!code-cs[FxCop.Design.Inference#1](../code-quality/codesnippet/CSharp/ca1004-generic-methods-should-provide-type-parameter_1.cs)]  
  
## Verwandte Regeln  
 [CA1005: Übermäßige Anzahl von Parametern in generischen Typen vermeiden](../code-quality/ca1005-avoid-excessive-parameters-on-generic-types.md)  
  
 [CA1010: Auflistungen müssen eine generische Schnittstelle implementieren](../code-quality/ca1010-collections-should-implement-generic-interface.md)  
  
 [CA1000: Statische Member nicht in generischen Typen deklarieren](../code-quality/ca1000-do-not-declare-static-members-on-generic-types.md)  
  
 [CA1002: Generische Listen nicht verfügbar machen](../code-quality/ca1002-do-not-expose-generic-lists.md)  
  
 [CA1006: Generische Typen in Membersignaturen nicht schachteln](../code-quality/ca1006-do-not-nest-generic-types-in-member-signatures.md)  
  
 [CA1003: Generische Ereignishandlerinstanzen verwenden](../code-quality/ca1003-use-generic-event-handler-instances.md)  
  
 [CA1007: Nach Möglichkeit Generika verwenden](../code-quality/ca1007-use-generics-where-appropriate.md)  
  
## Siehe auch  
 [Generika](/dotnet/csharp/programming-guide/generics/index)