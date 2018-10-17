---
title: 'Vorgehensweise: erstellen ein PolicyActivity-Regelsatzes (Vorgängerversion) | Microsoft-Dokumentation'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: .net-framework-4.6
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- PolicyActivity activity, creating rule sets
- Rule Set Editor dialog box
- PolicyActivity activity, selecting rule sets
- Select Rule Set dialog box
- rule sets, creating for PolicyActivity
ms.assetid: f272489d-3342-4511-8b59-6a0fd7a42d70
caps.latest.revision: 4
author: gewarren
ms.author: gewarren
manager: erikre
ms.openlocfilehash: 7ab49957d830bf558a9dddf55cdc5e8c2f3f75d2
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/12/2018
ms.locfileid: "49194622"
---
# <a name="how-to-create-a-policyactivity-rule-set-legacy"></a>Vorgehensweise: Erstellen eines PolicyActivity-Regelsatzes (Vorgängerversion)
In diesem Thema wird das Erstellen eines Richtlinienaktivitätsregelsatzes mithilfe der Vorgängerversion von [!INCLUDE[wfd1](../includes/wfd1-md.md)] beschrieben, die auf [!INCLUDE[netfx35_long](../includes/netfx35-long-md.md)] oder [!INCLUDE[vstecwinfx](../includes/vstecwinfx-md.md)] abzielt.  
  
 Nachdem Sie gezogen haben eine **Richtlinie** Aktivitätselement aus der **Toolbox** auf der Workflowentwurfsoberfläche, möchten Sie eine vorhandene Regel auswählen oder erstellen Sie einen neuen Regelsatz für die [PolicyActivity ](http://go.microsoft.com/fwlink?LinkID=65019) Aktivität. Wählen Sie einen vorhandenen Regelsatz mit der [Regel legen Sie im Dialogfeld auswählen (Legacy)](../workflow-designer/select-rule-set-dialog-box-legacy.md) und Regelsatz erstellen Sie mithilfe der [Regel-Editor-Dialogfeld festlegen (Legacy)](../workflow-designer/rule-set-editor-dialog-box-legacy.md).  
  
> [!NOTE]
>  Öffnen Sie die [Regel-Editor-Dialogfeld festlegen (Legacy)](../workflow-designer/rule-set-editor-dialog-box-legacy.md) Dialogfeld direkt durch Doppelklicken auf eine [PolicyActivity](http://go.microsoft.com/fwlink?LinkID=65019) -Aktivität auf der Workflowentwurfsoberfläche.  
  
### <a name="to-select-or-create-a-rule-set-for-a-policyactivity-activity"></a>So wählen Sie einen Regelsatz für eine PolicyActivity-Aktivität aus beziehungsweise erstellen ihn  
  
1.  Mit der rechten Maustaste die [PolicyActivity](http://go.microsoft.com/fwlink?LinkID=65019), und klicken Sie dann auf **Eigenschaften** zum Öffnen der **Eigenschaften** Fenster.  
  
2.  Klicken Sie auf die **RuleSetReference** Eigenschaft.  
  
3.  Führen Sie einen der folgenden Schritte aus:  
  
    -   Klicken Sie auf die **RuleSetReference** Ellipsen **[...]** , und wählen Sie dann auf einen vorhandenen Regelsatz der [Regel legen Sie im Dialogfeld auswählen (Legacy)](../workflow-designer/select-rule-set-dialog-box-legacy.md). Wechseln Sie dann zu Schritt 10.  
  
         - oder -   
  
    -   Geben Sie einen Namen für einen Regelsatz ein. Klicken Sie auf die **RuleSetReference** Ellipsen **[...]** , und wählen Sie dann **bearbeiten** in die [Regel legen Sie im Dialogfeld auswählen (Legacy)](../workflow-designer/select-rule-set-dialog-box-legacy.md).  
  
         - oder -   
  
    -   Geben Sie einen Namen für einen Regelsatz ein. Erweitern Sie die **RuleSetReference** Eigenschaft, und wählen Sie die Auslassungspunkte **[...]**  in die **Rulesetdefinition** Eigenschaft.  
  
         Die [Regel-Editor-Dialogfeld festlegen (Legacy)](../workflow-designer/rule-set-editor-dialog-box-legacy.md) wird geöffnet.  
  
4.  In der [Regel-Editor-Dialogfeld festlegen (Legacy)](../workflow-designer/rule-set-editor-dialog-box-legacy.md), klicken Sie auf **Regel hinzufügen** dem Regelsatz eine neue Regel hinzu.  
  
5.  Geben Sie die **Namen**, **Priorität**, und **erneute** Eigenschaften, oder behalten Sie die Standardwerte.  
  
6.  Geben Sie den Text für die **Bedingung**.  
  
7.  Geben Sie den Text für die **Then-Aktionen** und **Else-Aktionen**.  
  
8.  Klicken Sie auf **Regel hinzufügen** erneut aus, um eine weitere Regel hinzuzufügen.  
  
9. Wenn Sie fertig sind, klicken Sie auf **OK**.  
  
## <a name="see-also"></a>Siehe auch  
 [PolicyActivity](http://go.microsoft.com/fwlink?LinkID=65019)   
 [Regel für die Auswahl festlegen (Dialogfeld) (Vorgängerversion)](../workflow-designer/select-rule-set-dialog-box-legacy.md)   
 [Regelsatz-Editor-Dialogfeld (Vorgängerversion)](../workflow-designer/rule-set-editor-dialog-box-legacy.md)   
 [Verwenden der PolicyActivity](http://go.microsoft.com/fwlink?LinkID=65004)   
 [Legacyworkflowaktivitäten](../workflow-designer/legacy-workflow-activities.md)