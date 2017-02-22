---
title: "CA2146: Typen m&#252;ssen mindestens genauso kritisch sein wie ihre Basistypen und Schnittstellen | Microsoft Docs"
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
  - "CA2146"
ms.assetid: 241fb784-1f6b-46e5-8ceb-c438e341d38e
caps.latest.revision: 11
caps.handback.revision: 11
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# CA2146: Typen m&#252;ssen mindestens genauso kritisch sein wie ihre Basistypen und Schnittstellen
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|TypesMustBeAtLeastAsCriticalAsBaseTypes|  
|CheckId|CA2146|  
|Kategorie \(Category\)|Microsoft.Security|  
|Unterbrechende Änderung|Breaking|  
  
## Ursache  
 Ein transparenter Typ wird von einem Typ abgeleitet, der mit dem <xref:System.Security.SecuritySafeCriticalAttribute>\- oder dem <xref:System.Security.SecurityCriticalAttribute>\-Element markiert ist, oder ein Typ, der mit dem <xref:System.Security.SecuritySafeCriticalAttribute>\-Attribut markiert ist, wird von einem Typ abgeleitet, der mit dem <xref:System.Security.SecurityCriticalAttribute>\-Attribut markiert ist.  
  
## Regelbeschreibung  
 Diese Regel wird ausgelöst, wenn ein abgeleiteter Typ über ein Sicherheitstransparenzattribut verfügt, das nicht so wichtig wie der Basistyp oder die implementierte Schnittstelle ist.  Nur wichtige Typen können von wichtigen Basistypen abgeleitet werden oder kritische Schnittstellen implementieren, und nur kritische oder sicherheitskritische Typen können von sicherheitskritischen Basistypen abgeleitet werden oder sicherheitskritische Schnittstellen implementieren.  Verstöße gegen diese Regel in Transparenz der Ebene 2 führen zu einer <xref:System.TypeLoadException> für den abgeleiteten Typ.  
  
## Behandeln von Verstößen  
 Um diese Verletzung zu korrigieren, markieren Sie den abgeleiteten Typ oder Implementierungstyp mit einem Transparenzattribut, das mindestens so wichtig wie der Basistyp oder die Schnittstelle ist.  
  
## Wann sollten Warnungen unterdrückt werden?  
 Unterdrücken Sie keine Warnung dieser Regel.  
  
## Beispiel  
 [!code-cs[FxCop.Security.CA2146.TypesMustBeAtLeastAsCriticalAsBaseTypes#1](../code-quality/codesnippet/CSharp/ca2146-types-must-be-at-least-as-critical-as-their-base-types-and-interfaces_1.cs)]