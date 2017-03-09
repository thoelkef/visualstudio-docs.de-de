---
title: "Problembehandlung bei Ausnahmen: System.Threading.AbandonedMutexException | Microsoft Docs"
ms.custom: ""
ms.date: "11/17/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "System.Threading.AbandonedMutexException-Ausnahme"
  - "AbandonedMutexException-Ausnahme"
ms.assetid: 11157066-32ed-492c-83af-29983f915eec
caps.latest.revision: 5
caps.handback.revision: 5
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# Problembehandlung bei Ausnahmen: System.Threading.AbandonedMutexException
Diese Ausnahme wird ausgelöst, wenn ein Thread auf ein Mutex\-Objekt wartet und ein anderer Thread das Mutex durch Beenden abbricht, ohne es freizugeben.  
  
## Hinweise  
 Ein abgebrochenes Mutex weist in der Regel auf einen gravierenden Fehler im Code hin. Wird ein Thread beendet, ohne das Mutex freizugeben, ist die vom Mutex geschützte Datenstruktur möglicherweise nicht in einem konsistenten Zustand. Der nächste Thread, der den Besitz des Mutex anfordert, kann diese Ausnahme behandeln und fortfahren, falls die Integrität der Datenstruktur überprüft werden kann.  
  
## Siehe auch  
 <xref:System.Threading.AbandonedMutexException>   
 <xref:System.Threading.Mutex>   
 [Use the Exception Assistant](../Topic/How%20to:%20Use%20the%20Exception%20Assistant.md)   
 [Threading](../Topic/Threading%20\(C%23%20and%20Visual%20Basic\).md)