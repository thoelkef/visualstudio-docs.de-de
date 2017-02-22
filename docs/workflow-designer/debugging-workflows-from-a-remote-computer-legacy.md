---
title: "Debuggen von Workflows von einem Remotecomputer (Vorg&#228;ngerversion) | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
helpviewer_keywords: 
  - "Debuggen von Workflows, remote"
  - "Debuggen, Remote"
  - "Remotedebuggen, Workflows"
  - "Workflows, remote debuggen"
ms.assetid: 44eaec8f-9959-4ae7-a374-670946f933c1
caps.latest.revision: 6
caps.handback.revision: 6
author: "ErikRe"
ms.author: "erikre"
manager: "erikre"
---
# Debuggen von Workflows von einem Remotecomputer (Vorg&#228;ngerversion)
In diesem Thema wird das Debuggen von [!INCLUDE[wf](../workflow-designer/includes/wf_md.md)]\-Anwendungen der Vorgängerversion beschrieben, die mit der Vorgängerversion von [!INCLUDE[wfd1](../workflow-designer/includes/wfd1_md.md)] erstellt werden.Verwenden Sie die Vorgängerversion von [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)] verwenden, wenn die Anwendung auf [!INCLUDE[netfx35_long](../workflow-designer/includes/netfx35_long_md.md)] oder [!INCLUDE[vstecwinfx](../workflow-designer/includes/vstecwinfx_md.md)] abzielen muss.  
  
 Bei der Installation von [!INCLUDE[vs_current_long](../misc/includes/vs_current_long_md.md)] ist eine Option der Komponenteninstallation die Installation des [!INCLUDE[vs_current_long](../misc/includes/vs_current_long_md.md)]\-Debuggers für [!INCLUDE[wf](../workflow-designer/includes/wf_md.md)].Hiermit werden die Komponenten zum Remotedebuggen installiert.Diese Komponenten für Remotedebugging müssen auf dem Computer installiert werden, auf dem Remoteworkflow\-Debuggen ausgeführt werden soll.  
  
 Zusätzlich muss die Assembly, die die Workflowdefinition des Legacyworkflows enthält, den Sie auf einem Remotecomputer debuggen, im globalen Assemblycache \(GAC\) des lokalen Computers installiert sein, von dem Sie debuggen.Wird beispielsweise ein Legacyworkflow auf einem Remotecomputer A ausgeführt, und debuggen Sie diesen vom lokalen Computer B, muss die Workflowdefinition im GAC von Computer B vorhanden sein.Hiermit wird der Designer für die Deserialisierung und die Anzeige des Workflowmarkups des remote auf Computer A ausgeführten Workflows auf Computer B aktiviert.Weitere Informationen zum globalen Assemblycache finden Sie in der MSDN Library.  
  
 Das Remotedebugging in [!INCLUDE[wf2](../workflow-designer/includes/wf2_md.md)] funktioniert genauso wie das Remotedebugging for andere [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]\-Komponenten.Weitere Informationen finden Sie unter [!INCLUDE[vs_current_long](../misc/includes/vs_current_long_md.md)] Remotedebuggen in der MSDN Library.  
  
## Siehe auch  
 [Debuggen von Legacyworkflows](../workflow-designer/debugging-legacy-workflows.md)