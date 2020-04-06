---
title: Beibehalten der Eigenschaft eines Projektelements | Microsoft Docs
ms.date: 03/22/2018
ms.topic: conceptual
helpviewer_keywords:
- properties, adding to a project item
- project items, adding properties
ms.assetid: d7a0f2b0-d427-4d49-9536-54edfb37c0f3
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 15c280f15436a5e27bcc0dcc4d2fb9e9bdd82933
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/06/2020
ms.locfileid: "80702209"
---
# <a name="persist-the-property-of-a-project-item"></a>Beibehalten der Eigenschaft eines Projektelements
Sie können eine Eigenschaft beibehalten, die Sie einem Projektelement hinzufügen, z. B. dem Autor einer Quelldatei. Sie können dies tun, indem Sie die Eigenschaft in der Projektdatei speichern.

 Der erste Schritt, um eine Eigenschaft in einer Projektdatei beizubehalten, besteht darin, die Hierarchie des Projekts als <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy> Schnittstelle abzuspeichern. Sie können diese Schnittstelle entweder mithilfe <xref:Microsoft.VisualStudio.Shell.Interop.IVsMonitorSelection>von Automation oder mithilfe von erhalten. Sobald Sie die Schnittstelle erhalten haben, können Sie damit bestimmen, welches Projektelement derzeit ausgewählt ist. Sobald Sie über die Projektelement-ID verfügen, können <xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildPropertyStorage.SetItemAttribute%2A> Sie die Eigenschaft hinzufügen.

 In den folgenden Verfahren beibehalten `Author` Sie die `Tom` *VsPkg.cs-Eigenschaft* mit dem Wert in der Projektdatei.

## <a name="to-obtain-the-project-hierarchy-with-the-dte-object"></a>So rufen Sie die Projekthierarchie mit dem DTE-Objekt ab

1. Fügen Sie Ihrem VSPackage den folgenden Code hinzu:

    ```csharp
    EnvDTE.DTE dte = (EnvDTE.DTE)Package.GetGlobalService(typeof(EnvDTE.DTE));
    EnvDTE.Project project = dte.Solution.Projects.Item(1);

    string uniqueName = project.UniqueName;
    IVsSolution solution = (IVsSolution)Package.GetGlobalService(typeof(SVsSolution));
    IVsHierarchy hierarchy;
    solution.GetProjectOfUniqueName(uniqueName, out hierarchy);
    ```

## <a name="to-persist-the-project-item-property-with-the-dte-object"></a>So bleiben sie bei der Projektelementeigenschaft mit dem DTE-Objekt erhalten

1. Fügen Sie dem Code, der in der Methode im vorherigen Verfahren angegeben ist, den folgenden Code hinzu:

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

## <a name="to-obtain-the-project-hierarchy-using-ivsmonitorselection"></a>So erhalten Sie die Projekthierarchie mithilfe von IVsMonitorSelection

1. Fügen Sie Ihrem VSPackage den folgenden Code hinzu:

    ```csharp
    IVsHierarchy hierarchy = null;
    IntPtr hierarchyPtr = IntPtr.Zero;
    IntPtr selectionContainer = IntPtr.Zero;
    uint itemid;

    // Retrieve shell interface in order to get current selection
    IVsMonitorSelection monitorSelection =     Package.GetGlobalService(typeof(SVsShellMonitorSelection)) as     IVsMonitorSelection;
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

## <a name="to-persist-the-selected-project-item-property-given-the-project-hierarchy"></a>So bleiben Sie die ausgewählte Projektelementeigenschaft beibehalten, wenn Sie die Projekthierarchie

1. Fügen Sie dem Code, der in der Methode im vorherigen Verfahren angegeben ist, den folgenden Code hinzu:

    ```csharp
    IVsBuildPropertyStorage buildPropertyStorage =
        hierarchy as IVsBuildPropertyStorage;
    if (buildPropertyStorage != null)
    {
        buildPropertyStorage.SetItemAttribute(itemId, "Author", "Tom");
    }
    ```

## <a name="to-verify-that-the-property-is-persisted"></a>So überprüfen Sie, ob die Eigenschaft beibehalten wird

1. Starten [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] Sie eine Lösung, und öffnen Sie sie diese.

2. Wählen Sie das Projektelement VsPkg.cs im **Projektmappen-Explorer**aus.

3. Verwenden Sie einen Haltepunkt, oder bestimmen Sie auf andere Weise, ob Ihr VSPackage geladen und SetItemAttribute ausgeführt wird.

   > [!NOTE]
   > Sie können ein VSPackage automatisch <xref:Microsoft.VisualStudio.VSConstants.UICONTEXT.SolutionExists_guid>im UI-Kontext laden. Weitere Informationen finden Sie unter Laden von [VSPackages](../extensibility/loading-vspackages.md).

4. Schließen [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] Sie die Projektdatei in Notepad, und öffnen Sie sie dann. Sie sollten \<das Author>-Tag mit dem Wert Tom wie folgt sehen:

   ```xml
   <Compile Include="VsPkg.cs">
       <Author>Tom</Author>
   </Compile>
   ```

## <a name="see-also"></a>Weitere Informationen

- [Benutzerdefinierte Werkzeuge](../extensibility/internals/custom-tools.md)
