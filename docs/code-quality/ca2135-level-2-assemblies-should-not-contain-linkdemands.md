---
title: "CA2135: Assemblys der Stufe 2 d&#252;rfen keine LinkDemands enthalten | Microsoft Docs"
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
  - "CA2135"
ms.assetid: 7a775285-42d2-4f13-8434-3fdb0deeebe6
caps.latest.revision: 10
caps.handback.revision: 10
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# CA2135: Assemblys der Stufe 2 d&#252;rfen keine LinkDemands enthalten
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|SecurityRuleSetLevel2MethodsShouldNotBeProtectedWithLinkDemands|  
|CheckId|CA2135|  
|Kategorie \(Category\)|Microsoft.Security|  
|Unterbrechende Änderung|Breaking|  
  
## Ursache  
 Eine Klasse oder ein Klassenmember verwendet ein <xref:System.Security.Permissions.SecurityAction>\-Objekt in einer Anwendung, die Sicherheit der Ebene 2 verwendet.  
  
## Regelbeschreibung  
 LinkDemands sind im Sicherheitsregelsatz der Ebene 2 veraltet.  Markieren Sie, statt LinkDemands zur Erzwingung von Sicherheit zur Just\-In\-Time \(JIT\)\-Kompilierungszeit zu erzwingen, die Methoden, Typen und Felder mit dem <xref:System.Security.SecurityCriticalAttribute>\-Attribut.  
  
## Behandeln von Verstößen  
 Um eine Verletzung dieser Regel zu korrigieren, entfernen Sie das <xref:System.Security.Permissions.SecurityAction>\-Feld, und markieren Sie den Typ oder Member mit dem <xref:System.Security.SecurityCriticalAttribute>\-Attribut.  
  
## Wann sollten Warnungen unterdrückt werden?  
 Unterdrücken Sie keine Warnung dieser Regel.  
  
## Beispiel  
 Im folgenden Beispiel sollte <xref:System.Security.Permissions.SecurityAction> und die mit dem <xref:System.Security.SecurityCriticalAttribute>\-Attribut markierte Methode entfernt werden.  
  
 [!code-cs[FxCop.Security.CA2135.SecurityRuleSetLevel2MethodsShouldNotBeProtectedWithLinkDemands#1](../code-quality/codesnippet/CSharp/ca2135-level-2-assemblies-should-not-contain-linkdemands_1.cs)]