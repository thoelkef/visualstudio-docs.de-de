---
title: "CA1064: Ausnahmen sollten &#246;ffentlich sein | Microsoft Docs"
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
  - "CA1064"
  - "ExceptionsShouldBePublic"
helpviewer_keywords: 
  - "CA1064"
  - "ExceptionsShouldBePublic"
ms.assetid: 83eb224c-2456-4368-acf4-3b3378e67759
caps.latest.revision: 11
caps.handback.revision: 11
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# CA1064: Ausnahmen sollten &#246;ffentlich sein
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|ExceptionsShouldBePublic|  
|CheckId|CA1064|  
|Kategorie \(Category\)|Microsoft.Design|  
|Unterbrechende Änderung|Nicht unterbrechend|  
  
## Ursache  
 Eine nicht öffentliche Ausnahme wird direkt von <xref:System.Exception>, <xref:System.SystemException> oder <xref:System.ApplicationException> abgeleitet.  
  
## Regelbeschreibung  
 Eine interne Ausnahme ist nur innerhalb ihres eigenen internen Bereichs sichtbar.  Nachdem die Ausnahme den internen Bereich verlassen hat, kann nur die Basisausnahme zum Abfangen der Ausnahme verwendet werden.  Wenn die interne Ausnahme von <xref:System.Exception>, <xref:System.SystemException> oder <xref:System.ApplicationException> geerbt wurde, verfügt der externe Code nicht über genügend Informationen zur Behandlung der Ausnahme.  
  
 Wenn im Code jedoch eine öffentliche Ausnahme enthalten ist, die später als Basis für eine interne Ausnahme verwendet wird, kann zweifellos davon ausgegangen werden, dass der weiter außen liegende Code in der Lage sein wird, die Basisausnahme auf intelligente Weise zu behandeln.  Die öffentliche Ausnahme weist mehr als die von T:System.Exception, T:System.SystemException oder T:System.ApplicationException bereitgestellten Informationen auf.  
  
## Behandeln von Verstößen  
 Wandeln Sie die Ausnahme in eine öffentliche Ausnahme um, oder lassen Sie die interne Ausnahme von einer öffentlichen Ausnahme außer <xref:System.Exception>, <xref:System.SystemException> oder <xref:System.ApplicationException> ableiten.  
  
## Wann sollten Warnungen unterdrückt werden?  
 Unterdrücken Sie eine Meldung dieser Regel, wenn Sie in allen Fällen sicher sind, dass die private Ausnahme innerhalb ihres eigenen internen Bereichs abgefangen wird.  
  
## Beispiel  
 Diese Regel wird bei der ersten Beispielmethode ausgelöst \(FirstCustomException\), da die Ausnahmeklasse direkt von der Ausnahme abgeleitet wird und intern ist.  Die Regel wird nicht in der SecondCustomException\-Klasse ausgelöst, da die Klasse ungeachtet der unmittelbaren Ableitung von der Ausnahme als öffentlich deklariert wird.  Die dritte Klasse löst ebenfalls nicht die Regel aus, da sie nicht direkt von <xref:System.Exception?displayProperty=fullName>, <xref:System.SystemException?displayProperty=fullName>, oder <xref:System.ApplicationException?displayProperty=fullName> abgeleitet wird.  
  
 [!code-cs[FxCop.Design.ExceptionsShouldBePublic.CA1064#1](../code-quality/codesnippet/CSharp/ca1064-exceptions-should-be-public_1.cs)]