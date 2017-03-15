---
title: "CA2138: Transparente Methoden d&#252;rfen keine Methoden mit dem SuppressUnmanagedCodeSecurity-Attribut aufrufen | Microsoft Docs"
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
  - "CA2138"
ms.assetid: a14c4d32-f079-4f3a-956c-a1657cde0f66
caps.latest.revision: 12
caps.handback.revision: 12
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# CA2138: Transparente Methoden d&#252;rfen keine Methoden mit dem SuppressUnmanagedCodeSecurity-Attribut aufrufen
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|TransparentMethodsMustNotCallSuppressUnmanagedCodeSecurityMethods|  
|CheckId|CA2138|  
|Kategorie \(Category\)|Microsoft.Security|  
|Unterbrechende Änderung|Breaking|  
  
## Ursache  
 Eine sicherheitstransparente Methode ruft eine Methode auf, die mit dem <xref:System.Security.SuppressUnmanagedCodeSecurityAttribute>\-Attribut markiert ist.  
  
## Regelbeschreibung  
 Diese Regel wird für jede transparente Methode ausgelöst, die direkt einen Aufruf in systemeigenem Code ausführt, z. B. mit einem P\/Invoke\-Aufruf \(Plattformaufruf\).  P\/Invoke\- und COM\-Interop\-Methoden, die mit dem <xref:System.Security.SuppressUnmanagedCodeSecurityAttribute>\-Attribut markiert werden, führen zu einem LinkDemand, der für die aufrufende Methode durchgeführt wird.  Da sicherheitstransparenter Code LinkDemands nicht zufrieden stellen kann, können im Code auch nicht Methoden, die mit dem SuppressUnmanagedCodeSecurity\-Attribut markiert werden, oder Methoden einer Klasse, die mit SuppressUnmanagedCodeSecurity\-Attribut markiert wird, aufgerufen werden.  Die Methode schlägt fehl, oder die Forderung wird in eine vollständige Forderung konvertiert.  
  
 Verstöße gegen diese Regel führen im Sicherheitstransparenzmodell der Ebene 2 zu einer <xref:System.MethodAccessException>, und eine vollständige Anforderung für <xref:System.Security.Permissions.SecurityPermissionAttribute.UnmanagedCode%2A> im Transparenzmodell der Ebene 1.  
  
## Behandeln von Verstößen  
 Um eine Verletzung dieser Regel zu korrigieren, entfernen Sie das <xref:System.Security.SuppressUnmanagedCodeSecurityAttribute>\-Attribut, und markieren Sie die Methode mit dem <xref:System.Security.SecurityCriticalAttribute>\-Attribut oder dem <xref:System.Security.SecuritySafeCriticalAttribute>\-Attribut.  
  
## Wann sollten Warnungen unterdrückt werden?  
 Unterdrücken Sie keine Warnung dieser Regel.  
  
## Beispiel  
 [!code-cs[FxCop.Security.CA2138.TransparentMethodsMustNotCallSuppressUnmanagedCodeSecurityMethods#1](../code-quality/codesnippet/CSharp/ca2138-transparent-methods-must-not-call-methods-with-the-suppressunmanagedcodesecurity-attribute_1.cs)]