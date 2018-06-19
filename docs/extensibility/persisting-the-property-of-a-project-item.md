---
title: Die Eigenschaft eines Projektelements beibehalten | Microsoft Docs
ms.date: 03/22/2018
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- properties, adding to a project item
- project items, adding properties
ms.assetid: d7a0f2b0-d427-4d49-9536-54edfb37c0f3
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: a6b0bc529e01d8ef34b6959b98d773857000ec1c
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/16/2018
ms.locfileid: "31138053"
---
# <a name="persisting-the-property-of-a-project-item"></a>Die Eigenschaft eines Projektelements beibehalten
Möglicherweise möchten eine Eigenschaft persistent zu speichern, die Sie ein Projektelement, z. B. der Autor einer Quelldatei hinzufügen. Dazu können Sie die Eigenschaft in der Projektdatei gespeichert.

 Der erste Schritt beim Beibehalten einer Eigenschaft in einer Projektdatei wird zum Abrufen der Hierarchie des Projekts als eine <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy> Schnittstelle. Sie können diese Schnittstelle abrufen, mithilfe der Automatisierung oder mithilfe von <xref:Microsoft.VisualStudio.Shell.Interop.IVsMonitorSelection>. Nachdem Sie die Schnittstelle erhalten haben, können Sie es verwenden, um zu bestimmen, welche Projektelement derzeit ausgewählt ist. Nachdem Sie die Project-Element-ID haben, können Sie <xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildPropertyStorage.SetItemAttribute%2A> die Eigenschaft hinzufügen.

 In den folgenden Verfahren, die Sie beibehalten der Eigenschaft VsPkg.cs `Author` mit dem Wert `Tom` in der Projektdatei.

### <a name="to-obtain-the-project-hierarchy-with-the-dte-object"></a>Zum Abrufen der Projekthierarchie mit dem DTE-Objekt

1.  Fügen Sie den folgenden Code, um Ihr VSPackage:

    ```csharp
    EnvDTE.DTE dte = (EnvDTE.DTE)Package.GetGlobalService(typeof(EnvDTE.DTE));
    EnvDTE.Project project = dte.Solution.Projects.Item(1);

    string uniqueName = project.UniqueName;
    IVsSolution solution = (IVsSolution)Package.GetGlobalService(typeof(SVsSolution));
    IVsHierarchy hierarchy;
    solution.GetProjectOfUniqueName(uniqueName, out hierarchy);
    ```

### <a name="to-persist-the-project-item-property-with-the-dte-object"></a>Um den Projekt-Elementeigenschaft mit dem DTE-Objekt persistent zu speichern.

1.  Fügen Sie den folgenden Code an den Code in der Methode in der vorherigen Prozedur zugewiesen:

    ```csharp
    IVsBuildPropertyStorage buildPropertyStorage =
        hierarchy as IVsBuildPropertyStorage;
    if (buildPropertyStorage != null)
    {
        uint itemId;
        string fullPath = (string)project.ProjectItems.Item(
            "VsPkg.cs").Properties.Item("FullPath").Value;
        hierarchy.ParseCanonicalName(fullPath, out itemId);
        buildPropertyStorage.SetItemAttribute(itemId, "Author", "Tom");
    }
    ```

### <a name="to-obtain-the-project-hierarchy-using-ivsmonitorselection"></a>Zum Abrufen der Projekthierarchie IVsMonitorSelection verwenden

1.  Fügen Sie den folgenden Code, um Ihr VSPackage:

    ```csharp
    IVsHierarchy hierarchy = null;
    IntPtr hierarchyPtr = IntPtr.Zero;
    IntPtr selectionContainer = IntPtr.Zero;
    uint itemid;

    // Retrieve shell interface in order to get current selection
    IVsMonitorSelection monitorSelection =     Package.GetGlobalService(typeof(SVsShellMonitorSelection)) as     IVsMonitorSelection;
    if (monitorSelection == null)
        throw new InvalidOperationException();

    try
    {
        // Get the current project hierarchy, project item, and selection container for the current selection
        // If the selection spans multiple hierachies, hierarchyPtr is Zero
        IVsMultiItemSelect multiItemSelect = null;
        ErrorHandler.ThrowOnFailure(
            monitorSelection.GetCurrentSelection(
                out hierarchyPtr, out itemid,
                out multiItemSelect, out selectionContainer));

        // We only care if there is only one node selected in the tree
        if (!(itemid == VSConstants.VSITEMID_NIL ||
            hierarchyPtr == IntPtr.Zero ||
            multiItemSelect != null ||
            itemid == VSConstants.VSITEMID_SELECTION))
        {
            hierarchy = Marshal.GetObjectForIUnknown(hierarchyPtr)
                as IVsHierarchy;
        }
    }
    finally
    {
        if (hierarchyPtr != IntPtr.Zero)
            Marshal.Release(hierarchyPtr);
        if (selectionContainer != IntPtr.Zero)
            Marshal.Release(selectionContainer);
    }
    ```

2.

### <a name="to-persist-the-selected-project-item-property-given-the-project-hierarchy"></a>Das ausgewählte Projektelementeigenschaft persistent die Projekthierarchie angegeben

1.  Fügen Sie den folgenden Code an den Code in der Methode in der vorherigen Prozedur zugewiesen:

    ```csharp
    IVsBuildPropertyStorage buildPropertyStorage =
        hierarchy as IVsBuildPropertyStorage;
    if (buildPropertyStorage != null)
    {
        buildPropertyStorage.SetItemAttribute(itemId, "Author", "Tom");
    }
    ```

### <a name="to-verify-that-the-property-is-persisted"></a>Um sicherzustellen, dass die Eigenschaft beibehalten wird

1.  Starten Sie [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] und öffnen oder erstellen Sie eine Projektmappe.

2.  Wählen Sie das Projekt VsPkg.cs im Element **Projektmappen-Explorer**.

3.  Verwenden Sie einen Haltepunkt oder anderweitig zu bestimmen Sie, dass Ihr VSPackage geladen wird und dass SetItemAttribute ausgeführt wird.

    > [!NOTE]
    > Können Sie Autoload ein VSPackage in der Benutzeroberflächenkontext <xref:Microsoft.VisualStudio.VSConstants.UICONTEXT.SolutionExists_guid>. Weitere Informationen finden Sie unter [Laden von VSPackages](../extensibility/loading-vspackages.md).

4.  Schließen [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] , und öffnen Sie die Projektdatei im Editor. Daraufhin sollte die \<Autor >-Tag mit dem Wert Tom, wie folgt:

    ```xml
    <Compile Include="VsPkg.cs">
        <Author>Tom</Author>
    </Compile>
    ```

## <a name="see-also"></a>Siehe auch

- [Benutzerdefinierte Tools](../extensibility/internals/custom-tools.md)