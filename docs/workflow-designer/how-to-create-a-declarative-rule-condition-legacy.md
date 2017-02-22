---
title: "Vorgehensweise: Erstellen einer deklarativen Regelbedingung (Vorg&#228;ngerversion) | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
helpviewer_keywords: 
  - "Bedingungsanweisungen, deklarative Regelbedingungen"
  - "deklarative Regelbedingungen"
  - "Regelbedingungs-Editor (Dialogfeld)"
ms.assetid: 804b6129-c433-408f-a424-46987967730c
caps.latest.revision: 5
caps.handback.revision: 5
author: "ErikRe"
ms.author: "erikre"
manager: "erikre"
---
# Vorgehensweise: Erstellen einer deklarativen Regelbedingung (Vorg&#228;ngerversion)
In diesem Thema wird beschrieben, wie eine Regelbedingung mithilfe der Vorgängerversion von [!INCLUDE[wfd1](../workflow-designer/includes/wfd1_md.md)] deklariert wird, die auf [!INCLUDE[netfx35_long](../workflow-designer/includes/netfx35_long_md.md)] oder [!INCLUDE[vstecwinfx](../workflow-designer/includes/vstecwinfx_md.md)] abzielt.  
  
 Eine Bedingungsanweisung ergibt **True** oder **False**.Eine deklarative Regelbedingung ist eine Bedingungsanweisung, die mit dem [Dialogfeld "Regelbedingungs\-Editor" \(Vorgängerversion\)](../workflow-designer/rule-condition-editor-dialog-box-legacy.md) erstellt und im XML\-Format mit dem Workflow gespeichert wird.Sie kann Prädikate beinhalten, mit denen Workflowstatus und boolesche Algebra verglichen werden, in der mehrere Prädikate kombiniert sind.  
  
 Deklarative Regelbedingungen werden in den folgenden vordefinierten Windows Workflow Foundation\-Aktivitäten verwendet:  
  
-   [ConditionedActivityGroup  \(Seite ist möglicherweise nur in englischer Sprache verfügbar.\)](http://go.microsoft.com/fwlink?LinkID=65017)  
  
-   [IfElseBranchActivity  \(Seite ist möglicherweise nur in englischer Sprache verfügbar.\)](http://go.microsoft.com/fwlink?LinkID=65034)  
  
-   [ReplicatorActivity  \(Seite ist möglicherweise nur in englischer Sprache verfügbar.\)](http://go.microsoft.com/fwlink?LinkID=65039)  
  
-   [WhileActivity \(Seite ist möglicherweise nur in englischer Sprache verfügbar.\)](http://go.microsoft.com/fwlink?LinkID=65049)  
  
-   [SequentialWorkflowActivity  \(Seite ist möglicherweise nur in englischer Sprache verfügbar.\)](http://go.microsoft.com/fwlink?LinkID=65040)  
  
-   [StateMachineWorkflowActivity  \(Seite ist möglicherweise nur in englischer Sprache verfügbar.\)](http://go.microsoft.com/fwlink?LinkID=65045)  
  
### So erstellen Sie eine deklarative Regelbedingung mit dem Regelbedingungs\-Editor  
  
1.  Klicken Sie im **Eigenschaftenfenster** der Aktivität auf die **Condition**\-Eigenschaft oder die **UntilCondition**\-Eigenschaft \(je nach Aktivität\).  
  
2.  Wählen Sie in der Liste für die Eigenschaft **Deklarative Regelbedingung**.  
  
3.  Erweitern Sie die **Condition**\-Eigenschaft oder die **UntilCondition**\-Eigenschaft.  
  
4.  Klicken Sie auf die **ConditionName**\-Eigenschaft.  
  
5.  Klicken Sie auf die Auslassungszeichen für **ConditionName\[…\]**, um das Dialogfeld **Bedingung auswählen** aufzurufen.  
  
6.  Klicken Sie auf **Neue Bedingung**, um das Dialogfeld **Regelbedingungs\-Editor** zu öffnen.  
  
7.  Geben Sie den Ausdruck für die Bedingung in das Textfeld **Bedingung** ein.  
  
     Informationen zum Erstellen von Bedingungsausdrücken finden Sie unter [Dialogfeld "Regelbedingungs\-Editor" \(Vorgängerversion\)](../workflow-designer/rule-condition-editor-dialog-box-legacy.md).  
  
8.  Wenn Sie die Erstellung des Bedingungsausdrucks abgeschlossen haben, klicken Sie auf **OK**, um das Dialogfeld zu schließen und die Regelbedingung mit einem zugewiesenen Namen zu erstellen.  
  
     Das Dialogfeld **Bedingung auswählen** wird geöffnet.  
  
     Informationen zur Verwendung des Dialogfelds **Bedingung auswählen** finden Sie unter [Dialogfeld "Regelbedingungs\-Editor auswählen" \(Vorgängerversion\)](../workflow-designer/select-condition-dialog-box-legacy.md).  
  
## Siehe auch  
 [Legacyworkflowaktivitäten](../workflow-designer/legacy-workflow-activities.md)   
 [Verwenden von ConditionedActivityGroup](http://go.microsoft.com/fwlink?LinkID=65066)   
 [Verwenden der IfElseBranchActivity\-Aktivität](http://go.microsoft.com/fwlink?LinkID=65075)   
 [Verwenden der Replicator\-Aktivität](http://go.microsoft.com/fwlink?LinkID=65080)   
 [Verwenden der While\-Aktivität](http://go.microsoft.com/fwlink?LinkID=65091)   
 [Dialogfeld "Regelbedingungs\-Editor" \(Vorgängerversion\)](../workflow-designer/rule-condition-editor-dialog-box-legacy.md)   
 [Dialogfeld "Regelbedingungs\-Editor auswählen" \(Vorgängerversion\)](../workflow-designer/select-condition-dialog-box-legacy.md)   
 [Verwenden der Bedingungen in Workflows](http://go.microsoft.com/fwlink?LinkID=65009)