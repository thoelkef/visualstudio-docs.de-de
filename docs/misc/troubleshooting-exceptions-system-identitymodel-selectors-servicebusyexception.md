---
title: "Problembehandlung bei Ausnahmen: System.IdentityModel.Selectors.ServiceBusyException | Microsoft Docs"
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
  - "ServiceBusyException-Ausnahme"
  - "System.IdentityModel.Selectors.ServiceBusyException-Ausnahme"
ms.assetid: 88acdc6b-45ad-40c6-aa5c-3b56244edcee
caps.latest.revision: 6
caps.handback.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# Problembehandlung bei Ausnahmen: System.IdentityModel.Selectors.ServiceBusyException
Eine <xref:System.IdentityModel.Selectors.ServiceBusyException>\-Ausnahme wird ausgelöst, um anzugeben, dass der CardSpace\-Dienst mit der Verarbeitung anderer Anforderungen ausgelastet ist. CardSpace stellt keine Anforderungen in die Warteschlange und kann jeweils nur eine Anforderung bedienen.  
  
 Prüfen Sie, ob eine andere CardSpace\-Instanz ausgeführt wird. Wenn eine andere Instanz ausgeführt wird, beenden Sie sie durch Anhalten des icardagt.exe\-Prozesses im Task Manager.  
  
## Siehe auch  
 <xref:System.IdentityModel.Selectors.ServiceBusyException>   
 [Use the Exception Assistant](../Topic/How%20to:%20Use%20the%20Exception%20Assistant.md)