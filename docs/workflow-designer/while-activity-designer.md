---
title: "While-Aktivit&#228;tsdesigner | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "System.Activities.Statements.While.UI"
ms.assetid: ea008091-2e4c-4f64-bfa5-afb919552446
caps.latest.revision: 5
caps.handback.revision: 5
author: "ErikRe"
ms.author: "erikre"
manager: "erikre"
---
# While-Aktivit&#228;tsdesigner
Die <xref:System.Activities.Statements.While>\-Aktivität führt die in ihrem <xref:System.Activities.Statements.While.Body%2A> enthaltene Aktivität aus, sofern die angegebene <xref:System.Activities.Statements.Condition%2A> den Wert **true** ergibt.Die enthaltene Aktivität wird möglicherweise nie ausgeführt.Wenn die enthaltene Aktivität wenigstens einmal ausgeführt werden soll, verwenden Sie stattdessen die <xref:System.Activities.Statements.DoWhile>\-Aktivität.  
  
## While\-Eigenschaften im Workflow\-Designer  
 In der folgenden Tabelle werden die nützlichsten Eigenschaften der <xref:System.Activities.Statements.While>\-Aktivität aufgeführt, und es wird beschrieben, wie sie im Designer verwendet werden.  
  
|Eigenschaftenname|Erforderlich|Verwendung|  
|-----------------------|------------------|----------------|  
|<xref:System.Activities.Activity.DisplayName%2A>|False|Gibt den benutzerfreundlichen Namen der <xref:System.Activities.Statements.While>Aktivität im Header an.Der Standardwert lautet While.Der Wert kann im **Eigenschaftenfenster** oder direkt im Header des Aktivitätsdesigners bearbeitet werden.<br /><br /> Obwohl der <xref:System.Activities.Activity.DisplayName%2A> nicht zwingend erforderlich ist, wird empfohlen, einen Anzeigenamen zu verwenden.|  
|<xref:System.Activities.Statements.While.Body%2A>|False|Enthält die Aktivität, die ausgeführt wird, wenn die <xref:System.Activities.Statements.Condition%2A> den Wert **true** ergibt.|  
|<xref:System.Activities.Statements.Condition%2A>|True|Enthält den [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)]\-Ausdruck, dessen Auswertung bestimmt, ob die Aktivität im <xref:System.Activities.Statements.While.Body%2A> ausgeführt wird.|  
  
## Siehe auch  
 [Ablaufsteuerung](../workflow-designer/control-flow-activity-designers.md)   
 [DoWhile](../workflow-designer/dowhile-activity-designer.md)