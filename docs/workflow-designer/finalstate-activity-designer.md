---
title: "FinalState-Aktivit&#228;ts-Designer | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
ms.assetid: aa186893-8775-40dd-981f-8593ead831d0
caps.latest.revision: 5
ms.author: "sdanie"
manager: "erikre"
caps.handback.revision: 5
---
# FinalState-Aktivit&#228;ts-Designer
Der <xref:System.Activities.Core.Presentation.FinalState>\-Designer wird verwendet, um einen <xref:System.Activities.Statements.State> zu erstellen, der eine Instanz des Zustandsautomaten beendet.  
  
## Verwenden des FinalState\-Aktivitätsdesigners  
 Der **FinalState**\-Designer wird verwendet, um einen <xref:System.Activities.Statements.State> zu erstellen, der als endender Zustand in einen Zustandsautomaten vorkonfiguriert ist.Bei einem <xref:System.Activities.Statements.State>, der mit dem <xref:System.Activities.Core.Presentation.FinalState>\-Aktivitätsdesigner erstellt wird, ist die <xref:System.Activities.Statements.State.IsFinal%2A>\-Eigenschaft auf **true** festgelegt, und er verfügt über keine <xref:System.Activities.Statements.State.Exit%2A>\-Aktivität und keine Übergänge, die davon ausgehen.Um den <xref:System.Activities.Core.Presentation.FinalState>\-Aktivitätsdesigner zu verwenden, um eine <xref:System.Activities.Statements.State>\-Aktivität hinzuzufügen, die in einem Zustandsautomat in einem endenden Zustand vorkonfiguriert ist, ziehen Sie den **FinalState**\-Aktivitätsdesigner aus dem Abschnitt **State Machine** der **Toolbox**, und legen ihn auf dem Workflow\-Designer ab.Der <xref:System.Activities.Core.Presentation.FinalState>\-Aktivitätsdesigner kann auf <xref:System.Activities.Statements.StateMachine> abgelegt werden, und es können später Übergänge hinzugefügt oder ein Übergang erstellt werden, wenn der <xref:System.Activities.Core.Presentation.FinalState>\-Aktivitätsdesigner abgelegt wird.Weitere Informationen zur Erstellung von Übergängen finden Sie unter [Übergang](../workflow-designer/transition-activity-designer.md).  
  
### Eigenschaften für State\-Aktivitäten im Workflow\-Designer  
 In der folgenden Tabelle sind die Eigenschaften aufgeführt, die mithilfe des <xref:System.Activities.Core.Presentation.FinalState>\-Designers festgelegt werden können, und es wird beschrieben, wie sie im Designer verwendet werden.Einige Eigenschaften können im Eigenschaftenraster und einige auf der Designeroberfläche bearbeitet werden.  
  
|Eigenschaftenname|Erforderlich|Verwendung|  
|-----------------------|------------------|----------------|  
|<xref:System.Activities.Statements.State.DisplayName%2A>|False|Gibt den Anzeigenamen des <xref:System.Activities.Statements.State>\-Aktivitätsdesigners im Header an.Der Standardwert lautet **State** .Der Wert kann im Eigenschaftenraster oder direkt im Header des Aktivitätsdesigners bearbeitet werden.<xref:System.Activities.Statements.State.DisplayName%2A> wird in der Breadcrumbnavigation verwendet, die am oberen Rand des Workflow\-Designers angezeigt wird.<br /><br /> Obwohl der <xref:System.Activities.Statements.State.DisplayName%2A> nicht zwingend erforderlich ist, wird empfohlen, einen Anzeigenamen zu verwenden.|  
|<xref:System.Activities.Statements.State.Entry%2A>|False|Gibt die Aktion an, die eintritt, wenn ein Übergang in diesen Zustand stattfindet.Dieser Wert kann festgelegt werden, indem Sie eine Aktivität aus der **Toolbox** ziehen und auf dem Abschnitt <xref:System.Activities.Statements.State.Entry%2A> des Zustands ablegen.|  
  
## Siehe auch  
 [StateMachine](../workflow-designer/statemachine-activity-designer.md)   
 [Zustand](../workflow-designer/state-activity-designer.md)   
 [Übergang](../workflow-designer/transition-activity-designer.md)