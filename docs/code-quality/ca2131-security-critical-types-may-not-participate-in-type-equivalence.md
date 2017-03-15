---
title: "CA2131: Sicherheitskritische Typen d&#252;rfen nicht an Typ&#228;quivalenz beteiligt sein | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CA2131"
ms.assetid: 4170f3b1-6086-430d-8fba-837d5538c573
caps.latest.revision: 10
caps.handback.revision: 10
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# CA2131: Sicherheitskritische Typen d&#252;rfen nicht an Typ&#228;quivalenz beteiligt sein
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|CriticalTypesMustNotParticipateInTypeEquivalence|  
|CheckId|CA2131|  
|Kategorie \(Category\)|Microsoft.Security|  
|Unterbrechende Änderung|Breaking|  
  
## Ursache  
 Ein Typ nimmt an Typäquivalenz teil und entweder der Typ selbst oder ein Member oder ein Feld des Typs wird mit dem <xref:System.Security.SecurityCriticalAttribute>\-Attribut markiert.  
  
## Regelbeschreibung  
 Diese Regel wird für alle wichtigen Typen ausgelöst oder für Typen, die wichtige Methoden oder Felder enthalten, die an der Typäquivalenz beteiligt sind.  Wenn die CLR einen derartigen Typ erkennt, kann sie zur Laufzeit nicht mit einem <xref:System.TypeLoadException>\-Objekt geladen werden.  In der Regel wird diese Regel nur ausgelöst, wenn Benutzer Typäquivalenz manuell implementieren und die Typäquivalenz nicht von tlbimp und den Compilern ausführen lassen.  
  
## Behandeln von Verstößen  
 Um einen Verstoß gegen diese Regel zu beheben, entfernen Sie das SecurityCritical\-Attribut.  
  
## Wann sollten Warnungen unterdrückt werden?  
 Unterdrücken Sie keine Warnung dieser Regel.  
  
## Beispiel  
 In den folgenden Beispielen werden eine Schnittstelle, eine Methode und ein Feld, die bewirken, dass diese Regel ausgelöst wird, veranschaulicht.  
  
 [!code-cs[FxCop.Security.CA2131.CriticalTypesMustNotParticipateInTypeEquivalence#1](../code-quality/codesnippet/CSharp/ca2131-security-critical-types-may-not-participate-in-type-equivalence_1.cs)]  
  
## Siehe auch  
 [Security\-Transparent Code, Level 2](../Topic/Security-Transparent%20Code,%20Level%202.md)