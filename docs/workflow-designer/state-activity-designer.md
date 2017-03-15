---
title: "Zustandsaktivit&#228;ts-Designer | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "System.Activities.Statements.State.UI"
ms.assetid: 9455ab37-93a0-4c46-9eb8-b6611ca23167
caps.latest.revision: 5
ms.author: "sdanie"
manager: "erikre"
caps.handback.revision: 5
---
# Zustandsaktivit&#228;ts-Designer
<xref:System.Activities.Statements.State> stellt einen Zustand dar, in dem sich ein Zustandsautomat befinden kann.  
  
## Verwenden des State\-Aktivitätsdesigners  
 Um einem Workflow <xref:System.Activities.Statements.State> hinzuzufügen, ziehen Sie den **State**\-Aktivitätsdesigner aus dem Abschnitt **State Machine** der **Toolbox** und legen ihn auf einer <xref:System.Activities.Statements.StateMachine>\-Aktivität auf der [!INCLUDE[wfd1](../workflow-designer/includes/wfd1_md.md)]\-Oberfläche ab.Eine <xref:System.Activities.Statements.State>\-Aktivität kann auf <xref:System.Activities.Statements.StateMachine> abgelegt werden, und es können später Übergänge hinzugefügt oder ein Übergang erstellt werden, wenn die <xref:System.Activities.Statements.State>\-Aktivität abgelegt wird.Um in einem Schritt eine <xref:System.Activities.Statements.State>\-Aktivität hinzuzufügen und einen Übergang zu erstellen, ziehen Sie eine **State**\-Aktivität aus dem Abschnitt **State Machine** der **Toolbox** und bewegen sie über einen anderen Zustand im Workflow\-Designer.Sobald sich der gezogene <xref:System.Activities.Statements.State> über einem anderen <xref:System.Activities.Statements.State> befindet, werden vier Dreiecke um den anderen <xref:System.Activities.Statements.State> herum eingeblendet.Wenn <xref:System.Activities.Statements.State> auf einem der vier Dreiecke abgelegt wird, wird er dem Zustandsautomat hinzugefügt, und es wird ein Übergang vom Quell\-<xref:System.Activities.Statements.State> zum abgelegten Ziel\-<xref:System.Activities.Statements.State> erstellt.Weitere Informationen finden Sie unter [Übergang](../workflow-designer/transition-activity-designer.md).  
  
### Eigenschaften für State\-Aktivitäten im Workflow\-Designer  
 In der folgenden Tabelle sind die <xref:System.Activities.Statements.State>\-Eigenschaften aufgeführt, die mithilfe des Workflow\-Designers festgelegt werden können, und es wird beschrieben, wie sie im Designer verwendet werden.Einige Eigenschaften können im Eigenschaftenraster und einige auf der Designeroberfläche bearbeitet werden.  
  
|Eigenschaftenname|Erforderlich|Verwendung|  
|-----------------------|------------------|----------------|  
|<xref:System.Activities.Statements.State.DisplayName%2A>|False|Gibt den Anzeigenamen des <xref:System.Activities.Statements.State>\-Aktivitätsdesigners im Header an.Der Standardwert lautet **State** .Der Wert kann im Eigenschaftenraster oder direkt im Header des Aktivitätsdesigners bearbeitet werden.<xref:System.Activities.Statements.State.DisplayName%2A> wird in der Breadcrumbnavigation verwendet, die am oberen Rand des Workflow\-Designers angezeigt wird.<br /><br /> Obwohl der <xref:System.Activities.Statements.State.DisplayName%2A> nicht zwingend erforderlich ist, wird empfohlen, einen Anzeigenamen zu verwenden.|  
|<xref:System.Activities.Statements.State.Entry%2A>|False|Gibt die Aktion an, die eintritt, wenn ein Übergang in diesen Zustand stattfindet.Wenn die <xref:System.Activities.Statements.State>\-Aktivität erweitert wird, kann dieser Wert festgelegt werden, indem Sie eine Aktivität aus der **Toolbox** ziehen und sie auf dem Abschnitt **Eingabe** des Zustands ablegen.|  
|<xref:System.Activities.Statements.State.Exit%2A>|False|Gibt die Aktion an, die eintritt, wenn ein Übergang aus diesem Zustand stattfindet.Wenn die <xref:System.Activities.Statements.State>\-Aktivität erweitert wird, kann dieser Wert festgelegt werden, indem Sie eine Aktivität aus der **Toolbox** ziehen und sie auf dem Abschnitt **Exit** des Zustands ablegen.|  
|<xref:System.Activities.Statements.State.Transitions%2A>|False|Listet die möglichen Übergänge auf, die von <xref:System.Activities.Statements.State> ausgehen.Jedes Element in der Liste weist einen Link zum verknüpften <xref:System.Activities.Statements.Transition> und zum Ziel\-<xref:System.Activities.Statements.State> auf.Indem Sie auf den Link klicken, wechselt der Designer zur erweiterten Ansicht von <xref:System.Activities.Statements.Transition> oder <xref:System.Activities.Statements.State>.|  
  
## Siehe auch  
 [StateMachine](../workflow-designer/statemachine-activity-designer.md)   
 [FinalState](../workflow-designer/finalstate-activity-designer.md)   
 [Übergang](../workflow-designer/transition-activity-designer.md)