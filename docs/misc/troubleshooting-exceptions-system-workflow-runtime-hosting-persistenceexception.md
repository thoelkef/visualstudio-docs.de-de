---
title: "Problembehandlung bei Ausnahmen: System.Workflow.Runtime.Hosting.PersistenceException | Microsoft Docs"
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
  - "EHWRHPersistence"
helpviewer_keywords: 
  - "PersistenceException-Ausnahme"
  - "System.Workflow.Runtime.Hosting.PersistenceException-Ausnahme"
ms.assetid: cb2fb820-f990-4728-9a7f-5ec6fd8d5b10
caps.latest.revision: 7
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# Problembehandlung bei Ausnahmen: System.Workflow.Runtime.Hosting.PersistenceException
Eine <xref:System.Workflow.Runtime.Hosting.PersistenceException>\-Ausnahme wird ausgelöst, wenn der Persistenzdienst eine Anforderung nicht erfüllen kann.  
  
## Hinweise  
 Der <xref:System.Workflow.Runtime.Hosting.SqlWorkflowPersistenceService> löst eine <xref:System.Workflow.Runtime.Hosting.PersistenceException> aus, wenn er eine Anforderung zum Übernehmen eines abgeschlossenen Umfangs oder des Workflowinstanzstatus in die Datenbank nicht abschließen kann.  
  
 Wenn Sie einen Persistenzdienst durch Ableitung von der <xref:System.Workflow.Runtime.Hosting.WorkflowPersistenceService>\-Klasse oder der <xref:System.Workflow.Runtime.Hosting.SqlWorkflowPersistenceService>\-Klasse implementieren, können Sie die <xref:System.Workflow.Runtime.Hosting.PersistenceException> mit einer entsprechenden Meldung auslösen, um eine von Ihrem Dienst gefundene Fehlerbedingung anzugeben, die verhindert, dass eine vom Workflow\-Laufzeitmodul getätigte Anforderung erfüllt wird.  
  
 Weitere Informationen finden Sie unter <xref:System.Workflow.Runtime.Hosting.WorkflowPersistenceService>.  
  
## Siehe auch  
 <xref:System.Workflow.Runtime.Hosting.PersistenceException>   
 [Use the Exception Assistant](../Topic/How%20to:%20Use%20the%20Exception%20Assistant.md)