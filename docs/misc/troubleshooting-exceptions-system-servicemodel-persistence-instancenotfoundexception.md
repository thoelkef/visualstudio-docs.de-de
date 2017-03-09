---
title: "Problembehandlung bei Ausnahmen: System.ServiceModel.Persistence.InstanceNotFoundException | Microsoft Docs"
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
  - "InstanceNotFoundException-Ausnahme"
  - "System.ServiceModel.Persistence.InstanceNotFoundException-Ausnahme"
ms.assetid: e3905352-dff0-41d4-b970-8e1b26d85a83
caps.latest.revision: 6
caps.handback.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# Problembehandlung bei Ausnahmen: System.ServiceModel.Persistence.InstanceNotFoundException
Eine <xref:System.ServiceModel.Persistence.InstanceNotFoundException>\-Ausnahme wird unter den folgenden Umständen ausgelöst:  
  
-   ein Vorgang wird in einer permanenten Dienstinstanz ausgeführt, die zum Abschluss markiert wurde  
  
-   ein von einer <xref:System.ServiceModel.Persistence.SqlPersistenceProviderFactory> erstellter Persistenzanbieter versucht Zustandsdaten zu sperren, entsperren oder anderweitig zu verarbeitem, die nicht in der Datenbank gefunden wurden.  
  
## Siehe auch  
 <xref:System.ServiceModel.Persistence.InstanceNotFoundException>   
 [Use the Exception Assistant](../Topic/How%20to:%20Use%20the%20Exception%20Assistant.md)