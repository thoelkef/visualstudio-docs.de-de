---
title: "CA2211: Nicht konstante Felder sollten nicht sichtbar sein | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CA2211"
  - "NonConstantFieldsShouldNotBeVisible"
helpviewer_keywords: 
  - "CA2211"
  - "NonConstantFieldsShouldNotBeVisible"
ms.assetid: e1e42c40-0acd-4312-af29-70133739a304
caps.latest.revision: 13
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
caps.handback.revision: 13
---
# CA2211: Nicht konstante Felder sollten nicht sichtbar sein
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|NonConstantFieldsShouldNotBeVisible|  
|CheckId|CA2211|  
|Kategorie \(Category\)|Microsoft.Usage|  
|Unterbrechende Änderung|Breaking|  
  
## Ursache  
 Ein öffentliches oder geschütztes statisches Feld ist weder konstant noch ist es schreibgeschützt.  
  
## Regelbeschreibung  
 Statische Felder, die weder konstant noch schreibgeschützt sind, sind nicht threadsicher.  Der Zugriff auf ein solches Feld muss sorgfältig kontrolliert werden und erfordert fortgeschrittene Programmiertechniken zur Synchronisierung des Zugriffs auf das Klassenobjekt.  Weil diese Fertigkeiten schwer zu erlernen sind und das Testen eines solchen Objekts eigene Probleme birgt, werden statische Felder am besten zum Speichern von Daten verwendet, die sich nicht ändern.  Diese Regel gilt für Bibliotheken. Anwendungen sollten keine Felder verfügbar machen.  
  
## Behandeln von Verstößen  
 Um einen Verstoß gegen diese Regel zu beheben, sorgen Sie dafür, dass das statische Feld konstant oder schreibgeschützt ist.  Wenn dies nicht möglich ist, gestalten Sie den Typ so um, dass ein alternativer Mechanismus, z. B. eine threadsichere Eigenschaft, verwendet wird, um threadsichere Zugriffe auf das zugrunde liegende Feld zu verwalten.  Beachten Sie, dass sich Probleme wie Sperrungskonflikte und Deadlocks auf die Leistung und das Verhalten der Bibliothek auswirken können.  
  
## Wann sollten Warnungen unterdrückt werden?  
 Eine Warnung dieser Regel kann gefahrlos unterdrückt werden, wenn Sie eine Anwendung entwickeln und daher vollständige Kontrolle über den Typ haben, der das statische Feld enthält.  Programmierer von Bibliotheken sollten keine Warnung dieser Regel unterdrücken. Die Verwendung nicht konstanter statischer Felder kann Entwicklern die ordnungsgemäße Verwendung der Bibliothek erschweren.  
  
## Beispiel  
 Im folgenden Beispiel wird ein Typ veranschaulicht, der gegen diese Regel verstößt.  
  
 [!code-vb[FxCop.Usage.AvoidStaticNonConstants#1](../code-quality/codesnippet/VisualBasic/ca2211-non-constant-fields-should-not-be-visible_1.vb)]
 [!code-cs[FxCop.Usage.AvoidStaticNonConstants#1](../code-quality/codesnippet/CSharp/ca2211-non-constant-fields-should-not-be-visible_1.cs)]