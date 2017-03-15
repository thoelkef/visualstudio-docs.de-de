---
title: "CA2123: &#220;berschreibungslinkaufrufe sollten mit der Basis identisch sein | Microsoft Docs"
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
  - "CA2123"
  - "OverrideLinkDemandsShouldBeIdenticalToBase"
helpviewer_keywords: 
  - "CA2123"
  - "OverrideLinkDemandsShouldBeIdenticalToBase"
ms.assetid: 4538ecd5-fc6f-4480-ab00-90b2ce4730db
caps.latest.revision: 18
caps.handback.revision: 18
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# CA2123: &#220;berschreibungslinkaufrufe sollten mit der Basis identisch sein
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|OverrideLinkDemandsShouldBeIdenticalToBase|  
|CheckId|CA2123|  
|Kategorie \(Category\)|Microsoft.Security|  
|Unterbrechende Änderung|Breaking|  
  
## Ursache  
 Eine öffentliche oder geschützte Methode in einem öffentlichen Typ überschreibt eine Methode oder implementiert eine Schnittstelle und verfügt nicht über die gleichen [Link Demands](../Topic/Link%20Demands.md) wie die Schnittstelle oder die virtuelle Methode.  
  
## Regelbeschreibung  
 Durch diese Regel wird eine Methode mit ihrer Basismethode verglichen. Bei dieser handelt es sich entweder um eine Schnittstelle oder um eine virtuelle Methode in einem anderen Typ. Anschließend werden die Linkaufruf mit denen der Schnittstelle bzw. virtuellen Methode verglichen.  Ein Verstoß wird gemeldet, wenn die Methode einen Linkaufruf besitzt, die Basismethode dagegen nicht und umgekehrt.  
  
 Bei einem Verstoß gegen diese Regel kann ein böswilliger Aufrufer den Linkaufruf einfach durch den Aufruf der ungesicherten Methode umgehen.  
  
## Behandeln von Verstößen  
 Um einen Verstoß gegen diese Regel zu beheben, wenden Sie den gleichen Linkaufruf auf die Überschreibungsmethode oder die Implementierung an.  Wenn dies nicht möglich ist, markieren Sie die Methode mit einer vollständigen Forderung, oder entfernen Sie das Attribut vollständig.  
  
## Wann sollten Warnungen unterdrückt werden?  
 Unterdrücken Sie keine Warnung dieser Regel.  
  
## Beispiel  
 Im folgenden Beispiel werden verschiedene Verstöße gegen diese Regel veranschaulicht.  
  
 [!code-cs[FxCop.Security.OverridesAndSecurity#1](../code-quality/codesnippet/CSharp/ca2123-override-link-demands-should-be-identical-to-base_1.cs)]  
  
## Siehe auch  
 [Secure Coding Guidelines](../Topic/Secure%20Coding%20Guidelines.md)   
 [Link Demands](../Topic/Link%20Demands.md)