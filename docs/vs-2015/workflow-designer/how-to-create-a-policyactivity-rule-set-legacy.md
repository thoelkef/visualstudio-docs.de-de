---
title: 'Vorgehensweise: Erstellen eines PolicyActivity-Regelsatzes (Legacy) | Microsoft-Dokumentation'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-workflow-designer
ms.topic: reference
helpviewer_keywords:
- PolicyActivity activity, creating rule sets
- Rule Set Editor dialog box
- PolicyActivity activity, selecting rule sets
- Select Rule Set dialog box
- rule sets, creating for PolicyActivity
ms.assetid: f272489d-3342-4511-8b59-6a0fd7a42d70
caps.latest.revision: 4
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 0f8599348d204d149f3e28d17d681941ddf476b8
ms.sourcegitcommit: c150d0be93b6f7ccbe9625b41a437541502560f5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/10/2020
ms.locfileid: "75849319"
---
# <a name="how-to-create-a-policyactivity-rule-set-legacy"></a>Vorgehensweise: Erstellen eines PolicyActivity-Regelsatzes (Vorgängerversion)
In diesem Thema wird das Erstellen eines Richtlinienaktivitätsregelsatzes mithilfe der Vorgängerversion von [!INCLUDE[wfd1](../includes/wfd1-md.md)] beschrieben, die auf [!INCLUDE[netfx35_long](../includes/netfx35-long-md.md)] oder [!INCLUDE[vstecwinfx](../includes/vstecwinfx-md.md)] abzielt.

 Nachdem Sie ein **Richtlinien** Aktivitäts Element von der **Toolbox** auf die Workflow Entwurfs Oberfläche gezogen haben, können Sie eine vorhandene Regel auswählen oder einen neuen Regelsatz für die [PolicyActivity](https://msdn2.microsoft.com/library/system.workflow.activities.policyactivity.aspx) -Aktivität erstellen. Sie wählen mithilfe des [Dialog Felds Regelsatz auswählen (Legacy)](../workflow-designer/select-rule-set-dialog-box-legacy.md) einen vorhandenen Regelsatz aus, und Sie erstellen Regelsätze mit dem [Dialogfeld Regelsatz-Editor (Legacy)](../workflow-designer/rule-set-editor-dialog-box-legacy.md).

> [!NOTE]
> Sie können das Dialogfeld [Regelsatz-Editor (Legacy)](../workflow-designer/rule-set-editor-dialog-box-legacy.md) direkt öffnen, indem Sie auf eine [PolicyActivity](https://msdn2.microsoft.com/library/system.workflow.activities.policyactivity.aspx) -Aktivität doppelklicken, die sich auf der Workflow Entwurfs Oberfläche befindet.

### <a name="to-select-or-create-a-rule-set-for-a-policyactivity-activity"></a>So wählen Sie einen Regelsatz für eine PolicyActivity-Aktivität aus beziehungsweise erstellen ihn

1. Klicken Sie mit der rechten Maustaste auf [PolicyActivity](https://msdn2.microsoft.com/library/system.workflow.activities.policyactivity.aspx), und klicken Sie dann auf **Eigenschaften** , um das **Eigenschaften** Fenster zu öffnen.

2. Klicken Sie auf die Eigenschaft **rulesetreferenzierung** .

3. Führen Sie eine der folgenden Aktionen aus:

    - Klicken Sie auf die Schaltfläche **rulesetreferenzierung** **[...]** , und wählen Sie dann im [Dialog Feld Regelsatz auswählen (Legacy)](../workflow-designer/select-rule-set-dialog-box-legacy.md)einen vorhandenen Regelsatz aus. Wechseln Sie dann zu Schritt 10.

         \- oder -

    - Geben Sie einen Namen für einen Regelsatz ein. Klicken Sie auf die Schaltfläche **rulesetreferenzierung** **[...]** , und wählen Sie dann im [Dialog Feld Regelsatz auswählen (Legacy)](../workflow-designer/select-rule-set-dialog-box-legacy.md)die Option **Bearbeiten** aus.

         \- oder -

    - Geben Sie einen Namen für einen Regelsatz ein. Erweitern Sie die Eigenschaft **rulesetreferenzierung** , und wählen Sie die Auslassungs Punkte **[...]** in der Eigenschaft **RuleSet Definition** aus.

         Das [Dialog Feld Regelsatz-Editor (Legacy)](../workflow-designer/rule-set-editor-dialog-box-legacy.md) wird geöffnet.

4. Klicken Sie im [Dialog Feld Regelsatz-Editor (Legacy)](../workflow-designer/rule-set-editor-dialog-box-legacy.md)auf **Regel hinzufügen** , um dem Regelsatz eine neue Regel hinzuzufügen.

5. Geben Sie die Eigenschaften **Name**, **Priority**und **Reevaluation** ein, oder behalten Sie die Standardwerte bei.

6. Geben Sie den Text für die **Bedingung**ein.

7. Geben Sie den Text für die **Then-Aktionen** und die Else- **Aktionen**ein.

8. Klicken Sie erneut auf **Regel hinzufügen** , um weitere Regeln hinzuzufügen.

9. Klicken Sie zum Abschluss auf **OK**.

## <a name="see-also"></a>Siehe auch
 [PolicyActivity](https://msdn2.microsoft.com/library/system.workflow.activities.policyactivity.aspx) -Dialogfeld " [Regelsatz-Editor auswählen" (Legacy)](../workflow-designer/select-rule-set-dialog-box-legacy.md) [Dialogfeld "Regelsatz-Editor" (Legacy)](../workflow-designer/rule-set-editor-dialog-box-legacy.md) [mithilfe der Richtlinien Aktivität](https://msdn2.microsoft.com/library/bb675229.aspx) [Legacy Workflow Aktivitäten](../workflow-designer/legacy-workflow-activities.md)
