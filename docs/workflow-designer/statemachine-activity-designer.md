---
title: "StateMachine-Aktivit&#228;ts-Designer | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "StateMachine Designer"
  - "System.Activities.Statements.StateMachine.UI"
ms.assetid: 474d5fb3-1049-4b3f-bc6b-7524dbbe1672
caps.latest.revision: 5
ms.author: "sdanie"
manager: "erikre"
caps.handback.revision: 5
---
# StateMachine-Aktivit&#228;ts-Designer
Die <xref:System.Activities.Statements.StateMachine>\-Aktivität enthält eine Auflistung von Zustands\- und Modellworkflows, die das bekannte Zustandsautomatparadigma verwenden.  
  
## Verwenden des StateMachine\-Aktivitätsdesigners  
 Um eine <xref:System.Activities.Statements.StateMachine>\-Aktivität hinzuzufügen, ziehen Sie den **StateMachine**\-Aktivitätsdesigner aus dem Abschnitt **State Machine** der **Toolbox** und legen sie auf der [!INCLUDE[wfd1](../workflow-designer/includes/wfd1_md.md)]\-Oberfläche ab.Um dieser <xref:System.Activities.Statements.StateMachine>\-Aktivität einen untergeordneten Zustand hinzuzufügen, ziehen Sie <xref:System.Activities.Statements.State> oder <xref:System.Activities.Core.Presentation.FinalState> aus der **Toolbox**, und legen Sie ihn auf **StateMachine** ab.  
  
### Eigenschaften der StateMachine\-Aktivität im Workflow\-Designer  
 In der folgenden Tabelle sind die <xref:System.Activities.Statements.StateMachine>\-Eigenschaften aufgeführt, die mithilfe des Workflow\-Designers festgelegt werden können, und es wird beschrieben, wie sie im Designer verwendet werden.Diese Eigenschaften können im Eigenschaftenraster und einige können auf der Designeroberfläche bearbeitet werden.  
  
|Eigenschaftenname|Erforderlich|Verwendung|  
|-----------------------|------------------|----------------|  
|<xref:System.Activities.Activity.DisplayName%2A>|False|Gibt den Anzeigenamen des <xref:System.Activities.Statements.StateMachine>\-Aktivitätsdesigners im Header an.Der Standardwert ist **StateMachine**.Der Wert kann im Eigenschaftenraster oder direkt im Header des Aktivitätsdesigners bearbeitet werden.<xref:System.Activities.Activity.DisplayName%2A> wird in der Breadcrumbnavigation verwendet, die am oberen Rand des Workflow\-Designers angezeigt wird.<br /><br /> Obwohl der <xref:System.Activities.Activity.DisplayName%2A> nicht zwingend erforderlich ist, wird empfohlen, einen Anzeigenamen zu verwenden.|  
  
## Siehe auch  
 [Flussdiagramm](../workflow-designer/flowchart-activity-designer.md)   
 [Ablaufsteuerung](../workflow-designer/control-flow-activity-designers.md)