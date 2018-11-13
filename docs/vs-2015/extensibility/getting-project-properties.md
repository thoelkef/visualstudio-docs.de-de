---
title: Abrufen von Projekteigenschaften | Microsoft-Dokumentation
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- project properties, displaying in tool window
- tool windows, displaying project properties
ms.assetid: 96ba07ca-0811-4013-8602-12550ac4ba79
caps.latest.revision: 30
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: b99e86c4b955471ee10e0eb63cb5ca81fa675263
ms.sourcegitcommit: a34b7d4fdb3872865fcf98ba24a0fced58532adc
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/12/2018
ms.locfileid: "51561594"
---
# <a name="getting-project-properties"></a>Abrufen von Projekteigenschaften
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

In dieser exemplarischen Vorgehensweise zeigt Projekteigenschaften in einem Toolfenster.  
  
## <a name="prerequisites"></a>Vorraussetzungen  
 Ab Visual Studio 2015, sind Sie nicht Visual Studio SDK aus dem Downloadcenter installieren. Er ist als optionales Feature in Visual Studio-Setup enthalten. Sie können das VS-SDK auch später installieren. Weitere Informationen finden Sie unter [Installieren von Visual Studio SDK](../extensibility/installing-the-visual-studio-sdk.md).  
  
### <a name="to-create-a-vsix-project-and-add-a-tool-window"></a>Erstellen Sie ein VSIX-Projekt, und fügen ein Toolfenster  
  
1.  Alle Visual Studio-Erweiterung beginnt mit dem ein VSIX-Bereitstellung-Projekt, das die Ressourcen für die Erweiterung enthält. Erstellen Sie eine [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] VSIX-Projekt namens `ProjectPropertiesExtension`. Sie finden die VSIX-Projektvorlage in das **neues Projekt** Dialogfeld unter **Visual c# / Erweiterbarkeit**.  
  
2.  Fügen Sie ein Toolfenster durch Hinzufügen eines benutzerdefinierten Toolfensters Elements einer Vorlage mit dem Namen `ProjectPropertiesToolWindow`. In der **Projektmappen-Explorer**mit der rechten Maustaste auf den Projektknoten, und wählen Sie **hinzufügen / neues Element**. In der **Dialogfeld "Neues Element hinzufügen"**, wechseln Sie zu **Visual c#-Elemente / Erweiterbarkeit** , und wählen Sie **benutzerdefinierten Toolfensters**. In der **Namen** Feld am unteren Rand des Dialogfelds, ändern Sie den Dateinamen an `ProjectPropertiesToolWindow.cs`. Weitere Informationen zum Erstellen eines benutzerdefinierten Toolfensters finden Sie unter [erstellen eine Erweiterung mit einem Toolfenster](../extensibility/creating-an-extension-with-a-tool-window.md).  
  
3.  Erstellen Sie die Projektmappe, und stellen Sie sicher, dass sie fehlerfrei kompiliert wird.  
  
### <a name="to-display-project-properties-in-a-tool-window"></a>Zum Anzeigen von Projekteigenschaften in einem Toolfenster  
  
1.  Fügen Sie in der ProjectPropertiesToolWindowCommand.cs-Datei die folgenden using-Anweisungen.  
  
    ```csharp  
    using EnvDTE;  
    using System.Windows.Controls;  
  
    ```  
  
2.  Klicken Sie in ProjectPropertiesToolWindowControl.xaml entfernen Sie der vorhandene Schaltfläche "", und fügen Sie einem TreeView-Steuerelement aus der Toolbox. Sie können auch den Click-Ereignishandler aus der Datei ProjectPropertiesToolWindowControl.xaml.cs entfernen.  
  
3.  ProjectPropertiesToolWindowCommand.cs verwenden Sie die ShowToolWindow()-Methode, um das Projekt öffnen und lesen die Eigenschaften und anschließend fügen Sie die Eigenschaften in der Baumansicht hinzu. Der Code für ShowToolWindow sollte wie folgt aussehen:  
  
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
  
4.  Erstellen Sie das Projekt, und starten Sie das Debugging. Die experimentelle Instanz sollten angezeigt werden.  
  
5.  Öffnen Sie in der experimentellen Instanz ein Projekt aus.  
  
6.  In der **anzeigen / Other Windows** klicken Sie auf **ProjectPropertiesToolWindow**.  
  
     Daraufhin sollte das Strukturansicht-Steuerelement im Toolfenster, zusammen mit dem Namen des ersten Projekts und alle zugehörigen Projekteigenschaften.

