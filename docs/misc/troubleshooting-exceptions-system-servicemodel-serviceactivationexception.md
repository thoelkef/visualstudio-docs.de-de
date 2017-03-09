---
title: "Problembehandlung bei Ausnahmen: System.ServiceModel.ServiceActivationException | Microsoft Docs"
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
  - "ServiceActivationException-Ausnahme"
  - "System.ServiceModel.ServiceActivationException-Ausnahme"
ms.assetid: 32a3ea87-d6da-40bf-ba04-e862ac122391
caps.latest.revision: 6
caps.handback.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# Problembehandlung bei Ausnahmen: System.ServiceModel.ServiceActivationException
Eine <xref:System.ServiceModel.ServiceActivationException>\-Ausnahme wird ausgelöst, wenn die Aktivierung eines Diensts fehlschlägt.  
  
## Hinweise  
 Diese Ausnahme leitet sich von der <xref:System.ServiceModel.CommunicationException> ab, die eine Klasse wiederherstellbarer Fehler darstellt, die möglicherweise während der Kommunikation zwischen Endpunkten ausgelöst wird und die von stabilen [!INCLUDE[vsindigo](../data-tools/includes/vsindigo_md.md)]\-Client\- und Dienstanwendungen behandelt werden sollten. Um zu verhindern, dass der stärker generische <xref:System.ServiceModel.CommunicationException>\-Handler die spezifischere <xref:System.ServiceModel.ActionNotSupportedException> abfängt, fangen Sie diese Ausnahme vor der Behandlung der <xref:System.ServiceModel.CommunicationException> ab.  
  
## Siehe auch  
 <xref:System.ServiceModel.ServiceActivationException>   
 [Use the Exception Assistant](../Topic/How%20to:%20Use%20the%20Exception%20Assistant.md)