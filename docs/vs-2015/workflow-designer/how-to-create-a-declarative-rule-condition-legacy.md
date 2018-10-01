---
title: 'Vorgehensweise: erstellen eine deklarativen Regelbedingung (Vorgängerversion) | Microsoft-Dokumentation'
ms.custom: ''
ms.date: 2018-06-30
ms.prod: .net-framework-4.6
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- declarative rule conditions
- condition statements, declarative rule conditions
- Rule Condition Editor dialog box
ms.assetid: 804b6129-c433-408f-a424-46987967730c
caps.latest.revision: 5
author: gewarren
ms.author: gewarren
manager: erikre
ms.openlocfilehash: 59eebe93b5c11fa1b02dc9ae481d0658010e961b
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/22/2018
ms.locfileid: "47512807"
---
# <a name="how-to-create-a-declarative-rule-condition-legacy"></a>Vorgehensweise: Erstellen einer deklarativen Regelbedingung (Vorgängerversion)
In diesem Thema wird beschrieben, wie eine Regelbedingung mithilfe der Vorgängerversion von [!INCLUDE[wfd1](../includes/wfd1-md.md)] deklariert wird, die auf [!INCLUDE[netfx35_long](../includes/netfx35-long-md.md)] oder [!INCLUDE[vstecwinfx](../includes/vstecwinfx-md.md)] abzielt.  
  
 Eine bedingungsanweisung ergibt **"true"** oder **"false"**. Eine deklarative regelbedingung ist eine bedingungsanweisung, die mit der [Regel-Editor-Dialogfeld (Legacy)](../workflow-designer/rule-condition-editor-dialog-box-legacy.md) und mit dem Workflow als XML gespeichert. Sie kann Prädikate beinhalten, mit denen Workflowstatus und boolesche Algebra verglichen werden, in der mehrere Prädikate kombiniert sind.  
  
 Deklarative Regelbedingungen werden in den folgenden vordefinierten Windows Workflow Foundation-Aktivitäten verwendet:  
  
-   [ConditionedActivityGroup](http://go.microsoft.com/fwlink?LinkID=65017)  
  
-   [IfElseBranchActivity](http://go.microsoft.com/fwlink?LinkID=65034)  
  
-   [ReplicatorActivity](http://go.microsoft.com/fwlink?LinkID=65039)  
  
-   [WhileActivity](http://go.microsoft.com/fwlink?LinkID=65049)  
  
-   [SequentialWorkflowActivity](http://go.microsoft.com/fwlink?LinkID=65040)  
  
-   [StateMachineWorkflowActivity](http://go.microsoft.com/fwlink?LinkID=65045)  
  
### <a name="to-create-a-declarative-rule-condition-using-the-rule-condition-editor"></a>So erstellen Sie eine deklarative Regelbedingung mit dem Regelbedingungs-Editor  
  
1.  In der Aktivitäts **Eigenschaften** Fenster, klicken Sie auf die **Bedingung** Eigenschaft oder **UntilCondition** -Eigenschaft, je nach der Aktivität.  
  
2.  Wählen Sie **deklarative Regelbedingung** aus der Liste für die Eigenschaft.  
  
3.  Erweitern Sie die **Bedingung** oder **UntilCondition** Eigenschaft.  
  
4.  Klicken Sie auf die **ConditionName** Eigenschaft.  
  
5.  Klicken Sie auf die **ConditionName** Ellipsen **[...]**  zum Öffnen der **Bedingung auswählen** Dialogfeld.  
  
6.  Klicken Sie auf **neue Bedingung** zum Öffnen der **Regelbedingungs-Editor** Dialogfeld.  
  
7.  Geben Sie den Ausdruck für die Bedingung in der **Bedingung** Textfeld.  
  
     Weitere Informationen zum Erstellen, finden Sie unter [Regel-Editor-Dialogfeld (Legacy)](../workflow-designer/rule-condition-editor-dialog-box-legacy.md).  
  
8.  Wenn Sie die Erstellung des Bedingungsausdrucks haben, klicken Sie auf **OK** , um das Dialogfeld schließen und die regelbedingung mit einem zugewiesenen Namen zu erstellen.  
  
     Die **Bedingung auswählen** Dialogfeld wird geöffnet.  
  
     Informationen zur Verwendung der **Bedingung auswählen** im Dialogfeld finden Sie unter [wählen Sie im Dialogfeld Bedingung (Legacy)](../workflow-designer/select-condition-dialog-box-legacy.md).  
  
## <a name="see-also"></a>Siehe auch  
 [Legacyworkflowaktivitäten](../workflow-designer/legacy-workflow-activities.md)   
 [Verwenden von ConditionedActivityGroup](http://go.microsoft.com/fwlink?LinkID=65066)   
 [Verwenden der IfElseBranchActivity-Aktivität](http://go.microsoft.com/fwlink?LinkID=65075)   
 [Verwenden der Replicator-Aktivität](http://go.microsoft.com/fwlink?LinkID=65080)   
 [Verwenden der While Aktivität](http://go.microsoft.com/fwlink?LinkID=65091)   
 [Dialogfeld "Regelbedingungs-Editor" (Vorgängerversion)](../workflow-designer/rule-condition-editor-dialog-box-legacy.md)   
 [Dialogfeld "Wählen Sie die Bedingung" (Vorgängerversion)](../workflow-designer/select-condition-dialog-box-legacy.md)   
 [Verwenden von Bedingungen in Workflows](http://go.microsoft.com/fwlink?LinkID=65009)