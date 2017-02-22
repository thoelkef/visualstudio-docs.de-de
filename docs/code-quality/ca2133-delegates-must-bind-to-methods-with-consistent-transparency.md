---
title: "CA2133: Delegaten m&#252;ssen an Methoden mit konsistenter Transparenz gebunden werden | Microsoft Docs"
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
  - "CA2133"
ms.assetid: a09672e2-63cb-4abd-9e8f-dff515e101ce
caps.latest.revision: 11
caps.handback.revision: 11
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# CA2133: Delegaten m&#252;ssen an Methoden mit konsistenter Transparenz gebunden werden
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|DelegatesMustBindWithConsistentTransparency|  
|CheckId|CA2133|  
|Kategorie \(Category\)|Microsoft.Security|  
|Unterbrechende Änderung|Breaking|  
  
> [!NOTE]
>  Diese Warnung wird nur für Code übernommen, in dem die CoreCLR ausgeführt wird \(die Version der CLR, die speziell für Silverlight\-Webanwendungen verwendet wird\).  
  
## Ursache  
 Diese Warnung wird für eine Methode ausgelöst, die einen Delegat, der mit dem <xref:System.Security.SecurityCriticalAttribute>\-Objekt markiert ist, an eine Methode bindet, die transparent oder mit dem <xref:System.Security.SecuritySafeCriticalAttribute>\-Objekt markiert ist.  Die Warnung wird auch für eine Methode ausgelöst, die einen transparenten oder sicherheitsrelevanten Delegaten an eine wichtige Methode bindet.  
  
## Regelbeschreibung  
 Delegattypen und die Methoden, an die sie gebunden werden, müssen konsistente Transparenz aufweisen.  Transparente und sicherungskritische Delegaten können nur an andere transparente oder sicherungskritische Methoden gebunden werden.  Ebenso können kritische Delegaten nur an kritische Methoden gebunden werden.  Diese Bindungsregeln stellen sicher, dass im einzigen Code, in dem eine Methode über einen Delegaten aufgerufen werden kann, die gleiche Methode auch direkt hätte aufgerufen werden können.  Bindungsregeln verhindern z. B., dass in transparentem Code wichtiger Code für einen transparenten Delegaten direkt aufgerufen wird.  
  
## Behandeln von Verstößen  
 Um eine Verletzung dieser Warnung zu korrigieren, ändern Sie die Transparenz des Delegaten oder der Methode, die gebunden wird, damit die Transparenz der zwei Objekte übereinstimmt.  
  
## Wann sollten Warnungen unterdrückt werden?  
 Unterdrücken Sie keine Warnung dieser Regel.  
  
### Code  
 [!code-cs[FxCop.Security.CA2133.DelegatesMustBindWithConsistentTransparency#1](../code-quality/codesnippet/CSharp/ca2133-delegates-must-bind-to-methods-with-consistent-transparency_1.cs)]