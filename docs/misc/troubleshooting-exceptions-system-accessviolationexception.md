---
title: "Problembehandlung bei Ausnahmen: System.AccessViolationException | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "System.AccessViolationException-Ausnahme"
  - "AccessViolationException-Klasse"
ms.assetid: 7f09315d-8aad-4ab1-8b5e-21a8c97f6c14
caps.latest.revision: 9
caps.handback.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# Problembehandlung bei Ausnahmen: System.AccessViolationException
Eine <xref:System.AccessViolationException>\-Ausnahme wird ausgelöst, wenn versucht wird, von geschütztem Arbeitsspeicher zu lesen oder darauf zu schreiben.  
  
## Tipps  
 Stellen Sie sicher, dass der Arbeitsspeicher, auf den Sie zugreifen möchten, belegt wurde.  
 Bei der automatischen Speicherverwaltung handelt es sich um einen Dienst, der von der Common Language Runtime zur Verfügung gestellt wird. Es kann für Sie vorteilhaft sein, zur Nutzung dieses Dienstes auf verwalteten Code umzustellen. Weitere Informationen finden Sie unter [Automatische Speicherverwaltung](../Topic/Automatic%20Memory%20Management.md).  
  
 Stellen Sie sicher, dass der Arbeitsspeicher, auf den Sie zugreifen möchten, nicht beschädigt worden ist.  
 Wenn aufgrund ungültiger Zeiger mehrere Lese\- und Schreibvorgänge erfolgt sind, kann das möglicherweise zu einer Beschädigung des Arbeitsspeichers führen.  
  
### Hinweise  
 Eine Zugriffsverletzung tritt auf, wenn nicht verwalteter bzw. unsicherer Code versucht auf Arbeitsspeicher zuzugreifen, der nicht belegt ist, oder zu dem keine Zugangsberechtigung besteht. Nicht alle Lese\- und Schreibvorgänge, die aufgrund ungültiger Zeiger aufgetreten sind, führen zu Zugriffsverletzungen. Eine Zugriffsverletzung gibt somit an, dass mehrere Lese\- und Schreibvorgänge aufgrund ungültiger Zeiger aufgetreten sind und dass der Arbeitsspeicher u. U. beschädigt sein kann.  
  
 In verwaltetem Code sind alle Verweise entweder gültig oder NULL. Wenn eine Operation versucht, in überprüfbarem Code einen NULL\-Verweis herzustellen, wird eine <xref:System.NullReferenceException> ausgelöst.  
  
 Eine Zugriffsverletzung, die in unsicherem verwalteten Code auftritt, kann je nach Plattform entweder als <xref:System.NullReferenceException> oder als <xref:System.AccessViolationException> ausgedrückt werden.  
  
 Zugriffverletzungen in nicht verwaltetem Code, die an verwalteten Code übergeben werden, sind immer mit einer <xref:System.AccessViolationException> umschlossen.  
  
## Siehe auch  
 [Use the Exception Assistant](../Topic/How%20to:%20Use%20the%20Exception%20Assistant.md)   
 [Speicherverwaltung: Beispiele](../Topic/Memory%20Management:%20Examples.md)   
 [Automatische Speicherverwaltung](../Topic/Automatic%20Memory%20Management.md)