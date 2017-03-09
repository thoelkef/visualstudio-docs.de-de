---
title: "Problembehandlung bei Ausnahmen: System.Security.VerificationException | Microsoft Docs"
ms.custom: ""
ms.date: "10/29/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "EHVerification"
dev_langs: 
  - "JScript"
  - "VB"
  - "CSharp"
  - "C++"
helpviewer_keywords: 
  - "VerificationException-Klasse"
ms.assetid: b7b1a4c2-6769-46bd-8912-ebbfe226bfb3
caps.latest.revision: 15
caps.handback.revision: 15
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# Problembehandlung bei Ausnahmen: System.Security.VerificationException
Eine <xref:System.Security.VerificationException>\-Ausnahme wird ausgelöst, wenn die Sicherheitsrichtlinien Code erfordern, der typsicher ist, aber beim Prüfungsvorgang nicht bestätigt werden kann, dass der Code typsicher ist.  
  
## Tipps  
 Stellen Sie sicher, dass nicht zwei miteinander in Konflikt stehende Versionen einer Klassenbibliothek geladen werden.  
 Im Rahmen des Prüfungsvorgangs wird Microsoft Intermediate Language \(MSIL\) auf Typsicherheit geprüft, um sicherzustellen, dass die Objekte sicher voneinander getrennt wurden und dadurch vor versehentlicher oder böswilliger Beschädigung geschützt sind. Weitere Informationen finden Sie unter [Typsicherheit und Sicherheit](http://msdn.microsoft.com/de-de/095cd1f6-d8db-4c0e-bce2-83ccb34dd5dc).  
  
## Siehe auch  
 <xref:System.Security.VerificationException>   
 <xref:System.Security.Permissions.SecurityPermissionAttribute.SkipVerification%2A>   
 [Use the Exception Assistant](../Topic/How%20to:%20Use%20the%20Exception%20Assistant.md)