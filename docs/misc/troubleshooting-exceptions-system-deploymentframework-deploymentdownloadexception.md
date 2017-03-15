---
title: "Problembehandlung bei Ausnahmen: System.DeploymentFramework.DeploymentDownloadException | Microsoft Docs"
ms.custom: ""
ms.date: "11/16/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "DeploymentDownloadException-Klasse"
  - "Anwendungsbereitstellung [C#], DeploymentDownloadException-Klasse"
  - "Bereitstellen von Anwendungen [C#], DeploymentDownloadException-Klasse"
ms.assetid: 55ec7af5-b1d1-4db2-8af8-3c708f521cc7
caps.latest.revision: 12
caps.handback.revision: 12
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# Problembehandlung bei Ausnahmen: System.DeploymentFramework.DeploymentDownloadException
Eine `T:System.DeploymentFramework.DeploymentDownloadException` tritt auf, wenn beim Herunterladen eines Anwendungsupdates eine Netzwerkausnahme ausgelöst wird.  
  
## Tipps  
 **Untersuchen Sie InnerException, um die zugrunde liegende System.Net\-Ausnahme bzw. System.IO\-Ausnahme zu bestimmen.**  
 Diese Ausnahme tritt immer dann auf, wenn beim Download eines Anwendungsupdates eine Netzwerkausnahme ausgelöst wird. Untersuchen Sie die <xref:System.Exception.InnerException%2A>\-Eigenschaft der Ausnahme, um die zugrunde liegende Ausnahme zu bestimmen.  
  
## Siehe auch  
 [Use the Exception Assistant](../Topic/How%20to:%20Use%20the%20Exception%20Assistant.md)   
 [Try...Catch...Finally Statement](/dotnet/visual-basic/language-reference/statements/try-catch-finally-statement)