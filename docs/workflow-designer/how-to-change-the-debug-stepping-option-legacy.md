---
title: "Vorgehensweise: &#196;ndern der Option zum schrittweisen Debuggen (Vorg&#228;ngerversion) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
helpviewer_keywords: 
  - "schrittweises Ausführen von Verzweigungen"
  - "Debuggen von Workflows, Optionen für die schrittweise Ausführung"
  - "Debuggen, Optionen für die schrittweise Ausführung"
  - "schrittweises Ausführen von Instanzen"
  - "schrittweises Ausführen, Ändern von Optionen"
ms.assetid: aedc06af-d58a-44d6-aee4-f397f1f923a0
caps.latest.revision: 5
author: "ErikRe"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 5
---
# Vorgehensweise: &#196;ndern der Option zum schrittweisen Debuggen (Vorg&#228;ngerversion)
In diesem Thema wird beschrieben, wie die Option zum schrittweisen Debuggen für [!INCLUDE[wf](../workflow-designer/includes/wf_md.md)]\-Anwendungen in der Vorgängerversion von [!INCLUDE[wfd1](../workflow-designer/includes/wfd1_md.md)] ausgeführt wird, die über parallele Aktionen verfügen.Verwenden Sie die Vorgängerversion von [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)], wenn Sie entweder auf [!INCLUDE[netfx35_long](../workflow-designer/includes/netfx35_long_md.md)] oder [!INCLUDE[vstecwinfx](../workflow-designer/includes/vstecwinfx_md.md)] abzielen möchten.  
  
 Beim Debuggen von Legacyaktivitäten, die gleichzeitig ausgeführt werden, wie zum Beispiel **ParallelActivity** oder **ConditionedActivityGroup**, können Sie mit einer der beiden Optionen den Code schrittweise ausführen.  
  
 Führen Sie die nachstehenden Schritte aus, um die Option zum schrittweisen Debuggen in Ihrem Legacyworkflowprojekt zu ändern.  
  
## Vorgehensweisen  
  
#### So ändern Sie die Option zum schrittweisen Debuggen  
  
1.  Starten Sie Visual Studio.  
  
2.  Öffnen Sie ein vorhandenes Legacyworkflowprojekt, oder erstellen Sie ein neues Projekt, das gleichzeitige Aktivitäten verwendet und auf [!INCLUDE[netfx35_long](../workflow-designer/includes/netfx35_long_md.md)] oder [!INCLUDE[vstecwinfx](../workflow-designer/includes/vstecwinfx_md.md)] abzielt.  
  
3.  Zeigen Sie im Menü **Workflow** in der Vorgängerversion von [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)] auf **Debuggen** und dann auf **Steppingoptionen**.  
  
4.  Wählen Sie **Instanz** oder **Verzweigung** aus.  
  
## Siehe auch  
 [Debuggen von Legacyworkflows](../workflow-designer/debugging-legacy-workflows.md)   
 [Optionen zum schrittweisen Debuggen \(Vorgängerversion\)](../workflow-designer/debug-stepping-options-legacy.md)