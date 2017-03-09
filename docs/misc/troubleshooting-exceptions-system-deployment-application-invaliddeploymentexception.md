---
title: "Problembehandlung bei Ausnahmen: System.Deployment.Application.InvalidDeploymentException | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
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
  - "InvalidDeploymentException-Klasse"
ms.assetid: 4361e053-8eaf-44e3-b8ac-95516d8d1832
caps.latest.revision: 22
caps.handback.revision: 22
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# Problembehandlung bei Ausnahmen: System.Deployment.Application.InvalidDeploymentException
Eine <xref:System.Deployment.Application.InvalidDeploymentException>\-Ausnahme wird ausgelöst, wenn die Anwendung ungültig ist oder wenn das Anwendungsmanifest und das Bereitstellungsmanifest der Anwendung ungültig sind.  
  
## Tipps  
 **Stellen Sie sicher, dass alle Manifeste für diese Anwendung gültig sind.**  
 Ein Anwendungsmanifest ist eine XML\-Datei, die die freigegebenen und privaten parallelen Assemblys beschreibt und identifiziert, an die sich eine Anwendung zur Laufzeit binden soll. Dabei sollte es sich um die gleichen Assemblyversionen handeln, die zum Testen der Anwendung verwendet wurden. Anwendungsmanifeste können auch Metadaten für private Anwendungsdateien beschreiben.  
  
 **Verwenden Sie das ClickOnce\-Feature, um die Anwendung bereitzustellen.**  
 Mit ClickOnce können Sie Windows\-Anwendungen auf einem Webserver oder in einer Netzwerkdateifreigabe veröffentlichen und so den Installationsvorgang vereinfachen. Weitere Informationen finden Sie unter [ClickOnce Security and Deployment](../deployment/clickonce-security-and-deployment.md).  
  
## Siehe auch  
 <xref:System.Deployment.Application.InvalidDeploymentException>   
 [Use the Exception Assistant](../Topic/How%20to:%20Use%20the%20Exception%20Assistant.md)   
 [Troubleshooting ClickOnce Deployments](../deployment/troubleshooting-clickonce-deployments.md)   
 [ClickOnce\-Bereitstellung für Windows Forms](../Topic/ClickOnce%20Deployment%20for%20Windows%20Forms.md)