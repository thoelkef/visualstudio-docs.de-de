---
title: "Delay-Aktivit&#228;tsdesigner | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "System.Activities.Statements.Delay.UI"
ms.assetid: f51742a8-2c9a-47d1-8a23-18459d03ae19
caps.latest.revision: 8
author: "ErikRe"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 8
---
# Delay-Aktivit&#228;tsdesigner
Der **Delay**\-Aktivitätsdesigner wird verwendet, um eine <xref:System.Activities.Statements.Delay>\-Aktivität zu erstellen und zu konfigurieren.  
  
## Die Delay\-Aktivität  
 Die <xref:System.Activities.Statements.Delay>\-Aktivität verzögert die Ausführung eines Workflows während einer bestimmten Zeitspanne.  
  
### Verwenden des Delay\-Aktivitätsdesigners  
 Der **Delay**\-Aktivitätsdesigner befindet sich in der Kategorie **Primitives** der **Toolbox**, auf die Sie zugreifen können, indem Sie in [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)] auf die Registerkarte **Toolbox** klicken \(Sie können auch im Menü **Ansicht** den Befehl **Symbolleiste** auswählen oder STRG\+ALT\+X drücken\).  
  
 Der **Delay**\-Aktivitätsdesigner kann aus der **Toolbox** gezogen und auf der [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)]\-Oberfläche dort abgelegt werden, wo Aktivitäten normalerweise platziert werden, etwa innerhalb einer <xref:System.Activities.Statements.Sequence>.Dadurch wird eine <xref:System.Activities.Statements.Delay>\-Aktivität mit dem standardmäßigen <xref:System.Activities.Activity.DisplayName%2A> Delay erstellt.Der <xref:System.Activities.Activity.DisplayName%2A>\-Wert kann im Header des **Delay**\-Aktivitätsdesigners oder im Feld **DisplayName** des Eigenschaftenrasters bearbeitet werden.  
  
### Die Delay\-Eigenschaften  
 In der folgenden Tabelle werden die Eigenschaften von <xref:System.Activities.Statements.Delay> gezeigt, und es wird beschrieben, wie sie im Designer verwendet werden.Diese Eigenschaften können im Eigenschaftenraster, einige davon auf der [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)]\-Designeroberfläche bearbeitet werden.  
  
|Eigenschaftenname|Erforderlich|Verwendung|  
|-----------------------|------------------|----------------|  
|<xref:System.Activities.Activity.DisplayName%2A>|False|Der Anzeigename der <xref:System.Activities.Statements.Delay>\-Aktivität.Der Standardwert lautet Delay.Obwohl der <xref:System.Activities.Activity.DisplayName%2A>\-Wert nicht zwingend erforderlich ist, wird empfohlen, einen Anzeigenamen zu verwenden.|  
|<xref:System.Activities.Statements.Delay.Duration%2A>|True|Die Zeitspanne, um die der Workflow verzögert werden soll.Diese Eigenschaft wird im Eigenschaftenraster festgelegt.Geben Sie in entweder einen literalen <xref:System.TimeSpan>\-Wert im Format 00:00:00 oder einem Visual Basic\-Ausdruck ein, um die Zeitspanne anzugeben.|  
  
## Siehe auch  
 [Primitive](../workflow-designer/primitives-activity-designers.md)   
 [Assign](../workflow-designer/assign-activity-designer.md)   
 [Delay Activity Designer](../workflow-designer/delay-activity-designer.md)   
 [InvokeMethod](../workflow-designer/invokemethod-activity-designer.md)   
 [WriteLine](../workflow-designer/writeline-activity-designer.md)