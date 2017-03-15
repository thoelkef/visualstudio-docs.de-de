---
title: "Problembehandlung bei Ausnahmen: System.TypeInitializationException | Microsoft Docs"
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
  - "TypeInitializationException-Ausnahme"
  - "System.TypeInitializationException-Ausnahme"
ms.assetid: c77e81fd-1518-49a1-8213-3f169658f5f5
caps.latest.revision: 7
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# Problembehandlung bei Ausnahmen: System.TypeInitializationException
Die Ausnahme, die als Wrapper um die von dieser Klasseninitialisierung ausgelöste Ausnahme ausgelöst wird.  
  
## Hinweise  
 Wenn die Initialisierung eines Typs durch eine Klasseninitialisierung fehlschlägt, wird eine <xref:System.TypeInitializationException> erstellt. Dieser Ausnahme wird dann ein Verweis auf die Ausnahme übergeben, die durch die Klasseninitialisierung des Typs ausgelöst wurde. Die <xref:System.Exception.InnerException%2A>\-Eigenschaft der <xref:System.TypeInitializationException> enthält die zugrunde liegende Ausnahme.  
  
## Siehe auch  
 <xref:System.TypeInitializationException>   
 [Use the Exception Assistant](../Topic/How%20to:%20Use%20the%20Exception%20Assistant.md)