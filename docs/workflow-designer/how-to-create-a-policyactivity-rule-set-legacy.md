---
title: 'Workflow-Designer - Vorgehensweise: Erstellen eines PolicyActivity-Regelsatzes (Vorgängerversion)'
ms.date: 11/04/2016
ms.topic: conceptual
ms.prod: visual-studio-dev15
ms.technology: vs-workflow-designer
helpviewer_keywords:
- PolicyActivity activity, creating rule sets
- Rule Set Editor dialog box
- PolicyActivity activity, selecting rule sets
- Select Rule Set dialog box
- rule sets, creating for PolicyActivity
ms.assetid: f272489d-3342-4511-8b59-6a0fd7a42d70
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 57142fc21bc9db03a338f20a27e20b8af51b48cd
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/26/2018
---
# <a name="how-to-create-a-policyactivity-rule-set-legacy"></a>Vorgehensweise: Erstellen eines PolicyActivity-Regelsatzes (Vorgängerversion)

In diesem Thema wird beschrieben, wie zum Erstellen einer richtlinienaktivitätsregelsatzes mithilfe der älteren Windows-Workflow-Designer, .NET Framework, Version 3.5 oder die WinFX.

 Nachdem Sie gezogen haben eine **Richtlinie** Aktivitätselement aus der **Toolbox** auf der Workflowentwurfsoberfläche, sollten Sie eine vorhandene Regel auswählen oder erstellen einen neuen Regelsatz für die [PolicyActivity ](http://go.microsoft.com/fwlink?LinkID=65019) Aktivität. Wählen Sie einen vorhandenen Regelsatz, der mithilfe der [wählen Regelsatz festlegen (Dialogfeld) (Legacy)](../workflow-designer/select-rule-set-dialog-box-legacy.md) und Sie Regelsätze erstellen, indem die [Regelsatz festgelegt-Editor (Dialogfeld) (Legacy)](../workflow-designer/rule-set-editor-dialog-box-legacy.md).

> [!NOTE]
> Öffnen Sie die [Regelsatz festgelegt-Editor (Dialogfeld) (Legacy)](../workflow-designer/rule-set-editor-dialog-box-legacy.md) Dialogfeld direkt durch Doppelklicken auf eine [PolicyActivity](http://go.microsoft.com/fwlink?LinkID=65019) Aktivität, die auf der Entwurfsoberfläche des Workflows ist.

## <a name="to-select-or-create-a-rule-set-for-a-policyactivity-activity"></a>So wählen Sie einen Regelsatz für eine PolicyActivity-Aktivität aus beziehungsweise erstellen ihn

1.  Mit der rechten Maustaste die [PolicyActivity](http://go.microsoft.com/fwlink?LinkID=65019), und klicken Sie dann auf **Eigenschaften** So öffnen die **Eigenschaften** Fenster.

2.  Klicken Sie auf die **RuleSetReference** Eigenschaft.

3.  Führen Sie einen der folgenden Schritte aus:

    -   Klicken Sie auf die **RuleSetReference** Auslassungszeichen **[...]** , und wählen Sie dann auf einen vorhandenen Regelsatz der [wählen Regelsatz festlegen (Dialogfeld) (Legacy)](../workflow-designer/select-rule-set-dialog-box-legacy.md). Wechseln Sie dann zu Schritt 10.

         - oder - 

    -   Geben Sie einen Namen für einen Regelsatz ein. Klicken Sie auf die **RuleSetReference** Auslassungszeichen **[...]** , und wählen Sie dann **bearbeiten** in der [wählen Regelsatz festlegen (Dialogfeld) (Legacy)](../workflow-designer/select-rule-set-dialog-box-legacy.md).

         - oder - 

    -   Geben Sie einen Namen für einen Regelsatz ein. Erweitern Sie die **RuleSetReference** Eigenschaft, und wählen Sie die Auslassungspunkte **[...]**  in der **Rulesetdefinition** Eigenschaft.

         Die [Regelsatz festgelegt-Editor (Dialogfeld) (Legacy)](../workflow-designer/rule-set-editor-dialog-box-legacy.md) wird geöffnet.

4.  In der [Regelsatz festgelegt-Editor (Dialogfeld) (Legacy)](../workflow-designer/rule-set-editor-dialog-box-legacy.md), klicken Sie auf **Regel hinzufügen** dem Regelsatz eine neue Regel hinzu.

5.  Geben Sie die **Namen**, **Priorität**, und **erneute Bewertung** Eigenschaften, oder behalten Sie die Standardwerte.

6.  Geben Sie den Text für die **Bedingung**.

7.  Geben Sie den Text für die **Then-Aktionen** und **Else-Aktionen**.

8.  Klicken Sie auf **Regel hinzufügen** erneut aus, um eine weitere Regel hinzuzufügen.

9. Wenn Sie fertig sind, klicken Sie auf **OK**.

## <a name="see-also"></a>Siehe auch

- [PolicyActivity](http://go.microsoft.com/fwlink?LinkID=65019)
- [Dialogfeld "Regelsatz-Editor auswählen" (Vorgängerversion)](../workflow-designer/select-rule-set-dialog-box-legacy.md)
- [Dialogfeld "Regelsatz-Editor" (Vorgängerversion)](../workflow-designer/rule-set-editor-dialog-box-legacy.md)
- [Verwenden der Policy-Aktivität](http://go.microsoft.com/fwlink?LinkID=65004)
- [Legacyworkflowaktivitäten](../workflow-designer/legacy-workflow-activities.md)