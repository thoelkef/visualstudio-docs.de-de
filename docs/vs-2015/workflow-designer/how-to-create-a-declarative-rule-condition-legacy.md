---
title: 'Vorgehensweise: Erstellen einer deklarativen Regel Bedingung (Legacy) | Microsoft-Dokumentation'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-workflow-designer
ms.topic: reference
helpviewer_keywords:
- declarative rule conditions
- condition statements, declarative rule conditions
- Rule Condition Editor dialog box
ms.assetid: 804b6129-c433-408f-a424-46987967730c
caps.latest.revision: 5
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 0c23fed64d7f3a7681fce96663262f6d633299a9
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "75849336"
---
# <a name="how-to-create-a-declarative-rule-condition-legacy"></a>Vorgehensweise: Erstellen einer deklarativen Regelbedingung (Vorgängerversion)
In diesem Thema wird beschrieben, wie eine Regelbedingung mithilfe der Vorgängerversion von [!INCLUDE[wfd1](../includes/wfd1-md.md)] deklariert wird, die auf [!INCLUDE[netfx35_long](../includes/netfx35-long-md.md)] oder [!INCLUDE[vstecwinfx](../includes/vstecwinfx-md.md)] abzielt.

 Eine Bedingungs Anweisung ergibt **true** oder **false**. Eine deklarative Regel Bedingung ist eine Bedingungs Anweisung, die mithilfe des Dialog Felds [Regelbedingungs-Editor (Legacy)](../workflow-designer/rule-condition-editor-dialog-box-legacy.md) erstellt und im XML-Format mit dem Workflow gespeichert wird. Sie kann Prädikate beinhalten, mit denen Workflowstatus und boolesche Algebra verglichen werden, in der mehrere Prädikate kombiniert sind.

 Deklarative Regelbedingungen werden in den folgenden vordefinierten Windows Workflow Foundation-Aktivitäten verwendet:

- [ConditionedActivityGroup](https://msdn2.microsoft.com/library/system.workflow.activities.conditionedactivitygroup.aspx)

- [IfElseBranchActivity  (Seite ist möglicherweise nur in englischer Sprache verfügbar.)](https://msdn2.microsoft.com/library/system.workflow.activities.ifelsebranchactivity.aspx)

- [ReplicatorActivity  (Seite ist möglicherweise nur in englischer Sprache verfügbar.)](https://msdn2.microsoft.com/library/system.workflow.activities.replicatoractivity.aspx)

- [WhileActivity](https://msdn2.microsoft.com/library/system.workflow.activities.whileactivity.aspx)

- [SequentialWorkflowActivity  (Seite ist möglicherweise nur in englischer Sprache verfügbar.)](https://msdn2.microsoft.com/library/system.workflow.activities.sequentialworkflowactivity.aspx)

- [StateMachineWorkflowActivity  (Seite ist möglicherweise nur in englischer Sprache verfügbar.)](https://msdn2.microsoft.com/library/system.workflow.activities.statemachineworkflowactivity.aspx)

### <a name="to-create-a-declarative-rule-condition-using-the-rule-condition-editor"></a>So erstellen Sie eine deklarative Regelbedingung mit dem Regelbedingungs-Editor

1. Klicken Sie im **Eigenschaften** Fenster der Aktivität abhängig von der Aktivität auf die **Condition** -Eigenschaft oder die **UntilCondition** -Eigenschaft.

2. Wählen Sie in der Liste für die Eigenschaft **deklarative Regel Bedingung** aus.

3. Erweitern Sie die **Condition** -Eigenschaft oder die **UntilCondition** -Eigenschaft.

4. Klicken Sie auf die Eigenschaft **ConditionName** .

5. Klicken Sie auf die Schaltfläche **ConditionName** Auslassungs Punkte **[...]** , um das Dialogfeld **Bedingung auswählen** zu öffnen.

6. Klicken Sie auf **neue Bedingung** , um das Dialogfeld **Regelbedingungs-Editor** zu öffnen.

7. Geben Sie den Ausdruck für die Bedingung in das Textfeld **Bedingung** ein.

     Weitere Informationen zum Erstellen von Bedingungs Ausdrücken finden Sie unter [Regelbedingungs-Editor (Dialog Feld) (Legacy)](../workflow-designer/rule-condition-editor-dialog-box-legacy.md).

8. Wenn Sie die Erstellung des Bedingungs Ausdrucks abgeschlossen haben, klicken Sie auf **OK** , um das Dialogfeld zu schließen und die Regel Bedingung mit einem zugewiesenen Namen zu erstellen.

     Das Dialogfeld **Bedingung auswählen** wird geöffnet.

     Weitere Informationen zur Verwendung des Dialog Felds **Bedingung auswählen** finden [Sie unter Dialogfeld "Bedingung auswählen" (Legacy)](../workflow-designer/select-condition-dialog-box-legacy.md).

## <a name="see-also"></a>Weitere Informationen
 [Legacy Workflow Aktivitäten](../workflow-designer/legacy-workflow-activities.md) [mithilfe von ConditionedActivityGroup](https://msdn2.microsoft.com/library/bb675237.aspx) mithilfe der [ifelmenbranchactivity-Aktivität](https://msdn2.microsoft.com/library/bb628465.aspx) [mithilfe der Replicator-Aktivität](https://msdn2.microsoft.com/library/bb628544.aspx) mithilfe des Dialog Felds "while- [Aktivitäts](https://msdn2.microsoft.com/library/bb628552.aspx) Regel Bedingungs-Editor" ( [Legacy)](../workflow-designer/rule-condition-editor-dialog-box-legacy.md) Dialogfeld " [Bedingung auswählen" (Legacy)](../workflow-designer/select-condition-dialog-box-legacy.md) unter [Verwendung von Bedingungen in Workflows](https://msdn2.microsoft.com/library/bb628447.aspx)
