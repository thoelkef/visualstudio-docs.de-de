---
title: "Vorgehensweise: Erstellen einer Konsolenanwendung f&#252;r Workflows | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
ms.assetid: 51a2eea7-921c-49f1-b358-68afc27f1ee9
caps.latest.revision: 16
author: "ErikRe"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 16
---
# Vorgehensweise: Erstellen einer Konsolenanwendung f&#252;r Workflows
Mit [!INCLUDE[wf](../workflow-designer/includes/wf_md.md)] können Sie Workflows zum Ausführen von Systemprozessen oder menschlichen Prozessen erstellen.Der [!INCLUDE[wfd1](../workflow-designer/includes/wfd1_md.md)] stellt die Entwurfsoberfläche zum Erstellen dieser Workflows bereit.Der [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)] kann verwendet werden, um Workflows in [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] zu erstellen, oder er kann in andere Anwendungen integriert werden, die den Designer neu hosten.  
  
 In diesem Thema wird beschrieben, wie der [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)] in [!INCLUDE[vs2010](../modeling/includes/vs2010_md.md)] verwendet wird, um einen Workflow in einer Konsolenanwendung zu erstellen.  
  
### So erstellen Sie eine Konsolenanwendung für Workflows  
  
1.  Starten Sie [!INCLUDE[vs2010](../modeling/includes/vs2010_md.md)].  
  
2.  Zeigen Sie im Menü **Datei** auf **Neu**, und klicken Sie dann auf **Projekt**.  
  
     Das Dialogfeld **Neues Projekt** wird angezeigt.  
  
3.  Wählen Sie im Bereich **Installierte Vorlagen** die Option **Workflow** der **Visual C\#**\- oder **Visual Basic**\-Gruppe \(je nach bevorzugter Sprache\) aus.  
  
4.  Wählen Sie im mittleren Bereich **Konsolenanwendung für Workflows** aus.  
  
5.  Geben Sie im Feld **Name** einen beschreibenden Namen für das Projekt ein, um es einfach identifizieren zu können.  
  
6.  Geben Sie im Feld **Speicherort** das Verzeichnis ein, in dem das Projekt gespeichert werden soll, oder klicken Sie auf **Durchsuchen**, um zu dem Verzeichnis zu navigieren.  
  
7.  Geben Sie im Feld **Projektmappe** den Namen für die neue Projektmappe ein.Klicken Sie auf **OK**, um die Anwendung zu erstellen.  
  
    > [!NOTE]
    >  Wenn Sie einer vorhandenen Projektmappe eine Workflowkonsolenanwendung hinzufügen möchten, öffnen Sie diese Projektmappe in [!INCLUDE[vs2010](../modeling/includes/vs2010_md.md)], klicken Sie mit der rechten Maustaste im **Projektmappen\-Explorer** auf die Projektmappe, und wählen Sie **Hinzufügen** und dann **Neues Projekt** aus, um das Dialogfeld **Neues Projekt** zu öffnen.Fahren Sie wie oben in dieser Prozedur beschrieben fort.  
  
8.  Die Projektvorlage erstellt eine Workflowdefinition in XAML, und die Konsolenanwendungsdefinition ist in Quellcode.Der [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)] wird geöffnet und zeigt den Canvas für den Workflow an, den Sie erstellt haben.  
  
9. Um einen Workflow zu verfassen, ziehen Sie Aktivitäten oder andere Workflowelemente von der **Toolbox** zur Entwurfsoberfläche in Ihrem Workflow.  
  
## Siehe auch  
 [Erstellen eines Workflowprojekts](../workflow-designer/creating-a-workflow-project.md)