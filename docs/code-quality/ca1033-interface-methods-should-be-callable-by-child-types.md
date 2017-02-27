---
title: "CA1033: Schnittstellenmethoden sollten von untergeordneten Typen aufgerufen werden k&#246;nnen | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "InterfaceMethodsShouldBeCallableByChildTypes"
  - "CA1033"
helpviewer_keywords: 
  - "CA1033"
  - "InterfaceMethodsShouldBeCallableByChildTypes"
ms.assetid: 9f171497-a5e3-4769-a77b-7aed755b2662
caps.latest.revision: 17
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
caps.handback.revision: 17
---
# CA1033: Schnittstellenmethoden sollten von untergeordneten Typen aufgerufen werden k&#246;nnen
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|InterfaceMethodsShouldBeCallableByChildTypes|  
|CheckId|CA1033|  
|Kategorie \(Category\)|Microsoft.Design|  
|Unterbrechende Änderung|Nicht unterbrechend|  
  
## Ursache  
 Ein unversiegelter, extern sichtbarer Typ gibt eine explizite Methodenimplementierung einer öffentlichen Schnittstelle an und gibt keine alternative extern sichtbare Methode mit dem gleichen Namen an.  
  
## Regelbeschreibung  
 Ziehen Sie einen Basistyp in Erwägung, der eine öffentliche Schnittstellenmethode explizit implementiert.  Ein Typ, der vom Basistyp abgeleitet wird, kann auf die geerbte Schnittstellenmethode nur durch einen Verweis auf die aktuelle Instanz \(`this` in C\#\) zugreifen, die in die Schnittstelle umgewandelt wird.  Wenn der abgeleitete Typ die geerbte Schnittstellenmethode erneut \(explizit\) implementiert, kann auf die Basisimplementierung nicht mehr zugegriffen werden.  Beim Aufruf über den aktuellen Instanzverweis wird die abgeleitete Implementierung aufgerufen. Dies führt zur Rekursion und schließlich zu einem Stapelüberlauf.  
  
 Von dieser Regel wird bei einer expliziten Implementierung von <xref:System.IDisposable.Dispose%2A?displayProperty=fullName> kein Verstoß gemeldet, wenn eine extern sichtbare `Close()`\-Methode oder eine `System.IDisposable.Dispose(Boolean)`\-Methode angegeben wird.  
  
## Behandeln von Verstößen  
 Um einen Verstoß gegen diese Regel zu beheben, implementieren Sie eine neue Methode, die die gleiche Funktionalität verfügbar macht und für abgeleitete Typen sichtbar ist, oder verwenden Sie eine nicht explizite Implementierung.  Wenn eine Unterbrechende Änderung zulässig ist, haben Sie auch die Möglichkeit, den Typ als versiegelten Typ zu definieren.  
  
## Wann sollten Warnungen unterdrückt werden?  
 Eine Warnung dieser Regel kann gefahrlos unterdrückt werden, wenn eine extern sichtbare Methode angegeben wird, die die gleiche Funktionalität hat, aber einen anderen Namen aufweist als die explizit implementierte Methode.  
  
## Beispiel  
 Das folgende Beispiel zeigt einen Typ \(`ViolatingBase`\) der gegen die Regel verstößt, und einen Typ, `FixedBase`, der eine Korrektur des Verstoßes aufweist.  
  
 [!code-cs[FxCop.Design.ExplicitMethodImplementations#1](../code-quality/codesnippet/CSharp/ca1033-interface-methods-should-be-callable-by-child-types_1.cs)]  
  
## Siehe auch  
 [Schnittstellen](/dotnet/csharp/programming-guide/interfaces/index)