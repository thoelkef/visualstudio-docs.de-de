---
title: "CA2136: Member d&#252;rfen keine miteinander in Konflikt stehenden Transparenzanmerkungen aufweisen | Microsoft Docs"
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
  - "CA2127"
  - "SecurityTransparentAssembliesShouldNotContainSecurityCriticalCode"
  - "CA2136"
helpviewer_keywords: 
  - "CA2127"
  - "SecurityTransparentAssembliesShouldNotContainSecurityCriticalCode"
ms.assetid: ff5a1d18-7c52-4da5-8990-60be83a8ea81
caps.latest.revision: 15
caps.handback.revision: 15
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# CA2136: Member d&#252;rfen keine miteinander in Konflikt stehenden Transparenzanmerkungen aufweisen
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|TransparencyAnnotationsShouldNotConflict|  
|CheckId|CA2136|  
|Kategorie \(Category\)|Microsoft.Security|  
|Unterbrechende Änderung|Breaking|  
  
## Ursache  
 Diese Regel wird ausgelöst, wenn ein Typmember mit einem <xref:System.Security>\-Sicherheitsattribut markiert wird, das eine andere Transparenz aufweist als das Sicherheitsattribut eines Containers des Members.  
  
## Regelbeschreibung  
 Transparenzattribute werden von größeren Codeelementen bis hin zu kleineren Elementen übernommen.  Die Transparenzattribute von Codeelementen mit größerem Umfang haben Vorrang vor Transparenzattributen von Codeelementen, die im ersten Element enthalten sind.  Beispiel: Eine Klasse, die mit dem <xref:System.Security.SecurityCriticalAttribute>\-Attribut markiert ist, kann keine Methode enthalten, die mit dem <xref:System.Security.SecuritySafeCriticalAttribute>\-Attribut markiert ist.  
  
## Behandeln von Verstößen  
 Um diese Verletzung zu korrigieren, entfernen Sie das Sicherheitsattribut aus dem Codeelement, das einen niedrigeren Bereich hat, oder ändern Sie das Attribut, damit es mit dem enthaltenden Codeelement übereinstimmt.  
  
## Wann sollten Warnungen unterdrückt werden?  
 Unterdrücken Sie keine Warnung dieser Regel.  
  
## Beispiel  
 Im folgenden Beispiel wird eine Methode mit dem <xref:System.Security.SecuritySafeCriticalAttribute>\-Attribut markiert und ist ein Member einer Klasse, die mit dem <xref:System.Security.SecurityCriticalAttribute>\-Attribut markiert ist.  Das sichere Attribut sollte entfernt werden.  
  
 [!code-cs[FxCop.Security.CA2136.TransparencyAnnotationsShouldNotConflict#1](../code-quality/codesnippet/CSharp/ca2136-members-should-not-have-conflicting-transparency-annotations_1.cs)]