---
title: "If-Aktivit&#228;tsdesigner | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "System.Activities.Statements.If.UI"
ms.assetid: 930a8fa2-db98-43e9-ad6d-a85cc7a6519a
caps.latest.revision: 4
caps.handback.revision: 4
author: "ErikRe"
ms.author: "erikre"
manager: "erikre"
---
# If-Aktivit&#228;tsdesigner
Die <xref:System.Activities.Statements.If>\-Aktivität wertet eine Bedingung aus und führt eine Aktivität aus, die von den Ergebnissen dieser Auswertung abhängig ist.Bei Verwendung eines Programmierstils nach Art der Verfahrensmodellierung ist diese Aktivität höchst nützlich.Eine <xref:System.Activities.Statements.If>\-Aktivität kann in eine <xref:System.Activities.Statements.Sequence>\-Aktivität oder beispielsweise eine <xref:System.Activities.Statements.Parallel>\-Aktivität geschachtelt werden.Wenn Sie eine <xref:System.Activities.Statements.Flowchart>\-Aktivität verwenden, sollten Sie in Erwägung ziehen, stattdessen eine <xref:System.Activities.Statements.FlowDecision>\-Aktivität zu verwenden.  
  
## If\- Eigenschaften im Workflow\-Designer  
 In der folgenden Tabelle werden die nützlichsten Eigenschaften der <xref:System.Activities.Statements.If>\-Aktivität aufgeführt, und es wird beschrieben, wie sie im Designer verwendet werden.  
  
|Eigenschaftenname|Erforderlich|Verwendung|  
|-----------------------|------------------|----------------|  
|<xref:System.Activities.Statements.If.Condition%2A>|True|Die Bedingung, die die auszuführende untergeordnete Aktivität bestimmt.Um die <xref:System.Activities.Statements.If.Condition%2A>\-Bedingung festzulegen, geben Sie im Feld **Bedingung** im **If**\-Aktivitätsdesigner oder im Eigenschaftenraster einen [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)]\-Ausdruck ein.|  
|<xref:System.Activities.Statements.If.Else%2A>|False|Die Aktivität, die ausgeführt werden soll, wenn der <xref:System.Activities.Statements.If.Condition%2A>\-Ausdruck **false** ist.Um eine Aktivität hinzuzufügen, die vom <xref:System.Activities.Statements.If.Else%2A>\-Zweig ausgeführt wird, legen Sie eine Aktivität aus der **Toolbox** im **If**\-Aktivitätsdesigner auf dem Feld **Else** mit dem Hinweistext "Aktivität hier ablegen" ab.|  
|<xref:System.Activities.Statements.If.Then%2A>|False|Die Aktivität, die ausgeführt werden soll, wenn <xref:System.Activities.Statements.If.Condition%2A>**true** ist.Um eine Aktivität hinzuzufügen, die vom <xref:System.Activities.Statements.If.Then%2A>\-Zweig ausgeführt wird, legen Sie eine Aktivität aus der **Toolbox** im **If**\-Aktivitätsdesigner auf dem Feld **Then** mit dem Hinweistext "Aktivität hier ablegen" ab.|  
  
## Siehe auch  
 [Sequence](../workflow-designer/sequence-activity-designer.md)   
 [Parallel](../workflow-designer/parallel-activity-designer.md)   
 [Ablaufsteuerung](../workflow-designer/control-flow-activity-designers.md)