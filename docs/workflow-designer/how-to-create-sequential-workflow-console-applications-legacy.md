---
title: "Vorgehensweise: Erstellen von Konsolenanwendungen f&#252;r sequenzielle Workflows (Vorg&#228;ngerversion) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
helpviewer_keywords: 
  - "Konsolenanwendungen, sequenzielle Workflows"
  - "sequenzielle Workflows, Konsolenanwendungen"
  - "Workflows, Konsolenanwendungen"
ms.assetid: 9f7be7fa-551f-42c6-a9bb-f5ae8ab83625
caps.latest.revision: 5
author: "ErikRe"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 5
---
# Vorgehensweise: Erstellen von Konsolenanwendungen f&#252;r sequenzielle Workflows (Vorg&#228;ngerversion)
Führen Sie die folgenden Schritte aus, um ein Projekt für eine Konsolenanwendung für sequenzielle Workflows mithilfe der Vorgängerversion von [!INCLUDE[wfd1](../workflow-designer/includes/wfd1_md.md)] zu erstellen, die von [!INCLUDE[vs2010](../modeling/includes/vs2010_md.md)] bereitgestellt wird.Verwenden Sie die Vorgängerversion von [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)], wenn Sie entweder auf [!INCLUDE[netfx35_long](../workflow-designer/includes/netfx35_long_md.md)] oder [!INCLUDE[vstecwinfx](../workflow-designer/includes/vstecwinfx_md.md)] abzielen möchten.  
  
### So erstellen Sie eine Konsolenanwendung für sequenzielle Workflows  
  
1.  Starten Sie Visual Studio.  
  
2.  Zeigen Sie im Menü **Datei** auf **Neu**, und klicken Sie dann auf **Projekt**.  
  
     Das Dialogfeld **Neues Projekt** wird angezeigt.  
  
3.  Aktivieren Sie die Option **.NET Framework 3.0** oder die Option **.NET Framework 3.5** in der Dropdownliste am oberen Rand des Fensters **Neues Projekt**, um auf den Designer der Vorgängerversion zuzugreifen.  
  
    > [!NOTE]
    >  Standardmäßig ist in [!INCLUDE[vs2010](../modeling/includes/vs2010_md.md)] die Option **.NET Framework 4** aktiviert.Diese Option wird zum Erstellen von [!INCLUDE[wf](../workflow-designer/includes/wf_md.md)]\-Anwendungen verwendet, die auf [!INCLUDE[netfx40_short](../workflow-designer/includes/netfx40_short_md.md)] abzielen; dabei wird nicht der Designer der Vorgängerversion verwendet.  
  
4.  Wählen Sie im Bereich **Projekttypen** die Option Visual C\#\-Projekte oder Visual Basic\-Projekte \(unter **Andere Sprachen**\) und anschließend **Workflow** aus.  
  
5.  Wählen Sie im Bereich **Vorlagen** die Option **Konsolenanwendung für sequenzielle Workflows** aus.  
  
6.  Geben Sie im Feld **Name** einen beschreibenden Namen für das Projekt ein, um es einfach identifizieren zu können.  
  
7.  Geben Sie im Textfeld **Speicherort** das Verzeichnis ein, unter dem das Projekt gespeichert werden soll, oder klicken Sie auf die Schaltfläche **Durchsuchen**, um zum Verzeichnis zu navigieren.  
  
     Der Windows Forms\-Designer wird geöffnet und zeigt Form1 des neu erstellten Projekts an.  
  
8.  Klicken Sie auf **OK**.  
  
     Der Workflow\-Designer wird geöffnet und zeigt die Workflowentwurfsoberfläche des neu erstellten sequenziellen Workflows an.  
  
9. Ziehen Sie eine Aktivität aus der **Toolbox** in die Entwurfsoberfläche im festgelegten Bereich **Aktivität ablegen**.  
  
## Siehe auch  
 [Erstellen von Legacyworkflowprojekten](../workflow-designer/creating-legacy-workflow-projects.md)   
 [Developing Workflows](http://msdn.microsoft.com/de-de/557bcb1f-a7ab-49f6-8df7-2706b7001301)