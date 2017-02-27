---
title: "Parallel-Aktivit&#228;tsdesigner | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "System.Activities.Statements.Parallel.UI"
ms.assetid: 0306dc3b-075a-4091-ac3a-96486fbabed5
caps.latest.revision: 10
author: "ErikRe"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 10
---
# Parallel-Aktivit&#228;tsdesigner
Die <xref:System.Activities.Statements.Parallel>\-Aktivität führt eine Sammlung von untergeordneten Aktivitäten parallel aus.  
  
## Die Parallel\-Aktivität  
 Die <xref:System.Activities.Statements.Parallel>\-Aktivität speichert ihre untergeordneten Aktivitäten in einer <xref:System.Activities.Statements.Parallel.Branches%2A>\-Auflistung.Verwenden Sie die <xref:System.Activities.Statements.Parallel>\-Aktivität statt der <xref:System.Activities.Statements.Sequence>\-Aktivität, wenn einige der untergeordneten Aktivitäten sich möglicherweise im Leerlauf befinden könnten.  
  
 Die <xref:System.Activities.Statements.Parallel>\-Aktivität verfügt über eine <xref:System.Activities.Statements.Parallel.CompletionCondition%2A>\-Eigenschaft, die einen benutzerspezifischen [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)]\-Ausdruck enthält.Die <xref:System.Activities.Statements.Parallel>\-Aktivität wertet diese Eigenschaft nach Abschluss jeder Verzweigung aus.Wenn die Eigenschaft **True** ergibt, dann wird die <xref:System.Activities.Statements.Parallel>\-Aktivität abgeschlossen, ohne die anderen Verzweigungen auszuführen.Wenn <xref:System.Activities.Statements.Parallel.CompletionCondition%2A> nicht den Wert **True** ergibt, dann wird die <xref:System.Activities.Statements.Parallel>\-Aktivität abgeschlossen, sobald alle ihre untergeordneten Aktivitäten abgeschlossen sind.  
  
### Verwenden des Parallel\-Aktivitätsdesigners  
 Der **Parallel**\-Aktivitätsdesigner befindet sich in der Kategorie **Ablaufsteuerung** der **Toolbox**, auf die Sie zugreifen können, indem Sie auf der linken Seite von [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)] auf die Registerkarte **Toolbox** klicken \(Sie können auch im Menü **Ansicht** den Befehl **Symbolleiste** auswählen oder STRG\+ALT\+X drücken\).  
  
 Der **Parallel**\-Aktivitätsdesigner kann aus der **Toolbox** gezogen und auf der [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)]\-Oberfläche dort abgelegt werden, wo Aktivitätsdesigner normalerweise platziert werden, z. B. innerhalb eines **Sequence**\-Aktivitätsdesigners.Nachdem der Aktivitätsdesigner in [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)] abgelegt wurde, erstellt er eine <xref:System.Activities.Statements.Parallel>\-Aktivität mit dem standardmäßigen <xref:System.Activities.Activity.DisplayName%2A> des Typs **Parallel**  
  
 Um der <xref:System.Activities.Statements.Parallel.Branches%2A>\-Auflistung der parallelen Aktivität eine Aktivität hinzuzufügen, ziehen Sie einen beliebigen anderen Aktivitätsdesigner aus der **Toolbox**, und legen Sie ihn auf dem Dreieck innerhalb des **Parallel**\-Aktivitätsdesigners ab.Die Dreiecke flankieren die in den Verzweigungen enthaltenen Aktivitäten.Zusätzliche Aktivitäten können hinzugefügt werden, indem diese Prozedur wiederholt wird.Die Aktivitäten können durch Drag & Drop innerhalb des **Parallel**\-Aktivitätsdesigners neu angeordnet werden.  
  
### Eigenschaften der Parallel\-Aktivität im Workflow\-Designer  
 In der folgenden Tabelle werden die nützlichsten Eigenschaften der Parallel\-Aktivität aufgeführt, und es wird beschrieben, wie sie im Designer verwendet werden.  
  
|Eigenschaftenname|Erforderlich|Verwendung|  
|-----------------------|------------------|----------------|  
|<xref:System.Activities.Activity.DisplayName%2A>|False|Gibt den benutzerfreundlichen Anzeigenamen des Aktivitätsdesigners im Header an.Der Standardwert lautet **Parallel**.Der Wert kann optional im Raster **Eigenschaften** oder direkt im Header des Aktivitätsdesigners bearbeitet werden.|  
|<xref:System.Activities.Statements.Parallel.Branches%2A>|True|Enthält die Auflistung von untergeordneten Aktivitäten, die ausgeführt werden sollen.|  
|<xref:System.Activities.Statements.Parallel.CompletionCondition%2A>|False|Die Auswertung erfolgt nach Beendigung einer Verzweigung.Ergibt die Auswertung **True**, werden die geplanten ausstehenden Verzweigungen abgebrochen.Wenn diese Eigenschaft nicht festgelegt ist oder **False** ergibt, dann wird die Aktivität abgeschlossen, sobald alle ihre untergeordneten Aktivitäten abgeschlossen sind.Der Standardwert ist **null**.|  
  
## Siehe auch  
 [Sequence](../workflow-designer/sequence-activity-designer.md)   
 [ParallelForEach\<T\>](../workflow-designer/parallelforeach-t-activity-designer.md)   
 [Ablaufsteuerung](../workflow-designer/control-flow-activity-designers.md)