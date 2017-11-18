---
title: Abrufen von Projekteigenschaften | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- project properties, displaying in tool window
- tool windows, displaying project propeties
ms.assetid: 96ba07ca-0811-4013-8602-12550ac4ba79
caps.latest.revision: "29"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 931c4c6495d13418ed94f0507a00351e82a92564
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/31/2017
---
# <a name="getting-project-properties"></a>Abrufen von Projekteigenschaften
In dieser exemplarischen Vorgehensweise wird gezeigt, wie Sie Projekteigenschaften in einem Toolfenster angezeigt.  
  
## <a name="prerequisites"></a>Erforderliche Komponenten  
 Ab Visual Studio 2015, führen Sie Sie nicht Visual Studio-SDK aus dem Downloadcenter installieren. Sie ist als optionales Feature in Visual Studio-Setup aus. Sie können das VS-SDK auch später installieren. Weitere Informationen finden Sie unter [Installieren von Visual Studio SDK](../extensibility/installing-the-visual-studio-sdk.md).  
  
### <a name="to-create-a-vsix-project-and-add-a-tool-window"></a>Erstellen Sie ein VSIX-Projekt, und fügen ein Toolfenster  
  
1.  Alle Visual Studio-Erweiterung beginnt mit einem VSIX-Bereitstellung-Projekt bzw. die die Erweiterung Ressourcen enthält. Erstellen einer [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] VSIX-Projekt namens `ProjectPropertiesExtension`. Sie finden die VSIX-Projektvorlage in die **neues Projekt** Dialogfeld unter **Visual c# / Erweiterbarkeit**.  
  
2.  Fügen Sie ein Toolfenster hinzu, indem Sie eine Elementvorlage für benutzerdefinierte Toolfenster namens `ProjectPropertiesToolWindow`. In der **Projektmappen-Explorer**mit der rechten Maustaste auf den Projektknoten, und wählen Sie **hinzufügen / neues Element**. In der **Dialogfeld Neues Element hinzufügen**, wechseln Sie zu **Visual C#-Elemente / Erweiterbarkeit** , und wählen Sie **benutzerdefinierte Toolfenster**. In der **Namen** Feld am unteren Rand der Dialog, ändern Sie den Dateinamen an `ProjectPropertiesToolWindow.cs`. Weitere Informationen zum Erstellen eines benutzerdefinierten Toolfensters finden Sie unter [erstellen eine Erweiterung mit einem Toolfenster](../extensibility/creating-an-extension-with-a-tool-window.md).  
  
3.  Erstellen Sie die Projektmappe, und stellen Sie sicher, dass sie fehlerfrei kompiliert wird.  
  
### <a name="to-display-project-properties-in-a-tool-window"></a>Zum Anzeigen von Projekteigenschaften in einem Toolfenster  
  
1.  Fügen Sie in der Datei ProjectPropertiesToolWindowCommand.cs die folgenden using-Anweisungen.  
  
    ```csharp  
    using EnvDTE;  
    using System.Windows.Controls;  
  
    ```  
  
2.  Entfernen Sie in ProjectPropertiesToolWindowControl.xaml der vorhandene Schaltfläche "", und fügen Sie einer ' TreeView ' aus der Toolbox hinzu. Sie können auch den Click-Ereignishandler aus der Datei ProjectPropertiesToolWindowControl.xaml.cs entfernen.  
  
3.  Klicken Sie in ProjectPropertiesToolWindowCommand.cs verwenden Sie die ShowToolWindow()-Methode, um das Projekt öffnen und lesen die Eigenschaften, und fügen Sie die Eigenschaften der Baumstruktur hinzu. Der Code für ShowToolWindow sollte wie folgt aussehen:  
  
    ```csharp  
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
  
5.  Öffnen Sie ein Projekt, in der experimentellen Instanz.  
  
6.  In der **Ansicht / Weitere Fenster** klicken Sie auf **ProjectPropertiesToolWindow**.  
  
     Die Strukturansicht-Steuerelements im Toolfenster zusammen mit dem Namen des ersten Projekts und alle Projekteigenschaften sollte angezeigt werden.