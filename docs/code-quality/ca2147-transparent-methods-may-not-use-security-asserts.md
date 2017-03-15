---
title: "CA2147: Transparente Methoden d&#252;rfen keine Sicherheitsassertionen verwenden | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "SecurityTransparentCodeShouldNotAssert"
  - "CA2147"
  - "CA2128"
helpviewer_keywords: 
  - "CA2128"
  - "SecurityTransparentCodeShouldNotAssert"
ms.assetid: 5d31e940-e599-4b23-9b28-1c336f8d910e
caps.latest.revision: 18
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
caps.handback.revision: 18
---
# CA2147: Transparente Methoden d&#252;rfen keine Sicherheitsassertionen verwenden
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|SecurityTransparentCodeShouldNotAssert|  
|CheckId|CA2147|  
|Kategorie \(Category\)|Microsoft.Security|  
|Unterbrechende Änderung|Breaking|  
  
## Ursache  
 Code, der als <xref:System.Security.SecurityTransparentAttribute> markiert wurde, verfügt nicht über ausreichende Berechtigungen für die Verwendung von Assertionen.  
  
## Regelbeschreibung  
 Durch diese Regel werden alle Methoden und Typen in einer Assembly analysiert, die entweder zu 100 % aus transparentem Code oder aus einer Kombination aus transparentem\/relevantem Code besteht. Anschließend werden alle deklarativen oder imperativen Verwendungen von <xref:System.Security.CodeAccessPermission.Assert%2A> gekennzeichnet.  
  
 Zur Laufzeit bewirken alle Aufrufe von <xref:System.Security.CodeAccessPermission.Assert%2A> von transparentem Code aus, dass eine <xref:System.InvalidOperationException> ausgelöst wird.  Dies kann sowohl bei 100 % transparenten als auch bei Assemblys mit kombiniertem transparentem\/relevantem Code auftreten, in denen eine Methode oder ein Typ zwar transparent deklariert ist, jedoch eine deklarative oder imperative Assertion enthält.  
  
 In [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] 2.0 wurde ein Feature mit dem Namen *Transparenz* eingeführt.  Einzelne Methoden, Felder, Schnittstellen, Klassen und Typen können entweder sicherheitstransparent oder sicherheitsrelevant sein.  
  
 In transparentem Code können Sicherheitsberechtigungen nicht ausgeweitet werden.  Daher werden alle durch Code gewährten oder angeforderten Berechtigungen automatisch durch den Code an den Aufrufer oder die Hostanwendungsdomäne weitergeleitet.  Beispiele für Rechteerweiterungen sind Assertionen, LinkDemands, SuppressUnmanagedCode und `unsafe`\-Code.  
  
## Behandeln von Verstößen  
 Um das Problem zu beheben, markieren Sie entweder den Code, durch den die Assertion aufgerufen wird, mit <xref:System.Security.SecurityCriticalAttribute>, oder entfernen die Assertion.  
  
## Wann sollten Warnungen unterdrückt werden?  
 Unterdrücken Sie keine Meldung dieser Regel.  
  
## Beispiel  
 Dieser Code verursacht einen Fehler, wenn `SecurityTestClass` transparent ist, während die `Assert`\-Methode eine <xref:System.InvalidOperationException> auslöst.  
  
 [!code-cs[FxCop.Security.CA2147.TransparentMethodsMustNotUseSecurityAsserts#1](../code-quality/codesnippet/CSharp/ca2147-transparent-methods-may-not-use-security-asserts_1.cs)]  
  
## Beispiel  
 Eine Option ist, den Code der SecurityTransparentMethod\-Methode im Beispiel unten zu überprüfen, und wenn die Methode sicher für die Erhöhung ist, SecurityTransparentMethod als sicherheitskritisch zu kennzeichnen. Dies erfordert, dass eine ausführliche, vollständige und fehlerfreie Sicherheitsüberprüfung auf die Methode angewendet wird, zusammen mit allen Aufrufen, die innerhalb der Methode unter der Assertion auftreten:  
  
 [!code-cs[FxCop.Security.SecurityTransparentCode2#1](../code-quality/codesnippet/CSharp/ca2147-transparent-methods-may-not-use-security-asserts_2.cs)]  
  
 Eine weitere Möglichkeit besteht darin, die Assertion aus dem Code zu entfernen und nachfolgende Datei\-E\/A\-Berechtigungsanforderungen über SecurityTransparentMethod hinaus an den Aufrufer weiterleiten zu lassen.  Dies ermöglicht Sicherheitsüberprüfungen.  In diesem Fall ist generell keine Sicherheitsüberprüfung erforderlich, da die Berechtigungsanforderungen zum Aufrufer und\/oder zur Anwendungsdomäne geleitet werden.  Berechtigungsforderungen unterliegen einer strengen Kontrolle durch Sicherheitsrichtlinien, die Hostumgebung und gewährte Berechtigungen für die Codequelle.  
  
## Siehe auch  
 [Sicherheitswarnungen](../code-quality/security-warnings.md)