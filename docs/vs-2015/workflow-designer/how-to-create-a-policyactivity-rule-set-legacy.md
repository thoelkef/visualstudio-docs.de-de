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
ms.openlocfilehash: 2c200c7db90f3cad12c1188af88f4651d2f2d44c
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/19/2019
ms.locfileid: "72663395"
---
# <a name="how-to-create-a-policyactivity-rule-set-legacy"></a>Vorgehensweise: Erstellen eines PolicyActivity-Regelsatzes (Vorgängerversion)
In diesem Thema wird das Erstellen eines Richtlinienaktivitätsregelsatzes mithilfe der Vorgängerversion von [!INCLUDE[wfd1](../includes/wfd1-md.md)] beschrieben, die auf [!INCLUDE[netfx35_long](../includes/netfx35-long-md.md)] oder [!INCLUDE[vstecwinfx](../includes/vstecwinfx-md.md)] abzielt.

 Nachdem Sie ein **Richtlinien** Aktivitäts Element von der **Toolbox** auf die Workflow Entwurfs Oberfläche gezogen haben, können Sie eine vorhandene Regel auswählen oder einen neuen Regelsatz für die [PolicyActivity](http://go.microsoft.com/fwlink?LinkID=65019) -Aktivität erstellen. Sie wählen mithilfe des [Dialog Felds Regelsatz auswählen (Legacy)](../workflow-designer/select-rule-set-dialog-box-legacy.md) einen vorhandenen Regelsatz aus, und Sie erstellen Regelsätze mit dem [Dialogfeld Regelsatz-Editor (Legacy)](../workflow-designer/rule-set-editor-dialog-box-legacy.md).

> [!NOTE]
> Sie können das Dialogfeld [Regelsatz-Editor (Legacy)](../workflow-designer/rule-set-editor-dialog-box-legacy.md) direkt öffnen, indem Sie auf eine [PolicyActivity](http://go.microsoft.com/fwlink?LinkID=65019) -Aktivität doppelklicken, die sich auf der Workflow Entwurfs Oberfläche befindet.

### <a name="to-select-or-create-a-rule-set-for-a-policyactivity-activity"></a>So wählen Sie einen Regelsatz für eine PolicyActivity-Aktivität aus beziehungsweise erstellen ihn

1. Klicken Sie mit der rechten Maustaste auf [PolicyActivity](http://go.microsoft.com/fwlink?LinkID=65019), und klicken Sie dann auf **Eigenschaften** , um das **Eigenschaften** Fenster zu öffnen.

2. Klicken Sie auf die Eigenschaft **rulesetreferenzierung** .

3. Führen Sie einen der folgenden Schritte aus:

    - Klicken Sie auf die Schaltfläche **rulesetreferenzierung** **[...]** , und wählen Sie dann im [Dialog Feld Regelsatz auswählen (Legacy)](../workflow-designer/select-rule-set-dialog-box-legacy.md)einen vorhandenen Regelsatz aus. Wechseln Sie dann zu Schritt 10.

         - oder -

    - Geben Sie einen Namen für einen Regelsatz ein. Klicken Sie auf die Schaltfläche **rulesetreferenzierung** **[...]** , und wählen Sie dann im [Dialog Feld Regelsatz auswählen (Legacy)](../workflow-designer/select-rule-set-dialog-box-legacy.md)die Option **Bearbeiten** aus.

         - oder -

    - Geben Sie einen Namen für einen Regelsatz ein. Erweitern Sie die Eigenschaft **rulesetreferenzierung** , und wählen Sie die Auslassungs Punkte **[...]** in der Eigenschaft **RuleSet Definition** aus.

         Das [Dialog Feld Regelsatz-Editor (Legacy)](../workflow-designer/rule-set-editor-dialog-box-legacy.md) wird geöffnet.

4. Klicken Sie im [Dialog Feld Regelsatz-Editor (Legacy)](../workflow-designer/rule-set-editor-dialog-box-legacy.md)auf **Regel hinzufügen** , um dem Regelsatz eine neue Regel hinzuzufügen.

5. Geben Sie die Eigenschaften **Name**, **Priority**und **Reevaluation** ein, oder behalten Sie die Standardwerte bei.

6. Geben Sie den Text für die **Bedingung**ein.

7. Geben Sie den Text für die **Then-Aktionen** und die Else- **Aktionen**ein.

8. Klicken Sie erneut auf **Regel hinzufügen** , um weitere Regeln hinzuzufügen.

9. Wenn Sie fertig sind, klicken Sie auf **OK**.

## <a name="see-also"></a>Siehe auch
 [PolicyActivity](http://go.microsoft.com/fwlink?LinkID=65019) -Dialogfeld " [Regelsatz-Editor auswählen" (Legacy)](../workflow-designer/select-rule-set-dialog-box-legacy.md) [Dialogfeld "Regelsatz-Editor" (Legacy)](../workflow-designer/rule-set-editor-dialog-box-legacy.md) [mithilfe der Richtlinien Aktivität](http://go.microsoft.com/fwlink?LinkID=65004) [Legacy Workflow Aktivitäten](../workflow-designer/legacy-workflow-activities.md)