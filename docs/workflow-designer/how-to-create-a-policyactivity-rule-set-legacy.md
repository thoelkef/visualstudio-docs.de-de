---
title: "Vorgehensweise: Erstellen eines PolicyActivity-Regelsatzes (Vorg&#228;ngerversion) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
helpviewer_keywords: 
  - "PolicyActivity-Aktivität, Erstellen von Regelsätzen"
  - "PolicyActivity-Aktivität, Auswählen von Regelsätzen"
  - "Regelsatz-Editor (Dialogfeld)"
  - "Regelsätze, Erstellen für PolicyActivity"
  - "Regelsatz auswählen (Dialogfeld)"
ms.assetid: f272489d-3342-4511-8b59-6a0fd7a42d70
caps.latest.revision: 4
author: "ErikRe"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 4
---
# Vorgehensweise: Erstellen eines PolicyActivity-Regelsatzes (Vorg&#228;ngerversion)
In diesem Thema wird das Erstellen eines Richtlinienaktivitätsregelsatzes mithilfe der Vorgängerversion von [!INCLUDE[wfd1](../workflow-designer/includes/wfd1_md.md)] beschrieben, die auf [!INCLUDE[netfx35_long](../workflow-designer/includes/netfx35_long_md.md)] oder [!INCLUDE[vstecwinfx](../workflow-designer/includes/vstecwinfx_md.md)] abzielt.  
  
 Nachdem Sie eine **Policy**\-Aktivität aus der **Toolbox** in die Workflowentwurfsoberfläche gezogen haben, können Sie eine vorhandene Regel auswählen oder einen neuen Regelsatz für die [PolicyActivity](http://go.microsoft.com/fwlink?LinkID=65019)\-Aktivität erstellen.Einen vorhandenen Regelsatz wählen Sie mit dem [Dialogfeld "Regelsatz\-Editor auswählen" \(Vorgängerversion\)](../workflow-designer/select-rule-set-dialog-box-legacy.md) aus. Einen neuen Regelsatz erstellen Sie mit dem [Dialogfeld "Regelsatz\-Editor" \(Vorgängerversion\)](../workflow-designer/rule-set-editor-dialog-box-legacy.md).  
  
> [!NOTE]
>  Sie können das Dialogfeld [Dialogfeld "Regelsatz\-Editor" \(Vorgängerversion\)](../workflow-designer/rule-set-editor-dialog-box-legacy.md) direkt durch Doppelklicken auf eine [PolicyActivity](http://go.microsoft.com/fwlink?LinkID=65019)\-Aktivität auf der Workflowentwurfsoberfläche öffnen.  
  
### So wählen Sie einen Regelsatz für eine PolicyActivity\-Aktivität aus beziehungsweise erstellen ihn  
  
1.  Klicken Sie mit der rechten Maustaste auf die [PolicyActivity](http://go.microsoft.com/fwlink?LinkID=65019), und klicken Sie dann auf **Eigenschaften**, um das Eigenschaftenfenster aufzurufen.  
  
2.  Klicken Sie auf die **RuleSetReference**\-Eigenschaft.  
  
3.  Führen Sie einen der folgenden Schritte aus:  
  
    -   Klicken Sie auf die **RuleSetReference**\-Auslassungszeichen **\[…\]**, und wählen Sie dann im [Dialogfeld "Regelsatz\-Editor auswählen" \(Vorgängerversion\)](../workflow-designer/select-rule-set-dialog-box-legacy.md) einen vorhandenen Regelsatz aus.Wechseln Sie dann zu Schritt 10.  
  
         \-oder\-  
  
    -   Geben Sie einen Namen für einen Regelsatz ein.Klicken Sie auf die **RuleSetReference**\-Auslassungszeichen **\[…\]**, und wählen Sie dann im [Dialogfeld "Regelsatz\-Editor auswählen" \(Vorgängerversion\)](../workflow-designer/select-rule-set-dialog-box-legacy.md) die Option **Bearbeiten** aus.  
  
         – oder –  
  
    -   Geben Sie einen Namen für einen Regelsatz ein.Erweitern Sie die **RuleSetReference**\-Eigenschaft, und wählen Sie die Auslassungszeichen **\[…\]** der **RuleSetDefinition**\-Eigenschaft aus.  
  
         Daraufhin wird das [Dialogfeld "Regelsatz\-Editor" \(Vorgängerversion\)](../workflow-designer/rule-set-editor-dialog-box-legacy.md) geöffnet.  
  
4.  Klicken Sie im [Dialogfeld "Regelsatz\-Editor" \(Vorgängerversion\)](../workflow-designer/rule-set-editor-dialog-box-legacy.md) auf die Option **Regel hinzufügen**, um dem Regelsatz eine neue Regel hinzuzufügen.  
  
5.  Geben Sie die Eigenschaften **Name**, **Priorität** und **Erneute Auswertung** ein, oder behalten Sie die Standardwerte bei.  
  
6.  Geben Sie den Text für die **Bedingung** ein.  
  
7.  Geben Sie den Text für die **Then\-Aktionen** und die **Else\-Aktionen** ein.  
  
8.  Klicken Sie erneut auf **Regel hinzufügen**, um eine weitere Regel hinzuzufügen.  
  
9. Klicken Sie abschließend auf **OK**.  
  
## Siehe auch  
 [PolicyActivity](http://go.microsoft.com/fwlink?LinkID=65019)   
 [Dialogfeld "Regelsatz\-Editor auswählen" \(Vorgängerversion\)](../workflow-designer/select-rule-set-dialog-box-legacy.md)   
 [Dialogfeld "Regelsatz\-Editor" \(Vorgängerversion\)](../workflow-designer/rule-set-editor-dialog-box-legacy.md)   
 [Verwenden der PolicyActivity](http://go.microsoft.com/fwlink?LinkID=65004)   
 [Legacyworkflowaktivitäten](../workflow-designer/legacy-workflow-activities.md)