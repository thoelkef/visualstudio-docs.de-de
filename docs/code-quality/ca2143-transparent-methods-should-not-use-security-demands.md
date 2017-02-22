---
title: "CA2143: Transparente Methoden d&#252;rfen keine Sicherheitsanforderungen verwenden | Microsoft Docs"
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
  - "CA2143"
ms.assetid: 5d3923d7-cf40-4512-bc5c-0db0e0d6e25a
caps.latest.revision: 12
caps.handback.revision: 12
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# CA2143: Transparente Methoden d&#252;rfen keine Sicherheitsanforderungen verwenden
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|TransparentMethodsShouldNotDemand|  
|CheckId|CA2143|  
|Kategorie \(Category\)|Microsoft.Security|  
|Unterbrechende Änderung|Breaking|  
  
## Ursache  
 Ein transparenter Typ oder eine Methode wird deklarativ mit einer <xref:System.Security.Permissions.SecurityAction?displayProperty=fullName>`.Demand`\-Forderung markiert, oder die Methode ruft die <xref:System.Security.CodeAccessPermission.Demand%2A?displayProperty=fullName>\-Methode auf.  
  
## Regelbeschreibung  
 Sicherheitstransparenter Code sollte nicht für das Überprüfen der Sicherheit einer Operation zuständig sein und sollte daher keine Berechtigungen fordern.  Sicherheitstransparenter Code sollte mithilfe von vollständigen Anforderungen Sicherheitsentscheidungen fällen, und sicherheitskritischer Code sollte für die vollständige Anforderung nicht auf transparentem Code beruhen.  Jeder Code, in dem Sicherheitsüberprüfungen, z. B. Sicherheitsanforderungen, ausgeführt werden, sollte stattdessen sicherheitskritisch sein.  
  
## Behandeln von Verstößen  
 Um einen Verstoß gegen diese Regel zu beheben, markieren Sie im Allgemeinen die Methode oder den Typ mit dem <xref:System.Security.SecuritySafeCriticalAttribute>\-Attribut:  Sie können auch die Forderung entfernen.  
  
## Wann sollten Warnungen unterdrückt werden?  
 Unterdrücken Sie keine Warnung dieser Regel.  
  
## Beispiel  
 Die Regel wird im folgenden Code abgelegt, da eine transparente Methode eine deklarative Sicherheitsforderung macht.  
  
 [!code-cs[FxCop.Security.CA2143.TransparentMethodsShouldNotDemand#1](../code-quality/codesnippet/CSharp/ca2143-transparent-methods-should-not-use-security-demands_1.cs)]  
  
## Siehe auch  
 [CA2142: Transparenter Code darf nicht mit LinkDemands geschützt werden](../code-quality/ca2142-transparent-code-should-not-be-protected-with-linkdemands.md)