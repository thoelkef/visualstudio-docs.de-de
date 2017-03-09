---
title: "Pick-Aktivit&#228;tsdesigner | Microsoft Docs"
ms.custom: ""
ms.date: "12/08/2016"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "System.Activities.Statements.Pick.UI"
ms.assetid: 642c0a47-1b47-45de-a19a-ca0606cedd7a
caps.latest.revision: 9
caps.handback.revision: 9
author: "ErikRe"
ms.author: "erikre"
manager: "erikre"
---
# Pick-Aktivit&#228;tsdesigner
Die <xref:System.Activities.Statements.Pick>\-Aktivität stellt eine ereignisbasierte Ablaufsteuerung bereit.Die Aktivität führt eine von mehreren Verzweigungen als Reaktion auf die Auslösung eines Ereignisses aus.  
  
## Die Pick\-Aktivität  
 Eine <xref:System.Activities.Statements.Pick>\-Aktivität enthält eine Auflistung von <xref:System.Activities.Statements.PickBranch>\-Objekten, von denen die <xref:System.Activities.Statements.Pick>\-Aktivität eines ausführen kann, wenn sie ein Ereignis empfängt, das als Trigger dient.Auf diese Weise stellt [!INCLUDE[wfd1](../workflow-designer/includes/wfd1_md.md)] eine ereignisbasierte Ablaufsteuerungsmodellierung bereit.Jede <xref:System.Activities.Statements.PickBranch> enthält einen <xref:System.Activities.Statements.PickBranch.Trigger%2A> und eine <xref:System.Activities.Statements.PickBranch.Action%2A>.Am Anfang der Ausführung eines <xref:System.Activities.Statements.Pick>\-Aktivität werden sämtliche Triggeraktivitäten der <xref:System.Activities.Statements.PickBranch>\-Elemente geplant.Wenn die erste Aktivität abgeschlossen wird, wird die entsprechende Aktionsaktivität geplant, und alle anderen Triggeraktivitäten werden abgebrochen.  
  
### So verwenden Sie den Pick\-Aktivitätsdesigner  
 Der **Pick**\-Aktivitätsdesigner befindet sich in die Kategorie **Ablaufsteuerung** der **Toolbox**, auf Sie zugreifen, indem Sie in [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)] auf die Registerkarte **Toolbox** klicken. \(Sie können auch im Menü **Ansicht** den Befehl **Toolbox** auswählen oder STRG\+ALT\+X drücken.\)  
  
 Der **Pick**\-Aktivitätsdesigner kann aus der **Toolbox** gezogen und auf der [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)]\-Oberfläche dort abgelegt werden, wo Aktivitätsdesigner normalerweise platziert werden, z. B. innerhalb eines **Sequence**\-Aktivitätsdesigners.Nachdem er in [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)] abgelegt wurde, wird eine <xref:System.Activities.Statements.Pick>\-Aktivität erstellt, die standardmäßig zwei leere <xref:System.Activities.Statements.PickBranch>\-Aktivitäten als Elemente mit den Anzeigenamen von Branch1 und Branch2 enthält.Die jeweiligen <xref:System.Activities.Statements.PickBranch.DisplayName%2A>\-Eigenschaftswerte können im Header des **PickBranch**\-Aktivitätsdesigner oder innerhalb des **Eigenschaftenfensters** für jede Verzweigung bearbeitet werden.  
  
 Es gibt zwei Möglichkeiten, <xref:System.Activities.Statements.PickBranch>\-Aktivitäten der Auflistung eines <xref:System.Activities.Statements.Pick>\-Objekts hinzuzufügen: Indem Sie einen **PickBranch**\-Designer aus der **Toolbox** ziehen und ablegen oder indem Sie das Kontextmenü der **Pick**\-Entwurfsoberfläche verwenden.Ausführliche Informationen finden Sie unter dem Thema [PickBranch](../workflow-designer/pickbranch-activity-designer.md).Beachten Sie, dass als einziges Element ein **PickBranch**\-Aktivitätsdesigner in einem **Pick**\-Aktivitätsdesigner platziert werden kann.  
  
### Eigenschaften für Pick\-Aktivitäten im Workflow\-Designer  
 In der folgenden Tabelle werden die <xref:System.Activities.Statements.Pick>\-Eigenschaften aufgeführt, und es wird beschrieben, wie sie im Designer verwendet werden.Diese Eigenschaften können im Eigenschaftenraster oder auf der Designeroberfläche bearbeitet werden.  
  
|Eigenschaftenname|Erforderlich|Verwendung|  
|-----------------------|------------------|----------------|  
|<xref:System.Activities.Activity.DisplayName%2A>|False|Gibt den benutzerfreundlichen Namen der <xref:System.Activities.Statements.Pick>Aktivität im Header an.Der Standardwert lautet Pick.Der Wert kann im Eigenschaftenraster oder direkt im Header des Aktivitätsdesigners bearbeitet werden.<br /><br /> Obwohl der <xref:System.Activities.Activity.DisplayName%2A> nicht zwingend erforderlich ist, wird empfohlen, einen Anzeigenamen zu verwenden.|  
  
## Siehe auch  
 [Ablaufsteuerung](../workflow-designer/control-flow-activity-designers.md)   
 [Auswählen der Aktivität](../Topic/Pick%20Activity.md)   
 [Verwenden der Pick\-Aktivität](../Topic/Using%20the%20Pick%20Activity.md)