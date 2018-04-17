---
title: 'Vorgehensweise: Erstellen eines PolicyActivity-Regelsatzes (Vorgängerversion) | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
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
ms.openlocfilehash: 4911912aa46f5dc8a6aea9b9b20e87c1f83e576f
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/16/2018
---
# <a name="how-to-create-a-policyactivity-rule-set-legacy"></a>Vorgehensweise: Erstellen eines PolicyActivity-Regelsatzes (Vorgängerversion)

Dieses Thema beschreibt, wie eine richtlinienaktivitätsregelsatzes mithilfe der älteren Windows-Workflow-Designer erstellen, die [!INCLUDE[netfx35_long](../workflow-designer/includes/netfx35_long_md.md)] oder [!INCLUDE[vstecwinfx](../workflow-designer/includes/vstecwinfx_md.md)].

 Nachdem Sie gezogen haben eine **Richtlinie** Aktivitätselement aus der **Toolbox** auf der Workflowentwurfsoberfläche, sollten Sie eine vorhandene Regel auswählen oder erstellen einen neuen Regelsatz für die [PolicyActivity ](http://go.microsoft.com/fwlink?LinkID=65019) Aktivität. Wählen Sie einen vorhandenen Regelsatz, der mithilfe der [wählen Regelsatz festlegen (Dialogfeld) (Legacy)](../workflow-designer/select-rule-set-dialog-box-legacy.md) und Sie Regelsätze erstellen, indem die [Regelsatz festgelegt-Editor (Dialogfeld) (Legacy)](../workflow-designer/rule-set-editor-dialog-box-legacy.md).

> [!NOTE]
> Öffnen Sie die [Regelsatz festgelegt-Editor (Dialogfeld) (Legacy)](../workflow-designer/rule-set-editor-dialog-box-legacy.md) Dialogfeld direkt durch Doppelklicken auf eine [PolicyActivity](http://go.microsoft.com/fwlink?LinkID=65019) Aktivität, die auf der Entwurfsoberfläche des Workflows ist.

### <a name="to-select-or-create-a-rule-set-for-a-policyactivity-activity"></a>So wählen Sie einen Regelsatz für eine PolicyActivity-Aktivität aus beziehungsweise erstellen ihn

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