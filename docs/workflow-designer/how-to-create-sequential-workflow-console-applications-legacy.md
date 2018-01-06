---
title: "Vorgehensweise: Erstellen von Konsolenanwendungen für sequenzielle Workflows (Vorgängerversion) | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
helpviewer_keywords:
- workflows, console applications
- sequential workflows, console applications
- console applications, sequential workflow
ms.assetid: 9f7be7fa-551f-42c6-a9bb-f5ae8ab83625
caps.latest.revision: "5"
author: ErikRe
ms.author: erikre
manager: erikre
ms.workload: multiple
ms.openlocfilehash: 79969572e4cab24e93a6c593a23369a00243ae0e
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-create-sequential-workflow-console-applications-legacy"></a>Vorgehensweise: Erstellen von Konsolenanwendungen für sequenzielle Workflows (Vorgängerversion)
Führen Sie die folgenden Schritte aus, um ein Projekt für eine Konsolenanwendung für sequenzielle Workflows mithilfe der Vorgängerversion von [!INCLUDE[wfd1](../workflow-designer/includes/wfd1_md.md)] zu erstellen, die von [!INCLUDE[vs2010](../misc/includes/vs2010_md.md)] bereitgestellt wird. Verwenden Sie die Vorgängerversion von [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)], wenn Sie entweder auf [!INCLUDE[netfx35_long](../workflow-designer/includes/netfx35_long_md.md)] oder [!INCLUDE[vstecwinfx](../workflow-designer/includes/vstecwinfx_md.md)] abzielen möchten.  
  
### <a name="to-create-a-sequential-workflow-console-application"></a>So erstellen Sie eine Konsolenanwendung für sequenzielle Workflows  
  
1.  Starten Sie Visual Studio.  
  
2.  Auf der **Datei** Sie im Menü **neu**, und wählen Sie dann **Projekt**.  
  
     Das Dialogfeld **Neues Projekt** wird angezeigt.  
  
3.  Wählen Sie entweder die **.NET Framework 3.0** Option oder der **.NET Framework 3.5** -Option in der Dropdownliste am oberen Rand der **neues Projekt** Fenster aus, um den Designer der Vorgängerversion zuzugreifen.  
  
    > [!NOTE]
    >  Die Standardoption in [!INCLUDE[vs2010](../misc/includes/vs2010_md.md)] ist **.NET Framework 4**. Diese Option wird zum Erstellen von [!INCLUDE[wf](../workflow-designer/includes/wf_md.md)]-Anwendungen verwendet, die auf [!INCLUDE[netfx40_short](../workflow-designer/includes/netfx40_short_md.md)] abzielen; dabei wird nicht der Designer der Vorgängerversion verwendet.  
  
4.  In der **Projekttypen** Bereich Option Visual C#-Projekte oder Visual Basic-Projekte (unter **andere Sprachen**), und wählen Sie dann **Workflow**.  
  
5.  In der **Vorlagen** klicken Sie im Bereich **Konsolenanwendung für sequenzielle Workflows**.  
  
6.  In der **Namen** Geben Sie einen beschreibenden Namen für das Projekt in der es einfach identifizieren zu können.  
  
7.  In der **Speicherort** Geben Sie das Verzeichnis, in dem Sie das Projekt gespeichert werden soll, oder klicken möchten **Durchsuchen** navigieren.  
  
     Der Windows Forms-Designer wird geöffnet und zeigt Form1 des neu erstellten Projekts an.  
  
8.  Klicken Sie auf **OK**.  
  
     Der Workflow-Designer wird geöffnet und zeigt die Workflowentwurfsoberfläche des neu erstellten sequenziellen Workflows an.  
  
9. Ziehen Sie eine Aktivität aus der **Toolbox** auf die Entwurfsoberfläche in die **Aktivität ablegen** festgelegten Bereich.  
  
## <a name="see-also"></a>Siehe auch  
 [Erstellen von Legacyworkflowprojekten](../workflow-designer/creating-legacy-workflow-projects.md)   
 [Entwickeln von Workflows](http://msdn.microsoft.com/en-us/557bcb1f-a7ab-49f6-8df7-2706b7001301)