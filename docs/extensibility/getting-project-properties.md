---
title: Abrufen von Projekteigenschaften | Microsoft Docs
ms.date: 3/16/2019
ms.topic: conceptual
helpviewer_keywords:
- project properties, displaying in tool window
- tool windows, displaying project properties
ms.assetid: 96ba07ca-0811-4013-8602-12550ac4ba79
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 9ddfd48827bc762c9189f9b7600cfe9200e5c866
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/06/2020
ms.locfileid: "80711411"
---
# <a name="get-project-properties"></a>Abrufen von Projekteigenschaften

In dieser exemplarischen Vorgehensweise wird gezeigt, wie Projekteigenschaften in einem Werkzeugfenster angezeigt werden.

## <a name="prerequisites"></a>Voraussetzungen

Ab Visual Studio 2015 installieren Sie das Visual Studio SDK nicht aus dem Downloadcenter. Es ist als optionale Funktion in Visual Studio-Setup enthalten. Sie können das VS SDK auch später installieren. Weitere Informationen finden Sie unter [Installieren des Visual Studio SDK](../extensibility/installing-the-visual-studio-sdk.md).

### <a name="to-create-a-vsix-project-and-add-a-tool-window"></a>So erstellen Sie ein VSIX-Projekt und fügen ein Toolfenster hinzu

1. Jede Visual Studio-Erweiterung beginnt mit einem VSIX-Bereitstellungsprojekt, das die Erweiterungselemente enthält. Erstellen [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] Sie ein `ProjectPropertiesExtension`VSIX-Projekt mit dem Namen . Die VSIX-Projektvorlage finden Sie im Dialogfeld **Neues Projekt,** indem Sie nach "vsix" suchen.

2. Fügen Sie ein Toolfenster hinzu, indem `ProjectPropertiesToolWindow`Sie eine elementemustergebundene Vorlage für das benutzerdefinierte Werkzeugfenster mit dem Namen hinzufügen. Klicken Sie im **Projektmappen-Explorer**mit der rechten Maustaste auf den Projektknoten, und wählen Sie**Neues Element** **hinzufügen** > aus. Wechseln Sie im **Dialogfeld Neues Element hinzufügen**zu **Visual C-Items** > **Extensibility,** und wählen Sie **Benutzerdefiniertes Werkzeugfenster**aus. Ändern Sie im Feld **Name** am unteren Rand `ProjectPropertiesToolWindow.cs`des Dialogfelds den Dateinamen in . Weitere Informationen zum Erstellen eines benutzerdefinierten Werkzeugfensters finden Sie unter [Erstellen einer Erweiterung mit einem Werkzeugfenster](../extensibility/creating-an-extension-with-a-tool-window.md).

3. Erstellen Sie die Projektmappe, und stellen Sie sicher, dass sie fehlerfrei kompiliert wird.

### <a name="to-display-project-properties-in-a-tool-window"></a>So zeigen Sie Projekteigenschaften in einem Werkzeugfenster an

1. Fügen Sie in der ProjectPropertiesToolWindowCommand.cs Datei die folgenden Anweisungen hinzu.

    ```csharp
    using EnvDTE;
    using System.Windows.Controls;

    ```

2. Entfernen Sie in *ProjectPropertiesToolWindowControl.xaml*die vorhandene Schaltfläche, und fügen Sie eine TreeView aus der Toolbox hinzu. Sie können auch den Click-Ereignishandler aus der *ProjectPropertiesToolWindowControl.xaml.cs-Datei* entfernen.

3. Verwenden Sie in `ShowToolWindow()` *ProjectPropertiesToolWindowCommand.cs*die Methode, um das Projekt zu öffnen und seine Eigenschaften zu lesen, und fügen Sie dann die Eigenschaften zur TreeView hinzu. Der Code für ShowToolWindow sollte wie folgt aussehen:

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

4. Erstellen Sie das Projekt, und starten Sie das Debugging. Die experimentelle Instanz sollte angezeigt werden.

5. Öffnen Sie in der experimentellen Instanz ein Projekt.

6. Klicken Sie in der **Ansicht** > **Andere Windows-Taste** auf **ProjectPropertiesToolWindow**.

  Sie sollten das Struktursteuerelement im Werkzeugfenster zusammen mit dem Namen des ersten Projekts und aller Projekteigenschaften sehen.
