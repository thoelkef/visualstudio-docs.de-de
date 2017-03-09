---
title: "Problembehandlung bei Ausnahmen: System.StackOverflowException | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "JScript"
  - "VB"
  - "CSharp"
  - "C++"
helpviewer_keywords: 
  - "StackOverflowException-Klasse"
ms.assetid: 51b71217-c507-4f5b-bc35-0236180d7968
caps.latest.revision: 20
caps.handback.revision: 20
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# Problembehandlung bei Ausnahmen: System.StackOverflowException
Eine <xref:System.StackOverflowException>\-Ausnahme wird ausgelöst, wenn der Ausführungsstapel wegen einer zu großen Anzahl geschachtelter Methodenaufrufe überläuft.  
  
## Tipps  
 Stellen Sie sicher, dass sich keine Endlosschleife ergibt.  
 Zu viele Methodenaufrufe sind oft ein Hinweis auf eine sehr tiefe oder unbegrenzte Rekursion.  
  
## Hinweise  
 Sie können Ausnahmen für Stapelüberläufe nicht abfangen, da für den Ausnahmebehandlungscode möglicherweise der Stapel erforderlich ist. Wenn stattdessen in einer normalen Anwendung ein Stapelüberlauf auftritt, beendet die Common Language Runtime den Prozess.  
  
 Eine Anwendungen, die die Common Language Runtime hostet, kann das Standardverhalten ändern und angeben, dass die Common Language Runtime die Anwendungsdomäne entladen soll, wenn die Ausnahme auftritt, der Prozess aber fortgesetzt werden soll. Weitere Informationen finden Sie unter [ICLRPolicyManager\-Schnittstelle](../Topic/ICLRPolicyManager%20Interface.md).  
  
## Siehe auch  
 <xref:System.StackOverflowException>   
 [Use the Exception Assistant](../Topic/How%20to:%20Use%20the%20Exception%20Assistant.md)   
 [Loop Structures](/dotnet/visual-basic/programming-guide/language-features/control-flow/loop-structures)