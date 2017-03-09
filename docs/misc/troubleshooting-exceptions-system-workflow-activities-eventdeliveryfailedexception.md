---
title: "Problembehandlung bei Ausnahmen: System.Workflow.Activities.EventDeliveryFailedException | Microsoft Docs"
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
  - "EHWAEventDeliveryFailed"
helpviewer_keywords: 
  - "System.Workflow.Activities.EventDeliveryFailedException-Ausnahme"
  - "EventDeliveryFailedException-Ausnahme"
ms.assetid: 85ee2cb8-5cd1-4878-9421-2a78614e819f
caps.latest.revision: 7
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# Problembehandlung bei Ausnahmen: System.Workflow.Activities.EventDeliveryFailedException
Eine <xref:System.Workflow.Activities.EventDeliveryFailedException>\-Ausnahme wird ausgelöst, wenn ein vom Host ausgelöstes Ereignis nicht an die Workflowinstanz übergeben werden kann. In der Regel wird das Ereignis auf einer Workflowinstanz von einem <xref:System.Workflow.Activities.ExternalDataExchangeService> ausgelöst. Diese Klasse kann nicht vererbt werden.  
  
## Hinweise  
 Dem Ereignisprotokoll wird die folgende Zeichenfolge hinzugefügt, wenn diese Ausnahme ausgelöst wird: `Event '{1}' on interface type '{0}' for instance id '{2}' cannot be delivered`.  
  
 Wenn Sie einen Zustandsautomatworkflow verwenden, wird möglicherweise eine Ausnahme mit der Meldung `Queue '{0}' is not enabled` ausgegeben. Dies ist der Fall, wenn der aktuelle Status des Zustandsautomaten ein spezifisches Ereignis nicht behandeln kann. Die Meldung wird beispielsweise ausgegeben, wenn ein anderer Status als der aktuelle Status die <xref:System.Workflow.Activities.EventDrivenActivity> enthält, die die <xref:System.Workflow.Activities.HandleExternalEventActivity> enthält, die von der `'{0}'`\-Warteschlange dargestellt wird.  
  
## Siehe auch  
 <xref:System.Workflow.Activities.EventDeliveryFailedException>   
 [Use the Exception Assistant](../Topic/How%20to:%20Use%20the%20Exception%20Assistant.md)