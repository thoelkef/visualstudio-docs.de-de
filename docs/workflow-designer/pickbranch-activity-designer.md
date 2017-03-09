---
title: "PickBranch-Aktivit&#228;tsdesigner | Microsoft Docs"
ms.custom: ""
ms.date: "12/08/2016"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "System.Activities.Statements.PickBranch.UI"
ms.assetid: f523ad47-bbc0-4cda-a35c-41e67c4ba081
caps.latest.revision: 10
caps.handback.revision: 10
author: "ErikRe"
ms.author: "erikre"
manager: "erikre"
---
# PickBranch-Aktivit&#228;tsdesigner
Der <xref:System.Activities.Statements.PickBranch> stellt einen ereignisbasierten Ausführungspfad innerhalb einer <xref:System.Activities.Statements.Pick>\-Aktivität bereit, der von einem eingehenden Ereignis ausgelöst werden kann.  
  
## PickBranch  
 <xref:System.Activities.Statements.PickBranch>\-Objekte sind in der <xref:System.Activities.Statements.Pick.Branches%2A>\-Auflistung einer <xref:System.Activities.Statements.Pick>\-Aktivität enthalten.Jede <xref:System.Activities.Statements.PickBranch> ist in einer Verzweigung der <xref:System.Activities.Statements.Pick>\-Aktivität enthalten und wird aufgrund eines eingehenden Ereignisses ausgeführt, das als Trigger dient.Auf diese Weise stellt [!INCLUDE[wfd1](../workflow-designer/includes/wfd1_md.md)] ereignisbasierte Ablaufsteuerungsmodellierung bereit.Jede <xref:System.Activities.Statements.PickBranch> enthält einen <xref:System.Activities.Statements.PickBranch.Trigger%2A> und eine <xref:System.Activities.Statements.PickBranch.Action%2A>.  
  
### So verwenden Sie den Pick\-Aktivitätsdesigner  
 Der **PickBranch**\-Designer befindet sich in der Kategorie **Ablaufsteuerung** der **Toolbox**, auf die Sie zugreifen können, indem Sie in [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)] auf die Registerkarte **Toolbox** klicken \(Sie können auch im Menü **Ansicht** den Befehl **Symbolleiste** auswählen oder STRG\+ALT\+X drücken\).  
  
 Sobald der **Pick**\-Aktivitätsdesigner auf [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)] abgelegt wird, werden standardmäßig zwei leere <xref:System.Activities.Statements.PickBranch>\-Objekte mit den Anzeigenamen **Branch1** und **Branch2** als Elemente einer <xref:System.Activities.Statements.Pick>\-Aktivität erstellt.Die jeweiligen <xref:System.Activities.Statements.PickBranch.DisplayName%2A>\-Eigenschaftswerte können im Header des **PickBranch**\-Designers oder innerhalb des **Eigenschaftenfensters** für jede Verzweigung bearbeitet werden.  
  
 Es gibt zwei Möglichkeiten, <xref:System.Activities.Statements.PickBranch>\-Objekte der Auflistung eines <xref:System.Activities.Statements.Pick>\-Objekts hinzuzufügen: Indem Sie einen **PickBranch**\-Designer aus der **Toolbox** ziehen und ablegen oder indem Sie das Kontextmenü der **Pick**\-Entwurfsoberfläche verwenden:  
  
1.  Der **PickBranch**\-Designer erstellt ein <xref:System.Activities.Statements.PickBranch>\-Objekt, wenn er aus der **Toolbox** gezogen und in einer der Verzweigungen eines **Pick**\-Aktivitätsdesigners auf der [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)]\-Oberfläche abgelegt wird.Die neuen <xref:System.Activities.Statements.PickBranch>\-Objekte können im <xref:System.Activities.Statements.Pick>\-Designer auf der linken oder rechten Seite jedes <xref:System.Activities.Statements.PickBranch>\-Elements platziert werden, das bereits in der Auflistung enthalten ist.Wird ein **PickBranch**\-Designer mit der Maus auf einen **Pick**\-Designer gezogen, zeigt der **Pick\-Designer** mithilfe eines vertikalen blaugrauen Bands an, wo entsprechend der gegebenen Mausposition das <xref:System.Activities.Statements.PickBranch>\-Objekt hinzugefügt wird.  
  
2.  Klicken Sie mit der rechten Maustaste auf den **Pick**\-Aktivitätsdesigner \(jedoch nicht im **PickBranch**\-Designer\), um ein Kontextmenü anzuzeigen, in dem Sie **Verzweigung erstellen** auswählen, um eine neue <xref:System.Activities.Statements.PickBranch> hinzuzufügen.Beachten Sie, dass das neue <xref:System.Activities.Statements.PickBranch>\-Objekt im **Pick**\-Designer rechts neben den vorhandenen <xref:System.Activities.Statements.PickBranch>\-Objekten hinzugefügt wird.  
  
 Der **PickBranch**\-Designer kann erweitert werden, damit die Felder **Trigger** und **Aktion** angezeigt werden, oder er kann durch Klicken auf die doppelten Caretzeichen auf der rechten Seite ihrer Header reduziert werden.Bearbeiten Sie den <xref:System.Activities.Statements.PickBranch.Trigger%2A> und die <xref:System.Activities.Statements.PickBranch.Action%2A> jedes <xref:System.Activities.Statements.PickBranch>\-Objekts, indem Sie Aktivitäten in den Feldern **Trigger** und **Aktion** ihrer Designer ablegen.  
  
 Die <xref:System.Activities.Statements.PickBranch>\-Objekte in der <xref:System.Activities.Statements.Pick.Branches%2A>\-Auflistung eines <xref:System.Activities.Statements.Pick>\-Objekts können durch Ziehen und Ablegen in eine neue Position innerhalb des **Pick**\-Designers verschoben werden.Der **Pick\-Designer** zeigt mithilfe eines vertikalen blaugrauen Bands an, wo entsprechend der gegebenen Mausposition das <xref:System.Activities.Statements.PickBranch>\-Objekt hinzugefügt wird.  
  
 Es gibt zwei Möglichkeiten, ein <xref:System.Activities.Statements.PickBranch>\-Objekt zu löschen:  
  
1.  Wählen Sie den **PickBranch**\-Designer aus, und löschen Sie es.  
  
2.  Wählen Sie den **PickBranch**\-Designer aus, klicken Sie mit der rechten Maustaste, und wählen Sie im Kontextmenü den Befehl **Löschen** aus.  
  
 Vergewissern Sie sich, dass Sie den **PickBranch**\-Designer ausgewählt haben, denn das versehentliche Auswählen einer der Aktivitäten in dessen **Trigger**\- oder **Aktion**\-Feld löscht diese Aktivitäten und nicht das <xref:System.Activities.Statements.PickBranch>\-Objekt.  
  
### PickBranch\-Eigenschaften im Workflow\-Designer  
 In der folgenden Tabelle werden die nützlichsten Eigenschaften von <xref:System.Activities.Statements.PickBranch> aufgeführt, und es wird beschrieben, wie sie in [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)] verwendet werden.  
  
|Eigenschaftenname|Erforderlich|Verwendung|  
|-----------------------|------------------|----------------|  
|<xref:System.Activities.Statements.PickBranch.DisplayName%2A>|False|Der im Header des **PickBranch**\-Designers angezeigte benutzerfreundliche Name.Der Standardwert lautet Branch.<br /><br /> Obwohl der <xref:System.Activities.Activity.DisplayName%2A> nicht zwingend erforderlich ist, wird empfohlen, einen Anzeigenamen zu verwenden.|  
|<xref:System.Activities.Statements.PickBranch.Trigger%2A>|True|Jedes <xref:System.Activities.Statements.PickBranch>\-Objekt enthält eine <xref:System.Activities.Statements.PickBranch.Trigger%2A>\-Aktion, die <xref:System.Activities.Statements.PickBranch.Action%2A> aufrufen kann.|  
|<xref:System.Activities.Statements.PickBranch.Action%2A>|False|Jede <xref:System.Activities.Statements.PickBranch>\-Objekt enthält eine <xref:System.Activities.Statements.PickBranch.Action%2A>, die ausgeführt wird, sobald sie ausgelöst wird.|  
  
## Siehe auch  
 [Ablaufsteuerung](../workflow-designer/control-flow-activity-designers.md)   
 [Auswählen der Aktivität](../Topic/Pick%20Activity.md)   
 [Verwenden der Pick\-Aktivität](../Topic/Using%20the%20Pick%20Activity.md)