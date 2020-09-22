---
title: Beibehalten der Eigenschaft eines Projekt Elements | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- properties, adding to a project item
- project items, adding properties
ms.assetid: d7a0f2b0-d427-4d49-9536-54edfb37c0f3
caps.latest.revision: 8
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 4adcf0f5c5770f5d3ffc0e0ed9bffdb108869c7f
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "90840954"
---
# <a name="persisting-the-property-of-a-project-item"></a>Beibehalten der Eigenschaft eines Projektelements
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Möglicherweise möchten Sie eine Eigenschaft persistent speichern, die Sie einem Projekt Element hinzufügen, z. b. den Autor einer Quelldatei. Dies können Sie erreichen, indem Sie die-Eigenschaft in der Projektdatei speichern.  
  
 Der erste Schritt, um eine Eigenschaft in einer Projektdatei beizubehalten, besteht darin, die Hierarchie des Projekts als <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy> Schnittstelle zu erhalten. Sie können diese Schnittstelle entweder mithilfe von Automation oder mithilfe von abrufen <xref:Microsoft.VisualStudio.Shell.Interop.IVsMonitorSelection> . Nachdem Sie die Schnittstelle erhalten haben, können Sie Sie verwenden, um zu bestimmen, welches Projekt Element derzeit ausgewählt ist. Wenn Sie die Projekt Element-ID haben, können Sie verwenden, <xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildPropertyStorage.SetItemAttribute%2A> um die Eigenschaft hinzuzufügen.  
  
 In den folgenden Prozeduren speichern Sie die vspkg.cs-Eigenschaft `Author` mit dem Wert `Tom` in der Projektdatei.  
  
### <a name="to-obtain-the-project-hierarchy-with-the-dte-object"></a>So rufen Sie die Projekt Hierarchie mit dem DTE-Objekt ab  
  
1. Fügen Sie dem VSPackage den folgenden Code hinzu:  
  
    ```csharp  
    EnvDTE.DTE dte = (EnvDTE.DTE)Package.GetGlobalService(typeof(EnvDTE.DTE));  
    EnvDTE.Project project = dte.Solution.Projects.Item(1);  
  
    string uniqueName = project.UniqueName;  
    IVsSolution solution = (IVsSolution)Package.GetGlobalService(typeof(SVsSolution));  
    IVsHierarchy hierarchy;  
    solution.GetProjectOfUniqueName(uniqueName, out hierarchy);  
    ```  
  
### <a name="to-persist-the-project-item-property-with-the-dte-object"></a>So speichern Sie die Projekt Element Eigenschaft mit dem DTE-Objekt  
  
1. Fügen Sie dem Code, der in der-Methode in der vorherigen Prozedur angegeben wurde, den folgenden Code hinzu:  
  
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
  
### <a name="to-obtain-the-project-hierarchy-using-ivsmonitorselection"></a>So rufen Sie die Projekt Hierarchie mithilfe von ivsmonitorselection ab  
  
1. Fügen Sie dem VSPackage den folgenden Code hinzu:  
  
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
  
2. 
  
### <a name="to-persist-the-selected-project-item-property-given-the-project-hierarchy"></a>So speichern Sie die ausgewählte Projekt Element Eigenschaft mit der angegebenen Projekt Hierarchie  
  
1. Fügen Sie dem Code, der in der-Methode in der vorherigen Prozedur angegeben wurde, den folgenden Code hinzu:  
  
    ```  
    IVsBuildPropertyStorage buildPropertyStorage =   
        hierarchy as IVsBuildPropertyStorage;  
    if (buildPropertyStorage != null)  
    {  
        buildPropertyStorage.SetItemAttribute(itemId, "Author", "Tom");  
    }  
    ```  
  
### <a name="to-verify-that-the-property-is-persisted"></a>So überprüfen Sie, ob die Eigenschaft persistent ist  
  
1. Starten Sie, [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] und öffnen oder erstellen Sie eine Projekt Mappe.  
  
2. Wählen Sie das Projekt Element vspkg.cs in **Projektmappen-Explorer**aus.  
  
3. Verwenden Sie einen Haltepunkt, oder stellen Sie auf andere Weise fest, dass das VSPackage geladen und das Attribut "" auf "" festgelegt ist.  
  
    > [!NOTE]
    > Sie können ein VSPackage im UI-Kontext autolocken <xref:Microsoft.VisualStudio.VSConstants.UICONTEXT.SolutionExists_guid> . Weitere Informationen finden Sie unter [Laden von VSPackages](../extensibility/loading-vspackages.md).  
  
4. Schließen Sie [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] die Projektdatei, und öffnen Sie Sie dann in Notepad. Das \<Author> Tag mit dem Wert Tom sollte wie folgt angezeigt werden:  
  
    ```  
    <Compile Include="VsPkg.cs">  
        <Author>Tom</Author>  
    </Compile>  
    ```  
  
## <a name="see-also"></a>Weitere Informationen  
 [Benutzerdefinierte Tools](../extensibility/internals/custom-tools.md)
