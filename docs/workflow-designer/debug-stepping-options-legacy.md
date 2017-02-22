---
title: "Optionen zum schrittweisen Debuggen (Vorg&#228;ngerversion) | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
helpviewer_keywords: 
  - "schrittweises Ausführen von Verzweigungen"
  - "Debuggen von Workflows, Optionen für die schrittweise Ausführung"
  - "Debuggen, Optionen für die schrittweise Ausführung"
  - "schrittweises Ausführen von Instanzen"
  - "Ausführen in Einzelschritten, Optionen für Workflowdebuggen"
ms.assetid: 3e9e3041-68c7-4f16-9bd6-da5e5144744b
caps.latest.revision: 5
caps.handback.revision: 5
author: "ErikRe"
ms.author: "erikre"
manager: "erikre"
---
# Optionen zum schrittweisen Debuggen (Vorg&#228;ngerversion)
In diesem Thema wird beschrieben, wie [!INCLUDE[wf](../workflow-designer/includes/wf_md.md)]\-Anwendungen gedebuggt werden, die gleichzeitig ausgeführte Aktivitäten in der Vorgängerversion von [!INCLUDE[wfd1](../workflow-designer/includes/wfd1_md.md)] aufweisen.Verwenden Sie die Vorgängerversion von [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)], wenn Sie entweder auf [!INCLUDE[netfx35_long](../workflow-designer/includes/netfx35_long_md.md)] oder [!INCLUDE[vstecwinfx](../workflow-designer/includes/vstecwinfx_md.md)] abzielen möchten.  
  
 Beim Debuggen von Aktivitäten der Vorgängerversion, die gleichzeitig ausgeführt werden, wie zum Beispiel **ParallelActivity** oder **ConditionedActivityGroup**, können Sie mit einer der beiden nachstehenden Optionen den Code schrittweise ausführen.  
  
-   **Schrittweises Ausführen von Verzweigungen** In diesem Modus können Sie eine bestimmte Verzweigung einer zusammengesetzten Aktivität schrittweise durchlaufen und debuggen, beispielsweise die **ParallelActivity** oder die **ConditionalActivityGroup**\-Aktivität.Wenn Sie diese Option zum Debuggen verwenden, bemerken Sie nicht, dass sich das Steuerungsverhalten ändert, weil andere Aktivitäten im Workflow gleichzeitig ausgeführt werden.Der Debugger durchläuft nur die Aktivitäten in der momentan ausgewählten Verzweigung schrittweise, während gleichzeitig ggf. andere Aktivitäten des Workflows ausgeführt werden.Standardmäßig werden beispielsweise die am weitesten links befindliche Verzweigung einer **ParallelActivity**\-Aktivität und die erste untergeordnete Aktivität einer **ConditionedActivityGroup**\-Aktivität schrittweise durchlaufen.Wenn der Benutzer eine andere Verzweigung oder untergeordnete Aktivität debuggen möchte, muss er in der jeweiligen Verzweigung bzw. untergeordneten Aktivität einen expliziten Haltepunkt einfügen.Die Verzweigung wird weiter schrittweise durchlaufen, wenn der Haltepunkt ausgelöst wird.  
  
-   **Schrittweises Ausführen von Instanzen** In diesem Modus können Sie gleichzeitig ausgeführte Aktivitäten des Workflows schrittweise durchlaufen und debuggen.Bei dieser Option ändert sich das Steuerungsverhalten, wenn im Workflow gleichzeitig ausgeführte Aktivitäten aktiv sind.  
  
 Die Option zur schrittweisen Ausführung von Verzweigungen ist standardmäßig ausgewählt, und Benutzer können beim Debuggen eines Workflows der Vorgängerversion zwischen den beiden Optionen wechseln.  
  
 Wählen Sie zum Debuggen von Zustandsautomatworkflows der Vorgängerversion die Option zum schrittweisen Ausführen von Instanzen aus.  
  
## Siehe auch  
 [Debuggen von Legacyworkflows](../workflow-designer/debugging-legacy-workflows.md)   
 [Vorgehensweise: Ändern der Option zum schrittweisen Debuggen \(Vorgängerversion\)](../workflow-designer/how-to-change-the-debug-stepping-option-legacy.md)