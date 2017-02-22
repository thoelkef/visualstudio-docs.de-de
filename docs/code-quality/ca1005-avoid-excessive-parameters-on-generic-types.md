---
title: "CA1005: &#220;berm&#228;&#223;ige Anzahl von Parametern in generischen Typen vermeiden | Microsoft Docs"
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
  - "AvoidExcessiveParametersOnGenericTypes"
  - "CA1005"
helpviewer_keywords: 
  - "AvoidExcessiveParametersOnGenericTypes"
  - "CA1005"
ms.assetid: 372b2f28-5c59-4815-9753-6c65b2bb3589
caps.latest.revision: 18
caps.handback.revision: 18
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# CA1005: &#220;berm&#228;&#223;ige Anzahl von Parametern in generischen Typen vermeiden
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|AvoidExcessiveParametersOnGenericTypes|  
|CheckId|CA1005|  
|Kategorie \(Category\)|Microsoft.Design|  
|Unterbrechende Änderung|Breaking|  
  
## Ursache  
 Ein extern sichtbarer generischer Typ hat mehr als zwei Typparameter.  
  
## Regelbeschreibung  
 Je mehr Typparameter ein generischer Typ enthält, desto schwieriger ist es, zu wissen und zu behalten, was die einzelnen Typparameter darstellen.  In der Regel ist dies offensichtlich bei einem Typparameter, wie in `List<T>`, und in bestimmten Fällen auch bei zwei Typparametern, wie in `Dictionary<TKey, TValue>`.  Wenn mehr als zwei Typparameter vorhanden sind, wird die Schwierigkeit für die meisten Benutzer zu groß \(z. B. `TooManyTypeParameters<T, K, V>` in C\# oder `TooManyTypeParameters(Of T, K, V)` in [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)]\).  
  
## Behandeln von Verstößen  
 Um einen Verstoß gegen diese Regel zu beheben, ändern Sie das Design dahingehend, dass nicht mehr als zwei Typparameter verwendet werden.  
  
## Wann sollten Warnungen unterdrückt werden?  
 Unterdrücken Sie keine Warnung dieser Regel, es sei denn, für das Design sind unbedingt mehr als zwei Typparameter erforderlich.  Durch die Bereitstellung von Generika in einer einfach zu verstehenden und verwendenden Syntax wird die Zeit, die Sie zum Erlernen benötigen, reduziert und die Übernahmerate neuer Bibliotheken erhöht.  
  
## Verwandte Regeln  
 [CA1010: Auflistungen müssen eine generische Schnittstelle implementieren](../code-quality/ca1010-collections-should-implement-generic-interface.md)  
  
 [CA1000: Statische Member nicht in generischen Typen deklarieren](../code-quality/ca1000-do-not-declare-static-members-on-generic-types.md)  
  
 [CA1002: Generische Listen nicht verfügbar machen](../code-quality/ca1002-do-not-expose-generic-lists.md)  
  
 [CA1006: Generische Typen in Membersignaturen nicht schachteln](../code-quality/ca1006-do-not-nest-generic-types-in-member-signatures.md)  
  
 [CA1004: Generische Methoden müssen den Typparameter angeben](../code-quality/ca1004-generic-methods-should-provide-type-parameter.md)  
  
 [CA1003: Generische Ereignishandlerinstanzen verwenden](../code-quality/ca1003-use-generic-event-handler-instances.md)  
  
 [CA1007: Nach Möglichkeit Generika verwenden](../code-quality/ca1007-use-generics-where-appropriate.md)  
  
## Siehe auch  
 [Generika](/dotnet/csharp/programming-guide/generics/index)