---
title: "Vorgehensweise: erstellen eine deklarativen Regelbedingung (Vorgängerversion) | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
helpviewer_keywords:
- declarative rule conditions
- condition statements, declarative rule conditions
- Rule Condition Editor dialog box
ms.assetid: 804b6129-c433-408f-a424-46987967730c
caps.latest.revision: "5"
author: ErikRe
ms.author: erikre
manager: erikre
ms.openlocfilehash: 736c36df419d601c27998d8d34bde9abe5976a17
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/27/2017
---
# <a name="how-to-create-a-declarative-rule-condition-legacy"></a>Vorgehensweise: Erstellen einer deklarativen Regelbedingung (Vorgängerversion)
In diesem Thema wird beschrieben, wie eine Regelbedingung mithilfe der Vorgängerversion von [!INCLUDE[wfd1](../workflow-designer/includes/wfd1_md.md)] deklariert wird, die auf [!INCLUDE[netfx35_long](../workflow-designer/includes/netfx35_long_md.md)] oder [!INCLUDE[vstecwinfx](../workflow-designer/includes/vstecwinfx_md.md)] abzielt.  
  
 Eine bedingungsanweisung ergibt **"true"** oder **"false"**. Eine deklarative regelbedingung ist eine bedingungsanweisung, die erstellt wird die [Regelsatz Bedingung-Editor (Dialogfeld) (Legacy)](../workflow-designer/rule-condition-editor-dialog-box-legacy.md) und mit dem Workflow als XML gespeichert. Sie kann Prädikate beinhalten, mit denen Workflowstatus und boolesche Algebra verglichen werden, in der mehrere Prädikate kombiniert sind.  
  
 Deklarative Regelbedingungen werden in den folgenden vordefinierten Windows Workflow Foundation-Aktivitäten verwendet:  
  
-   [ConditionedActivityGroup](http://go.microsoft.com/fwlink?LinkID=65017)  
  
-   ["IfElseBranchActivity"](http://go.microsoft.com/fwlink?LinkID=65034)  
  
-   [ReplicatorActivity](http://go.microsoft.com/fwlink?LinkID=65039)  
  
-   [WhileActivity](http://go.microsoft.com/fwlink?LinkID=65049)  
  
-   [SequentialWorkflowActivity](http://go.microsoft.com/fwlink?LinkID=65040)  
  
-   [StateMachineWorkflowActivity](http://go.microsoft.com/fwlink?LinkID=65045)  
  
### <a name="to-create-a-declarative-rule-condition-using-the-rule-condition-editor"></a>So erstellen Sie eine deklarative Regelbedingung mit dem Regelbedingungs-Editor  
  
1.  In der Aktivitätssymbols **Eigenschaften** Fenster, klicken Sie auf die **Bedingung** Eigenschaft oder **UntilCondition** -Eigenschaft, abhängig von der Aktivität.  
  
2.  Wählen Sie **deklarative Regelbedingung** aus der Liste für die Eigenschaft.  
  
3.  Erweitern Sie die **Bedingung** oder **UntilCondition** Eigenschaft.  
  
4.  Klicken Sie auf die **ConditionName** Eigenschaft.  
  
5.  Klicken Sie auf die **ConditionName** Auslassungszeichen **[...]**  So öffnen die **Bedingung auswählen** (Dialogfeld).  
  
6.  Klicken Sie auf **neue Bedingung** So öffnen die **Regelbedingungs-Editor** (Dialogfeld).  
  
7.  Geben Sie den Ausdruck für die Bedingung in der **Bedingung** Textfeld.  
  
     Informationen zur Vorgehensweise beim Erstellen der Ausdrücke für suchbedingungen finden Sie unter [Regelsatz Bedingung-Editor (Dialogfeld) (Legacy)](../workflow-designer/rule-condition-editor-dialog-box-legacy.md).  
  
8.  Wenn Sie Erstellung des Bedingungsausdrucks abgeschlossen haben, klicken Sie auf **OK** um das Dialogfeld zu schließen und die regelbedingung mit einem zugewiesenen Namen zu erstellen.  
  
     Die **Bedingung auswählen** Dialogfeld wird geöffnet.  
  
     Informationen zur Verwendung der **Bedingung auswählen** (Dialogfeld), finden Sie unter [wählen Sie im Dialogfeld Bedingung (Legacy)](../workflow-designer/select-condition-dialog-box-legacy.md).  
  
## <a name="see-also"></a>Siehe auch  
 [Legacyworkflowaktivitäten](../workflow-designer/legacy-workflow-activities.md)   
 [Mithilfe der ConditionedActivityGroup](http://go.microsoft.com/fwlink?LinkID=65066)   
 [Verwenden der Aktivität "IfElseBranchActivity"](http://go.microsoft.com/fwlink?LinkID=65075)   
 [Verwenden der Replikator-Aktivität](http://go.microsoft.com/fwlink?LinkID=65080)   
 [Verwenden von While Aktivität](http://go.microsoft.com/fwlink?LinkID=65091)   
 [Dialogfeld "Regelbedingungs-Editor" (Vorgängerversion)](../workflow-designer/rule-condition-editor-dialog-box-legacy.md)   
 [Dialogfeld "Wählen Sie die Bedingung" (Vorgängerversion)](../workflow-designer/select-condition-dialog-box-legacy.md)   
 [Verwenden von Bedingungen in Workflows](http://go.microsoft.com/fwlink?LinkID=65009)