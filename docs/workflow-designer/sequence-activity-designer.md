---
title: "Sequence-Aktivit&#228;tsdesigner | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "System.Activities.Statements.Sequence.UI"
ms.assetid: 51c8d3cb-4d43-458f-9631-b63755f9ac94
caps.latest.revision: 5
author: "ErikRe"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 5
---
# Sequence-Aktivit&#228;tsdesigner
Die <xref:System.Activities.Statements.Sequence>\-Aktivität enthält eine geordnete Auflistung von untergeordneten Aktivitäten, die in der angegebenen Reihenfolge ausgeführt werden.  
  
 Eine andere Möglichkeit, eine Gruppe von Aktivitäten in einer bestimmten Reihenfolge auszuführen, besteht in der Verwendung einer <xref:System.Activities.Statements.Flowchart>\-Aktivität.Ziehen Sie in Erwägung, [Flussdiagramm](../workflow-designer/flowchart-activity-designer.md) zu verwenden, wenn Sie eine einfache Verzweigung oder einen Programmablauf mit einer Schleife graphisch modellieren möchten.  
  
## Verwenden des Sequence\-Aktivitätsdesigners  
 Um eine <xref:System.Activities.Statements.Sequence>\-Aktivität hinzuzufügen, ziehen Sie den **Sequence**\-Aktivitätsdesigner aus der **Toolbox** und legen ihn auf der [!INCLUDE[wfd1](../workflow-designer/includes/wfd1_md.md)]\-Oberfläche ab.Um dieser <xref:System.Activities.Statements.Sequence>\-Aktivität eine untergeordnete Aktivität hinzuzufügen, ziehen Sie eine andere Aktivität aus der **Toolbox**, und legen Sie sie auf dem Dreieck im Feld mit dem Hinweistext "Aktivität hier ablegen" ab.  
  
### Eigenschaften der Sequence\-Aktivität im Workflow\-Designer  
 In der folgenden Tabelle werden die Eigenschaften von <xref:System.Activities.Statements.Sequence> gezeigt und es wird beschrieben, wie sie im Designer verwendet werden.Diese Eigenschaften können im Eigenschaftenraster oder auf der Designeroberfläche bearbeitet werden.  
  
|Eigenschaftenname|Erforderlich|Verwendung|  
|-----------------------|------------------|----------------|  
|<xref:System.Activities.Activity.DisplayName%2A>|False|Gibt den Anzeigenamen des <xref:System.Activities.Statements.Sequence>\-Aktivitätsdesigners im Header an.Der Standardwert ist Sequence.Der Wert kann im Eigenschaftenraster oder direkt im Header des Aktivitätsdesigners bearbeitet werden.<br /><br /> Obwohl der <xref:System.Activities.Activity.DisplayName%2A> nicht zwingend erforderlich ist, wird empfohlen, einen Anzeigenamen zu verwenden.|  
  
## Siehe auch  
 [Flussdiagramm](../workflow-designer/flowchart-activity-designer.md)   
 [Ablaufsteuerung](../workflow-designer/control-flow-activity-designers.md)