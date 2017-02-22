---
title: "Abrufen von Projekteigenschaften | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Projekteigenschaften im Toolfenster anzeigen"
  - "Toolfenster, Projekt-Eigenschaften anzeigen"
ms.assetid: 96ba07ca-0811-4013-8602-12550ac4ba79
caps.latest.revision: 29
caps.handback.revision: 29
ms.author: "gregvanl"
manager: "ghogen"
---
# Abrufen von Projekteigenschaften
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

In dieser exemplarischen Vorgehensweise wird gezeigt, wie Sie Projekteigenschaften in einem Toolfenster angezeigt.  
  
## Vorbereitungsmaßnahmen  
 Starten in Visual Studio 2015, führen Sie Sie nicht Visual Studio SDK aus dem Downloadcenter installieren. Er ist als optionales Feature in Visual Studio\-Setup enthalten. Sie können auch später im Visual Studio SDK installieren. Weitere Informationen finden Sie unter [Das Visual Studio SDK installieren](../extensibility/installing-the-visual-studio-sdk.md).  
  
### So erstellen ein VSIX\-Projekt und fügen ein Toolfenster  
  
1.  Alle Visual Studio\-Erweiterung beginnt mit der ein VSIX\-Bereitstellungsprojekt, das die Ressourcen für die Erweiterung enthält. Erstellen einer [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] VSIX\-Projekt namens `ProjectPropertiesExtension`. Sie finden die VSIX\-Projektvorlage in die **Neues Projekt** Dialogfeld unter **Visual c\# \/ Erweiterbarkeit**.  
  
2.  Fügen Sie ein Toolfenster hinzu, indem Sie ein benutzerdefiniertes Toolfenster\-Elementvorlage mit dem Namen `ProjectPropertiesToolWindow`. In der **Projektmappen\-Explorer**, mit der rechten Maustaste auf den Projektknoten, und wählen Sie **Hinzufügen \/ neues Element**. In der **Dialogfeld Neues Element hinzufügen**, zur **Visual C\#\-Elemente \/ Erweiterbarkeit** und wählen Sie **benutzerdefinierte Toolfenster**. In den **Namen** Feld am unteren Rand des Dialogfelds, ändern Sie den Dateinamen `ProjectPropertiesToolWindow.cs`. Weitere Informationen zum Erstellen eines benutzerdefinierten Toolfensters finden Sie unter [Erstellen eine Erweiterung mit einem Toolfenster](../extensibility/creating-an-extension-with-a-tool-window.md).  
  
3.  Erstellen Sie die Projektmappe, und stellen Sie sicher, dass sie fehlerfrei kompiliert wird.  
  
### Zum Anzeigen von Projekteigenschaften in einem Toolfenster  
  
1.  Fügen Sie in der ProjectPropertiesToolWindowCommand.cs\-Datei die folgende using\-Anweisungen.  
  
    ```c#  
    using EnvDTE;  
    using System.Windows.Controls;  
  
    ```  
  
2.  Klicken Sie in ProjectPropertiesToolWindowControl.xaml entfernen Sie die vorhandene Schaltfläche, und fügen Sie einem TreeView\-Steuerelement aus der Toolbox. Sie können auch den Click\-Ereignishandler aus der Datei ProjectPropertiesToolWindowControl.xaml.cs entfernen.  
  
3.  Klicken Sie im ProjectPropertiesToolWindowCommand.cs verwenden Sie die ShowToolWindow\(\)\-Methode, um das Projekt öffnen und lesen die Eigenschaften, und fügen Sie die Eigenschaften der TreeView. Der Code für ShowToolWindow sollte wie folgt aussehen:  
  
    ```c#  
    private void ShowToolWindow(object sender, EventArgs e)  
    {  
        ToolWindowPane window = this.package.FindToolWindow(typeof(ProjectPropertiesToolWindow), 0, true);  
        if ((null == window) || (null == window.Frame))  
        {  
            throw new NotSupportedException("Cannot create window.");  
        }  
        IVsWindowFrame windowFrame = (IVsWindowFrame)window.Frame;  
        Microsoft.VisualStudio.ErrorHandler.ThrowOnFailure(windowFrame.Show());  
  
        // Get the tree view and populate it if there is a project open.  
        ProjectPropertiesToolWindowControl control = (ProjectPropertiesToolWindowControl)window.Content;  
        TreeView treeView = control.treeView;  
  
        // Reset the TreeView to 0 items.  
        treeView.Items.Clear();  
  
        DTE dte = (DTE)this.ServiceProvider.GetService(typeof(DTE));  
        Projects projects = dte.Solution.Projects;  
        if (projects.Count == 0)   // no project is open  
        {  
            TreeViewItem item = new TreeViewItem();  
            item.Name = "Projects";  
            item.ItemsSource = new string[]{ "no projects are open." };  
            item.IsExpanded = true;  
            treeView.Items.Add(item);  
            return;  
        }  
  
        Project project = projects.Item(1);  
        TreeViewItem item1 = new TreeViewItem();  
        item1.Header = project.Name + "Properties";  
        treeView.Items.Add(item1);  
  
        foreach (Property property in project.Properties)  
        {  
            TreeViewItem item = new TreeViewItem();  
            item.ItemsSource = new string[] { property.Name };  
            item.IsExpanded = true;  
            treeView.Items.Add(item);  
        }  
    }  
    ```  
  
4.  Erstellen Sie das Projekt, und starten Sie das Debugging. Die experimentelle Instanz sollte angezeigt werden.  
  
5.  Öffnen Sie ein Projekt in der experimentellen Instanz.  
  
6.  In der **Anzeigen \/ andere Fenster** klicken Sie auf **ProjectPropertiesToolWindow**.  
  
     Das Strukturansicht\-Steuerelement im Toolfenster zusammen mit dem Namen des ersten Projekts und alle Projekteigenschaften sollte angezeigt werden.