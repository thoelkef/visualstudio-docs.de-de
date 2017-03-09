---
title: "Vorgehensweise: Hinzuf&#252;gen von Aktivit&#228;ten zur Toolbox | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
ms.assetid: b3a8a785-5928-457a-8a50-30267e29503d
caps.latest.revision: 16
caps.handback.revision: 16
author: "ErikRe"
ms.author: "erikre"
manager: "erikre"
---
# Vorgehensweise: Hinzuf&#252;gen von Aktivit&#228;ten zur Toolbox
Der **Toolbox** in einer Projektmappe können auf verschiedene Weise Aktivitäten hinzugefügt werden.Sie können sie innerhalb des aktuellen Projekts hinzufügen oder durch einen Verweis auf ein anderes Projekt oder eine andere Assembly.  
  
### So fügen Sie innerhalb des aktuellen Projekts eine Aktivität hinzu  
  
1.  Fügen Sie dem aktuellen Workflowprojekt eine neue benutzerdefinierte Aktivität hinzu.[!INCLUDE[crabout](../test/includes/crabout_md.md)] zum Hinzufügen einer neuen benutzerdefinierten Aktivität zum Projekt finden Sie unter [Gewusst wie: Hinzufügen eines neuen Elements zu einem Workflowprojekt](../workflow-designer/how-to-add-a-new-item-to-a-workflow-project.md).  
  
2.  Fügen Sie der Aktivität benutzerdefinierte Logik hinzu.  
  
3.  Erstellen Sie das Projekt.Wenn die Erstellung erfolgreich war, wird in der **Toolbox** eine neue Kategorie namens "\<*project name*\>" angezeigt, die die benutzerdefinierte Aktivität enthält.  
  
    > [!NOTE]
    >  Wenn die Toolbox zurückgesetzt wird, werden benutzerdefinierte Aktivitäten entfernt. Dies gilt auch, wenn die Projektmappe erneut erstellt wird.Um die Toolbox erneut mit benutzerdefinierten Aktivitäten aufzufüllen, nachdem sie zurückgesetzt wurde, starten Sie [!INCLUDE[vs2010](../modeling/includes/vs2010_md.md)] erneut.  
  
    > [!NOTE]
    >  Die Toolbox kann nur eine Aktivität mit einem bestimmten Namen anzeigen.Wenn zwei Aktivitäten aus verschiedenen Assemblys denselben Klassennamen haben, wird nur eine anzeigt.  
  
    > [!NOTE]
    >  Die Anwendungsdomäne wird von Editorinstanzen gemeinsam verwendet. Wenn statische Variablen verwendet werden, werden sie von den Editorinstanzen auch gemeinsam verwendet.Wenn dieses Verhalten nicht erwünscht ist, sollte ein Dienst verwendet werden, um Variableninstanzen nachzuverfolgen.Informationen zur Verwendung von Diensten innerhalb des Designers finden Sie unter [Verwenden des ModelItem\-Bearbeitungskontexts](../Topic/Using%20the%20ModelItem%20Editing%20Context.md).  
  
### So fügen eine Aktivität aus einem anderen Projekt hinzu  
  
1.  Öffnen Sie eine Projektmappe, die mindestens ein Workflowprojekt und entweder ein benutzerdefiniertes Aktivitätsbibliotheksprojekt oder ein anderes Workflowprojekt enthält, in dem eine benutzerdefinierte Aktivität definiert wird.  
  
2.  Erstellen Sie beide Projekte.Wenn die Erstellung erfolgreich war, wird in der **Toolbox** eine neue Kategorie namens "\<*project name*\>" angezeigt, die die benutzerdefinierte Aktivität enthält.  
  
### So fügen Sie eine Aktivität aus einer Assembly der Toolbox hinzu  
  
1.  Öffnen Sie eine Workflowprojektmappe.  
  
2.  Wählen Sie im Menü **Extras** die Option **Toolboxelemente auswählen…** aus.  
  
3.  Wählen Sie im Dialogfeld **Toolboxelemente auswählen** die Registerkarte **System.Activities\-Komponenten** aus, und klicken Sie dann auf **Durchsuchen…**, um zu der Assembly zu wechseln, welche die benutzerdefinierte Aktivität enthält, die Sie hinzufügen möchten.  
  
4.  Wählen Sie die gewünschte Assembly aus, und klicken Sie auf **OK**.Die benutzerdefinierte Aktivitätskomponente wird der Liste der Komponenten hinzugefügt und automatisch ausgewählt.  
  
    1.  Klicken Sie auf **OK**, um das Dialogfeld zu schließen.  
  
5.  Um die Toolbox anzuzeigen, wählen Sie im Menü **Ansicht** die Option **Toolbox**.  
  
6.  Die benutzerdefinierte Aktivität wird in der **Toolbox** unter der Kategorie angezeigt, die im Fokus war, bevor das Element hinzugefügt wurde.Wenn z. B. die Kategorie **Allgemein** in der **Toolbox** vor dem Hinzufügen des Toolboxelements ausgewählt war, wird die Aktivität in der Kategorie **Allgemein** angezeigt.  
  
## Siehe auch  
 [Verwenden des Workflow\-Designers](../workflow-designer/using-the-workflow-designer.md)