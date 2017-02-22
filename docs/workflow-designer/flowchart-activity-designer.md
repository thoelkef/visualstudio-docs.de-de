---
title: "Flussdiagramm-Aktivit&#228;tsdesigner | Microsoft Docs"
ms.custom: ""
ms.date: "09/27/2016"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "System.Activities.Statements.Flowchart.UI"
  - "System.Activities.Statements.FlowStep.UI"
  - "System.Activities.Core.Presentation.FlowStart.UI"
ms.assetid: d5af2276-5215-4138-880a-cf2b90bbf3a0
caps.latest.revision: 5
caps.handback.revision: 5
author: "ErikRe"
ms.author: "erikre"
manager: "erikre"
---
# Flussdiagramm-Aktivit&#228;tsdesigner
Die <xref:System.Activities.Statements.Flowchart>\-Aktivität wird verwendet, um Workflows zu erstellen, die komplexe Flusssteuerungen definieren und verwalten.Ein <xref:System.Activities.Statements.Flowchart> kann entweder im Code oder mit [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)] erstellt werden.Dieses Thema zeigt die Verwendung von [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)].Der [!INCLUDE[wfd1](../workflow-designer/includes/wfd1_md.md)]\-Workflowaktivitätsdesigner ermöglicht es Entwicklern, Workflows auf eine natürliche Weise zu erstellen.  
  
## Die Flowchart\-Aktivität  
 Die <xref:System.Activities.Statements.Flowchart>\-Aktivität gibt einen eindeutigen <xref:System.Activities.Statements.Flowchart.StartNode%2A> an, der ausgeführt wird, wenn der Workflow startet und ein Netzwerk miteinander verknüpfter <xref:System.Activities.Statements.Flowchart.Nodes%2A> verwendet, um beliebige Schleifen zu erstellen oder zu einem bestimmten Zeitpunkt den Ausführungsfluss anderswohin im Workflow umzuleiten.  
  
### Verwenden des Flussdiagramm\-Aktivitätsdesigners  
 Der **Flussdiagramm**\-Aktivitätsdesigner befindet sich in der Kategorie **Flussdiagramm** der **Toolbox**, auf die zugreifen können, indem Sie in [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)] auf die Registerkarte **Toolbox** klicken \(Sie können auch im Menü **Ansicht** den Befehl **Symbolleiste** auswählen oder STRG\+ALT\+X drücken\).  
  
 Der **Flussdiagramm**\-Aktivitätsdesigner kann aus der **Toolbox** gezogen und auf der [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)]\-Oberfläche dort abgelegt werden, wo Aktivitätsdesigner normalerweise platziert werden, und zwar entweder als eine Stammaktivität oder als das untergeordnete Element einer anderen Ablaufsteuerungsaktivität.Wenn der **Flussdiagramm**\-Aktivitätsdesigner auf einer leeren [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)]\-Oberfläche abgelegt wird, erstellt er eine <xref:System.Activities.Statements.Flowchart>\-Aktivität, die sich standardmäßig in einer erweiterten Ansicht präsentiert, in der der Startknoten, der die Ausführung initiiert, als grüner Ball dargestellt ist.Wenn der **Flussdiagramm**\-Aktivitätsdesigner in einer anderen Ablaufsteuerungsaktivität abgelegt wird, präsentiert er sich in einer minimierten Ansicht, die erweitert werden kann, indem Sie auf den **Flussdiagramm**\-Aktivitätsdesigner doppelklicken.Jede Aktivität in der **Toolbox** kann ebenso wie andere Ablaufsteuerungsaktivitäten direkt auf den **Flussdiagramm**\-Aktivitätsdesigner gezogen werden.  
  
 Nachdem Sie die verschiedenen Aktivitätsdesigner auf den [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)]\-Canvas gezogen haben, können die durch sie dargestellten <xref:System.Activities.Activity>\-Objekte miteinander verknüpft werden, um die Reihenfolge der Ausführung anzugeben.Sie erstellen einen Link zwischen einer Quellaktivität und einer Zielaktivität, indem Sie die Maus über den Designer der Quellaktivität bewegen, an dessen beiden Seiten dann quadratische Ziehpunkte angezeigt werden.Klicken Sie auf einen der quadratischen Ziehpunkte, und ziehen Sie ihn bei gedrückter Maustaste auf einen der Ziehpunkte, die um die Zielaktivität angezeigt werden, sobald Sie die Maus über diese Aktivität bewegen.Lassen Sie die Maustaste los, und zwischen beiden Aktivitäten wird ein Link erstellt, der als vom Quelldesigner zum Zieldesigner zeigender Pfeil dargestellt wird.  
  
### Flussdiagrammaktivitätseigenschaften  
 In der folgenden Tabelle werden die Eigenschaften von <xref:System.Activities.Statements.Flowchart> gezeigt und es wird beschrieben, wie sie im Designer verwendet werden.Diese Eigenschaften können im Eigenschaftenraster oder auf der Designeroberfläche bearbeitet werden.  
  
|Eigenschaftenname|Erforderlich|Verwendung|  
|-----------------------|------------------|----------------|  
|<xref:System.Activities.Activity.DisplayName%2A>|False|Gibt den Anzeigenamen des Aktivitätsdesigners im Header an.Der Standardwert lautet Flussdiagramm.Der Wert kann im **Eigenschaftenfenster** oder direkt im Header des Aktivitätsdesigners bearbeitet werden.<br /><br /> Obwohl der <xref:System.Activities.Activity.DisplayName%2A> nicht zwingend erforderlich ist, wird empfohlen, einen Anzeigenamen zu verwenden.|  
|<xref:System.Activities.Statements.Flowchart.Variables%2A>|False|Die Auflistung der innerhalb dieses <xref:System.Activities.Statements.Flowchart> gültigen Variablen, mittels derer der Zustand gemeinsam mit seinen untergeordneten Aktivitäten verwendet wird.|  
|<xref:System.Activities.Statements.Flowchart.StartNode%2A>|False|Der <xref:System.Activities.Statements.FlowNode>, der ausgeführt wird, wenn <xref:System.Activities.Statements.Flowchart> startet.|  
|<xref:System.Activities.Statements.Flowchart.Nodes%2A>|False|Enthält die Auflistung der <xref:System.Activities.Statements.FlowNode>\-Objekte im <xref:System.Activities.Statements.Flowchart>.|  
  
## Siehe auch  
 [Flussdiagramm](../workflow-designer/flowchart-activity-designers.md)   
 [FlowDecision](../workflow-designer/flowdecision-activity-designer.md)   
 [FlowSwitch\<T\>](../workflow-designer/flowswitch-t-activity-designer.md)