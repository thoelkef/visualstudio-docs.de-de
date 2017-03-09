---
title: "Problembehandlung bei Ausnahmen: System.Deployment.DependentPlatformMissingException | Microsoft Docs"
ms.custom: ""
ms.date: "10/29/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "JScript"
  - "VB"
  - "CSharp"
  - "C++"
helpviewer_keywords: 
  - "DependentPlatformMissingException-Klasse"
ms.assetid: 2343eb4f-f23f-4b6c-a65c-1f93c3e6ea36
caps.latest.revision: 13
caps.handback.revision: 13
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# Problembehandlung bei Ausnahmen: System.Deployment.DependentPlatformMissingException
Eine `T:System.Deployment.DependentPlatformMissingException`\-Ausnahme wird bei dem Versuch ausgelöst, eine Anwendung auf einem nicht kompatiblen Computer auszuführen. Grund dafür kann ein falsches Betriebssystem oder eine falsche Version von .NET Framework auf dem Zielcomputer sein.  
  
## Tipps  
 **Stellen Sie sicher, dass alle für die Anwendung erforderlichen Assemblys auf dem Zielcomputer installiert sind.**  
 Bei jeder Installation mit dem Windows Installer wird zuerst überprüft, ob der Installer auf dem Computer des Benutzers vorhanden ist. Wenn dies nicht der Fall ist, wird überprüft, ob der Windows Installer auf dem Computer installiert werden kann.  
  
## Siehe auch  
 [Use the Exception Assistant](../Topic/How%20to:%20Use%20the%20Exception%20Assistant.md)