---
title: "Problembehandlung bei Ausnahmen: System.DeploymentFramework.DependentPlatformMissingException | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "DependentPlatformMissingException-Klasse, Problembehandlung"
ms.assetid: fee1ca1c-0f0b-483b-b8ab-3743dfdda038
caps.latest.revision: 12
caps.handback.revision: 12
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# Problembehandlung bei Ausnahmen: System.DeploymentFramework.DependentPlatformMissingException
Eine `T:System.DeploymentFramework.DependentPlatformMissingException`\-Ausnahme wird ausgelöst, wenn eine Anwendung von einer Komponente abhängig ist, die nicht auf diesem Client installiert ist. Eine mögliche Ursache kann unter anderem ein falsches Betriebssystem oder eine falsche Version von [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] auf dem Computer sein, auf dem die Anwendung bereitgestellt wird.  
  
## Tipps  
 **Stellen Sie sicher, dass alle für die Anwendung erforderlichen Assemblys auf dem Zielcomputer installiert sind.**  
 Bei jeder Installation mit dem Windows Installer wird zuerst überprüft, ob der Installer auf dem Computer des Benutzers vorhanden ist. Wenn dies nicht der Fall ist, wird überprüft, ob der Windows Installer auf dem Computer installiert werden kann.  
  
## Siehe auch  
 [Use the Exception Assistant](../Topic/How%20to:%20Use%20the%20Exception%20Assistant.md)