---
title: "CA2140: Transparenter Code darf nicht auf sicherheitskritische Elemente verweisen | Microsoft Docs"
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
  - "CA2129"
  - "SecurityTransparentCodeShouldNotReferenceNonpublicSecurityCriticalCode"
  - "CA2140"
helpviewer_keywords: 
  - "CA2129"
  - "CA2140"
  - "SecurityTransparentCodeShouldNotReferenceNonpublicSecurityCriticalCode"
ms.assetid: 251a12da-0557-47f5-a4f7-0229d590ae7b
caps.latest.revision: 17
caps.handback.revision: 17
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# CA2140: Transparenter Code darf nicht auf sicherheitskritische Elemente verweisen
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|TransparentMethodsMustNotReferenceCriticalCode|  
|CheckId|CA2140|  
|Kategorie \(Category\)|Microsoft.Security|  
|Unterbrechende Änderung|Breaking|  
  
## Ursache  
 Eine transparente Methode:  
  
-   behandelt einen sicherheitskritischen Sicherheitsausnahmetyp  
  
-   verfügt über einen Parameter, der als sicherheitskritischer Typ markiert ist  
  
-   hat einen generischen Parameter mit sicherheitskritischen Einschränkungen  
  
-   verfügt über eine lokale Variable von einem sicherheitskritischen Typ  
  
-   verweist auf einen Typ, der als sicherheitskritisch markiert ist  
  
-   ruft eine Methode auf, die als sicherheitskritisch markiert ist  
  
-   verweist auf ein Feld, das als sicherheitskritisch markiert ist  
  
-   Gibt einen Typ zurück, der als sicherheitskritisch markiert ist  
  
## Regelbeschreibung  
 Ein Code\-Element, das mit dem <xref:System.Security.SecurityCriticalAttribute>\-Attribut markiert ist, ist sicherheitsrelevant.  Eine transparente Methode kann kein sicherheitskritisches Element verwenden.  Wenn ein transparenter Typ einen sicherheitskritischen Typ verwendet, wird <xref:System.TypeAccessException>, <xref:System.MethodAccessException> oder <xref:System.FieldAccessException> ausgelöst.  
  
## Behandeln von Verstößen  
 Führen Sie einen der folgenden Schritte aus, um einen Verstoß gegen diese Regel zu beheben:  
  
-   Das Code\-Element markieren, das den sicherheitskritischen Code mit dem <xref:System.Security.SecurityCriticalAttribute>\-Attribut verwendet.  
  
     – oder –  
  
-   Entfernen Sie das <xref:System.Security.SecurityCriticalAttribute>\-Attribut aus den Codeelementen, die als sicherheitskritisch markiert werden, und markieren Sie sie stattdessen mit dem <xref:System.Security.SecuritySafeCriticalAttribute>\-Attribut oder <xref:System.Security.SecurityTransparentAttribute>\-Attribut.  
  
## Wann sollten Warnungen unterdrückt werden?  
 Unterdrücken Sie keine Warnung dieser Regel.  
  
## Beispiel  
 In den folgenden Beispielen versucht eine transparente Methode, auf eine sicherheitskritische generische Auflistung, ein sicherheitskritisches Feld und eine sicherheitskritische Methode zu verweisen.  
  
 [!code-cs[FxCop.Security.CA2140.TransparentMethodsMustNotReferenceCriticalCode#1](../code-quality/codesnippet/CSharp/ca2140-transparent-code-must-not-reference-security-critical-items_1.cs)]  
  
## Siehe auch  
 <xref:System.Security.SecurityTransparentAttribute>   
 <xref:System.Security.SecurityCriticalAttribute>   
 <xref:System.Security.SecurityTransparentAttribute>   
 <xref:System.Security.SecurityTreatAsSafeAttribute>   
 <xref:System.Security?displayProperty=fullName>