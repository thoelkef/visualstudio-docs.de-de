---
title: "CA1007: Nach M&#246;glichkeit Generika verwenden | Microsoft Docs"
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
  - "CA1007"
  - "UseGenericsWhereAppropriate"
helpviewer_keywords: 
  - "CA1007"
  - "UseGenericsWhereAppropriate"
ms.assetid: eab780ea-3b1f-4d32-b15a-5d48da2df46b
caps.latest.revision: 19
caps.handback.revision: 19
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# CA1007: Nach M&#246;glichkeit Generika verwenden
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|UseGenericsWhereAppropriate|  
|CheckId|CA1007|  
|Kategorie \(Category\)|Microsoft.Design|  
|Unterbrechende Änderung|Breaking|  
  
## Ursache  
 Eine extern sichtbare Methode enthält einen Verweisparameter des Typs <xref:System.Object?displayProperty=fullName>, und die enthaltende Assembly hat [!INCLUDE[dnprdnlong](../code-quality/includes/dnprdnlong_md.md)] zum Ziel.  
  
## Regelbeschreibung  
 Ein Verweisparameter ist ein Parameter, der mit dem `ref` \(`ByRef` in [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)]\)\-Schlüsselwort geändert wird.  Der für einen Verweisparameter angegebene Argumenttyp muss genau mit dem Typ des Verweisparameters übereinstimmen.  Damit ein vom Typ des Verweisparameters abgeleiteter Typ verwendet werden kann, muss der Typ zuerst umgewandelt und dann einer Variablen des Verweisparametertyps zugewiesen werden.  Bei Verwendung einer generischen Methode können alle Typen mit gewissen Einschränkungen an die Methode übergeben werden, ohne dass der Typ zuvor in den Typ des Verweisparameters umgewandelt werden muss.  
  
## Behandeln von Verstößen  
 Um einen Verstoß gegen diese Regel zu beheben, verwenden Sie eine generische Methode und ersetzen den <xref:System.Object>\-Parameter durch einen Typparameter.  
  
## Wann sollten Warnungen unterdrückt werden?  
 Unterdrücken Sie keine Warnung dieser Regel.  
  
## Beispiel  
 Im folgenden Beispiel wird eine allgemein verwendbare Austauschroutine veranschaulicht, die sowohl mit nicht generischen als auch mit generischen Methoden implementiert ist.  Beachten Sie, wie effizient die Zeichenfolgen mit der generischen Methode im Vergleich zur nicht generischen Methode ausgetauscht werden.  
  
 [!code-vb[FxCop.Design.UseGenerics#1](../code-quality/codesnippet/VisualBasic/ca1007-use-generics-where-appropriate_1.vb)]
 [!code-cs[FxCop.Design.UseGenerics#1](../code-quality/codesnippet/CSharp/ca1007-use-generics-where-appropriate_1.cs)]  
  
## Verwandte Regeln  
 [CA1005: Übermäßige Anzahl von Parametern in generischen Typen vermeiden](../code-quality/ca1005-avoid-excessive-parameters-on-generic-types.md)  
  
 [CA1010: Auflistungen müssen eine generische Schnittstelle implementieren](../code-quality/ca1010-collections-should-implement-generic-interface.md)  
  
 [CA1000: Statische Member nicht in generischen Typen deklarieren](../code-quality/ca1000-do-not-declare-static-members-on-generic-types.md)  
  
 [CA1002: Generische Listen nicht verfügbar machen](../code-quality/ca1002-do-not-expose-generic-lists.md)  
  
 [CA1006: Generische Typen in Membersignaturen nicht schachteln](../code-quality/ca1006-do-not-nest-generic-types-in-member-signatures.md)  
  
 [CA1004: Generische Methoden müssen den Typparameter angeben](../code-quality/ca1004-generic-methods-should-provide-type-parameter.md)  
  
 [CA1003: Generische Ereignishandlerinstanzen verwenden](../code-quality/ca1003-use-generic-event-handler-instances.md)  
  
## Siehe auch  
 [Generika](/dotnet/csharp/programming-guide/generics/index)