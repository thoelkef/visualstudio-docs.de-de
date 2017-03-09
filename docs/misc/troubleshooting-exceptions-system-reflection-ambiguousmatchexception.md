---
title: "Problembehandlung bei Ausnahmen: System.Reflection.AmbiguousMatchException | Microsoft Docs"
ms.custom: ""
ms.date: "10/29/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "System.Reflection.AmbiguousMatchException-Ausnahme"
  - "AmbiguousMatchException-Ausnahme"
ms.assetid: f92b5c51-42b6-4c2e-83df-0d598b3b41c4
caps.latest.revision: 6
caps.handback.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# Problembehandlung bei Ausnahmen: System.Reflection.AmbiguousMatchException
Diese Ausnahme wird ausgelöst, wenn bei der Bindung an eine Methode mehr als eine Methode den Bindungskriterien entspricht.  
  
## Hinweise  
 Eine <xref:System.Reflection.AmbiguousMatchException> wird ausgelöst, wenn die Anwendung bei einem Klassenaufruf nicht bestimmen kann, welche Klasse oder überladene Klasse zu verwenden ist. In dem Bindungsvorgang wird versucht, die für die Verwendung geeignete Klasse anhand der Anzahl und der Typen der Parameter zu bestimmen. Wenn mehrere Klassen infrage kommen, wird diese Ausnahme ausgelöst.  
  
## Siehe auch  
 <xref:System.Reflection.AmbiguousMatchException>   
 [Use the Exception Assistant](../Topic/How%20to:%20Use%20the%20Exception%20Assistant.md)