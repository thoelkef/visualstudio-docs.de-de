---
title: "DoWhile-Aktivit&#228;tsdesigner | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "System.Activities.Statements.DoWhile.UI"
ms.assetid: 948deb35-d72f-462b-bea6-4b119c10a148
caps.latest.revision: 7
author: "ErikRe"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 7
---
# DoWhile-Aktivit&#228;tsdesigner
Die <xref:System.Activities.Statements.DoWhile>\-Aktivität führt die in ihrem <xref:System.Activities.Statements.DoWhile.Body%2A>\-Element enthaltene Aktivität mindestens einmal aus, bis eine angegebene Bedingung **false** ergibt.Wenn die in einem Schleifentext enthaltene Anwendung der 0 \(null\) oder mehrmals ausgeführt werden soll, verwenden Sie stattdessen die <xref:System.Activities.Statements.While>\-Aktivität.  
  
## DoWhile\- Eigenschaften im Workflow\-Designer  
 In der folgenden Tabelle werden die nützlichsten Eigenschaften der <xref:System.Activities.Statements.DoWhile>\-Aktivität aufgeführt, und es wird beschrieben, wie sie im Designer verwendet werden.  
  
|Eigenschaftenname|Erforderlich|Verwendung|  
|-----------------------|------------------|----------------|  
|<xref:System.Activities.Statements.DoWhile.Body%2A>|False|Die Aktivität, die ausgeführt werden soll, solange die Bedingung  **true** ist.Sie fügen die <xref:System.Activities.Statements.DoWhile.Body%2A>\-Aktivität hinzu, indem Sie eine Aktivität aus der Toolbox in den **DoWhile**\-Aktivitätsdesigner in das Feld **Body** mit dem Hinweistext "Aktivität hier ablegen" ziehen.|  
|<xref:System.Activities.Statements.DoWhile.Condition%2A>|True|Die Bedingung, die nach jedem Schleifendurchlauf ausgewertet werden soll.Um die <xref:System.Activities.Statements.DoWhile.Condition%2A>\-Bedingung festzulegen, geben Sie im Feld **Bedingung** im **DoWhile**\-Aktivitätsdesigner oder im Eigenschaftenraster einen [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)]\-Ausdruck ein.|  
  
## Siehe auch  
 [While](../workflow-designer/while-activity-designer.md)   
 [Ablaufsteuerung](../workflow-designer/control-flow-activity-designers.md)