---
title: "Deaktivieren des Visual Studio-Debuggers f&#252;r Windows Workflow Foundation (Vorg&#228;ngerversion) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
helpviewer_keywords: 
  - "Debuggen von Workflows, Deaktivieren des Debuggers"
  - "Debuggen von Workflows, Deaktivieren"
  - "Workflows, Deaktivieren des Debuggers"
ms.assetid: 9da96d0e-f941-4fa9-a1a5-6bab50adfec9
caps.latest.revision: 6
author: "ErikRe"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 6
---
# Deaktivieren des Visual Studio-Debuggers f&#252;r Windows Workflow Foundation (Vorg&#228;ngerversion)
In diesem Thema wird das Deaktivieren des [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]\-Debuggers mithilfe der Konfigurationsdatei beim Erstellen von [!INCLUDE[wf](../workflow-designer/includes/wf_md.md)]\-Anwendungen in der Vorgängerversion von [!INCLUDE[wfd1](../workflow-designer/includes/wfd1_md.md)] beschrieben.Verwenden Sie die Vorgängerversion von [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)], wenn Sie entweder auf [!INCLUDE[netfx35_long](../workflow-designer/includes/netfx35_long_md.md)] oder [!INCLUDE[vstecwinfx](../workflow-designer/includes/vstecwinfx_md.md)] abzielen möchten.  
  
 Standardmäßig ist der [!INCLUDE[vs_current_long](../misc/includes/vs_current_long_md.md)]\-Debugger für [!INCLUDE[wf](../workflow-designer/includes/wf_md.md)] für einen Hostprozess aktiviert.Zur Deaktivierung des Workflowdebuggens müssen Sie dieses ausdrücklich ausschalten, indem Sie einen Eintrag "DisableWorkflowDebugging" zum **\<switches\>**\-Element im **\<system.diagnostics\>**\-Abschnitt der Hostkonfigurationsdatei hinzufügen.  
  
 Im folgenden Beispiel wird gezeigt, wie die Hostkonfigurationsdatei geändert wird, um Workflowdebuggen zu deaktivieren.  
  
```  
<?xml version="1.0" encoding="utf-8" ?>  
<configuration>  
   <system.diagnostics>  
      <switches>  
         <add name="DisableWorkflowDebugging" value="true"/>  
      </switches>  
   </system.diagnostics>  
</configuration>  
```  
  
## Siehe auch  
 [Aufrufen des Visual Studio\-Debuggers für Windows Workflow Foundation \(Vorgängerversion\)](../workflow-designer/invoking-the-visual-studio-debugger-for-windows-workflow-foundation-legacy.md)   
 [Debuggen von Legacyworkflows](../workflow-designer/debugging-legacy-workflows.md)