---
title: "Problembehandlung bei Ausnahmen: System.ServiceModel.ServerTooBusyException | Microsoft Docs"
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
  - "System.ServiceModel.ServerTooBusyException-Ausnahme"
  - "ServerTooBusyException-Ausnahme"
ms.assetid: 80eb606a-ab3c-48af-b747-c9902989a059
caps.latest.revision: 6
caps.handback.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# Problembehandlung bei Ausnahmen: System.ServiceModel.ServerTooBusyException
Eine <xref:System.ServiceModel.ServerTooBusyException>\-Ausnahme wird ausgelöst, wenn ein Server zu stark ausgelastet ist und keine Nachricht akzeptieren kann.  
  
## Hinweise  
 Diese Ausnahme leitet sich von der <xref:System.ServiceModel.CommunicationException> ab, die eine Klasse wiederherstellbarer Fehler darstellt, die möglicherweise während der Kommunikation zwischen Endpunkten ausgelöst wird. Von stabilen Client\- und Dienst\-[!INCLUDE[vsindigo](../data-tools/includes/vsindigo_md.md)]\-Anwendungen wird die Behandlung dieser Ausnahmen erwartet. Um zu verhindern, dass ein Handler für die <xref:System.ServiceModel.CommunicationException> die spezifischere <xref:System.ServiceModel.ServerTooBusyException> abfängt, fangen Sie diese Ausnahme vor der Behandlung der <xref:System.ServiceModel.CommunicationException> ab.  
  
## Siehe auch  
 <xref:System.ServiceModel.ServerTooBusyException>   
 [Use the Exception Assistant](../Topic/How%20to:%20Use%20the%20Exception%20Assistant.md)