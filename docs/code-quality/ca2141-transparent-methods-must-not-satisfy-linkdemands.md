---
title: "CA2141: Transparente Methoden d&#252;rfen keine LinkDemands erf&#252;llen | Microsoft Docs"
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
  - "CA2141"
ms.assetid: 2957f5f7-c511-4180-ba80-752034f10a77
caps.latest.revision: 14
caps.handback.revision: 14
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# CA2141: Transparente Methoden d&#252;rfen keine LinkDemands erf&#252;llen
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|TransparentMethodsMustNotSatisfyLinkDemands|  
|CheckId|CA2141|  
|Kategorie \(Category\)|Microsoft.Security|  
|Unterbrechende Änderung|Breaking|  
  
## Ursache  
 Eine sicherheitstransparente Methode ruft eine Methode in einer Assembly auf, die nicht mit dem <xref:System.Security.AllowPartiallyTrustedCallersAttribute> \(APTCA\)\-Attribut markiert ist, oder eine sicherheitstransparente Methode stellt ein <xref:System.Security.Permissions.SecurityAction>`.LinkDemand`\-Element für einen Typ oder eine Methode bereit.  
  
## Regelbeschreibung  
 Die Erfüllung eines LinkDemand ist ein sicherheitssensibler Vorgang, der unbeabsichtigt zur Erweiterung der Berechtigungen führen kann.  Sicherheitstransparenter Code darf LinkDemands nicht bedienen, da er nicht denselben Sicherheitsprüfungsanforderungen unterliegt wie sicherheitskritischer Code.  Transparente Methoden in Assemblys des Sicherheitsregelsatzes der Ebene 1 sorgen dafür, dass alle LinkDemands, denen sie entsprechen, zur Laufzeit in vollständige Anforderungen konvertiert werden, wodurch Leistungsprobleme entstehen können.  In Assemblys mit Sicherheitsregel auf Ebene 2 werden transparente Methoden nicht im Just\-In\-Time \(JIT\)\-Compiler kompiliert, wenn sie versuchen, einen LinkDemand zu bedienen.  
  
 In Assemblys mit Ebene\-2\-Sicherheit, löst der Versuch, durch eine sicherheitstransparente Methode einen LinkDemand zu bedienen oder eine Methode in einer nicht\-APTCA\-Assembly aufzurufen, eine <xref:System.MethodAccessException> aus. In Assemblys der Ebene 1 wird LinkDemand zu einer vollständigen Anforderung.  
  
## Behandeln von Verstößen  
 Um eine Verletzung dieser Regel zu korrigieren, markieren Sie die Zugriffsmethode mit dem <xref:System.Security.SecurityCriticalAttribute>\-Attribut oder dem <xref:System.Security.SecuritySafeCriticalAttribute>\-Attribut, oder entfernen Sie die LinkDemand aus der Methode, auf die zugegriffen wurde.  
  
## Wann sollten Warnungen unterdrückt werden?  
 Unterdrücken Sie keine Warnung dieser Regel.  
  
## Beispiel  
 In diesem Beispiel versucht eine transparente Methode, eine Methode aufzurufen, die über einen LinkDemand verfügt.  Diese Regel wird für diesen Code ausgelöst.  
  
 [!code-cs[FxCop.Security.CA2141.TransparentMethodsMustNotSatisfyLinkDemands#1](../code-quality/codesnippet/CSharp/ca2141-transparent-methods-must-not-satisfy-linkdemands_1.cs)]