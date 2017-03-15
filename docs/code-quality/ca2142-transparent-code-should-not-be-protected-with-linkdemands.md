---
title: "CA2142: Transparenter Code darf nicht mit LinkDemands gesch&#252;tzt werden | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CA2142"
ms.assetid: 6dc59053-5dd9-4583-bf10-5f339107e59f
caps.latest.revision: 10
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
caps.handback.revision: 10
---
# CA2142: Transparenter Code darf nicht mit LinkDemands gesch&#252;tzt werden
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|TransparentMethodsShouldNotBeProtectedWithLinkDemands|  
|CheckId|CA2142|  
|Kategorie \(Category\)|Microsoft.Security|  
|Unterbrechende Änderung|Breaking|  
  
## Ursache  
 Eine transparente Methode erfordert ein <xref:System.Security.Permissions.SecurityAction>\-Element oder eine andere Sicherheitsanforderung.  
  
## Regelbeschreibung  
 Diese Regel wird für transparente Methoden ausgelöst, die einen Zugriff durch LinkDemands erfordern.  Sicherheitstransparenter Code sollte nicht für das Überprüfen der Sicherheit einer Operation zuständig sein und sollte daher keine Berechtigungen fordern.  Da transparente Methoden sicherheitsneutral sein sollten, sollten sie keine Sicherheitsentscheidungen treffen.  Darüber hinaus sollte sicherheitsrelevanter Code, in dem Sicherheitsentscheidungen getroffen werden, nicht auf transparentem Code gründen, in dem zuvor so eine Entscheidung getroffen wurde.  
  
## Behandeln von Verstößen  
 Um eine Verletzung dieser Regel zu korrigieren, entfernen Sie den Linkaufruf für die transparente Methode, oder markieren Sie die Methode mit dem <xref:System.Security.SecuritySafeCriticalAttribute>\-Attribut, wenn Sicherheitsüberprüfungen ausgeführt werden, wie z. B. Sicherheitsanforderungen.  
  
## Wann sollten Warnungen unterdrückt werden?  
 Unterdrücken Sie keine Warnung dieser Regel.  
  
## Beispiel  
 Im folgenden Beispiel wird die Regel für die Methode ausgelöst, da die Methode transparent ist und mit einem LinkDemand <xref:System.Security.PermissionSet> markiert ist, der einen <xref:System.Security.Permissions.SecurityAction> enthält.  
  
 [!code-cs[FxCop.Security.CA2142.TransparentMethodsShouldNotBeProtectedWithLinkDemands#1](../code-quality/codesnippet/CSharp/ca2142-transparent-code-should-not-be-protected-with-linkdemands_1.cs)]  
  
 Unterdrücken Sie keine Warnung dieser Regel.