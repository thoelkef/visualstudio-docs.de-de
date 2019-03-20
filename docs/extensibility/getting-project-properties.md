---
title: Abrufen von Projekteigenschaften | Microsoft-Dokumentation
ms.date: 3/16/2019
ms.topic: conceptual
helpviewer_keywords:
- project properties, displaying in tool window
- tool windows, displaying project properties
ms.assetid: 96ba07ca-0811-4013-8602-12550ac4ba79
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: d6708759796639886d84a46003fbb894b988a714
ms.sourcegitcommit: 4d9c54f689416bf1dc4ace058919592482d02e36
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/19/2019
ms.locfileid: "58194994"
---
# <a name="get-project-properties"></a>Abrufen von Projekteigenschaften

In dieser exemplarischen Vorgehensweise zeigt Projekteigenschaften in einem Toolfenster.

## <a name="prerequisites"></a>Vorraussetzungen

Ab Visual Studio 2015, sind Sie nicht Visual Studio SDK aus dem Downloadcenter installieren. Er ist als optionales Feature in Visual Studio-Setup enthalten. Sie können das VS-SDK auch später installieren. Weitere Informationen finden Sie unter [installieren Sie Visual Studio SDK](../extensibility/installing-the-visual-studio-sdk.md).

### <a name="to-create-a-vsix-project-and-add-a-tool-window"></a>Erstellen Sie ein VSIX-Projekt, und fügen ein Toolfenster

1. Alle Visual Studio-Erweiterung beginnt mit dem ein VSIX-Projekt-Bereitstellung, die die Ressourcen für die Erweiterung enthält. Erstellen Sie eine [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] VSIX-Projekt namens `ProjectPropertiesExtension`. Sie finden die VSIX-Projektvorlage in das **neues Projekt** Dialogfeld, indem Sie nach "Vsix" suchen.

2. Fügen Sie ein Toolfenster durch Hinzufügen eines benutzerdefinierten Toolfensters Elements einer Vorlage mit dem Namen `ProjectPropertiesToolWindow`. In der **Projektmappen-Explorer**mit der rechten Maustaste auf den Projektknoten, und wählen Sie **hinzufügen** > **neues Element**. In der **Dialogfeld "Neues Element hinzufügen"**, wechseln Sie zu **Visual c#-Elemente** > **Erweiterbarkeit** , und wählen Sie **benutzerdefinierten Toolfensters**. In der **Namen** Feld am unteren Rand des Dialogfelds, ändern Sie den Dateinamen an `ProjectPropertiesToolWindow.cs`. Weitere Informationen zum Erstellen eines benutzerdefinierten Toolfensters finden Sie unter [erstellen Sie eine Erweiterung mit einem Toolfenster](../extensibility/creating-an-extension-with-a-tool-window.md).

3. Erstellen Sie die Projektmappe, und stellen Sie sicher, dass sie fehlerfrei kompiliert wird.

### <a name="to-display-project-properties-in-a-tool-window"></a>Zum Anzeigen von Projekteigenschaften in einem Toolfenster

1. Fügen Sie in der Datei ProjectPropertiesToolWindowCommand.cs die folgenden using-Anweisungen.

    ```csharp
    using EnvDTE;
    using System.Windows.Controls;

    ```

2. In *ProjectPropertiesToolWindowControl.xaml*der vorhandene Schaltfläche "entfernen", und fügen Sie einem TreeView-Steuerelement aus der Toolbox hinzu. Sie können auch entfernen, den Click-Ereignishandler aus der *ProjectPropertiesToolWindowControl.xaml.cs* Datei.

3. In *ProjectPropertiesToolWindowCommand.cs*, verwenden Sie die `ShowToolWindow()` Methode, um das Projekt öffnen und Lesen seine Eigenschaften, dann fügen Sie die Eigenschaften in der Baumansicht. Der Code für ShowToolWindow sollte wie folgt aussehen:

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

4. Erstellen Sie das Projekt, und starten Sie das Debugging. Die experimentelle Instanz sollten angezeigt werden.

5. Öffnen Sie in der experimentellen Instanz ein Projekt.

6. In der **Ansicht** > **Other Windows** klicken Sie auf **ProjectPropertiesToolWindow**.

  Daraufhin sollte das Strukturansicht-Steuerelement im Toolfenster, zusammen mit dem Namen des ersten Projekts und alle zugehörigen Projekteigenschaften.