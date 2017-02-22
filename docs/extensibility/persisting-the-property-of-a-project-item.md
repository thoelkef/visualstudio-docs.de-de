---
title: "Die Eigenschaft eines Projektelements beibehalten | Microsoft Docs"
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
  - "Eigenschaften, die einem Projektelement hinzufügen"
  - "Projektelemente, Hinzufügen von Eigenschaften"
ms.assetid: d7a0f2b0-d427-4d49-9536-54edfb37c0f3
caps.latest.revision: 7
caps.handback.revision: 7
ms.author: "gregvanl"
manager: "ghogen"
---
# Die Eigenschaft eines Projektelements beibehalten
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Kann eine Eigenschaft beibehalten werden sollen, die Sie ein Projektelement, z. B. der Autor einer Quelldatei hinzufügen. Dazu können Sie die Eigenschaft in der Projektdatei gespeichert.  
  
 Der erste Schritt eine Eigenschaft in einer Projektdatei beibehalten wird, zum Abrufen der Hierarchie des Projekts als eine <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy> Schnittstelle. Sie erhalten diese Schnittstelle durch Automatisierung oder mithilfe von <xref:Microsoft.VisualStudio.Shell.Interop.IVsMonitorSelection>. Nachdem Sie die Schnittstelle erhalten haben, können Sie es verwenden, um zu bestimmen, welche Projektelement derzeit ausgewählt ist. Nachdem Sie die Projekt\-ID haben, können Sie <xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildPropertyStorage.SetItemAttribute%2A> zum Hinzufügen der Eigenschaft.  
  
 In den folgenden Verfahren, die Sie beibehalten der Eigenschaft VsPkg.cs `Author` mit dem Wert `Tom` in der Projektdatei.  
  
### Zum Abrufen der Projekthierarchie das DTE\-Objekt  
  
1.  Fügen Sie den folgenden Code, um das VSPackage:  
  
    ```c#  
    EnvDTE.DTE dte = (EnvDTE.DTE)Package.GetGlobalService(typeof(EnvDTE.DTE)); EnvDTE.Project project = dte.Solution.Projects.Item(1); string uniqueName = project.UniqueName; IVsSolution solution = (IVsSolution)Package.GetGlobalService(typeof(SVsSolution)); IVsHierarchy hierarchy; solution.GetProjectOfUniqueName(uniqueName, out hierarchy);  
    ```  
  
### Die Projekt\-Item\-Eigenschaft mit dem DTE\-Objekt beibehalten werden.  
  
1.  Fügen Sie den folgenden Code, um den Code in der Methode in der vorherigen Prozedur gegeben:  
  
    ```c#  
    IVsBuildPropertyStorage buildPropertyStorage = hierarchy as IVsBuildPropertyStorage; if (buildPropertyStorage != null) { uint itemId; string fullPath = (string)project.ProjectItems.Item( "VsPkg.cs").Properties.Item("FullPath").Value; hierarchy.ParseCanonicalName(fullPath, out itemId); buildPropertyStorage.SetItemAttribute(itemId, "Author", "Tom"); }  
    ```  
  
### Zum Abrufen der Projekthierarchie mit IVsMonitorSelection  
  
1.  Fügen Sie den folgenden Code, um das VSPackage:  
  
    ```c#  
    IVsHierarchy hierarchy = null; IntPtr hierarchyPtr = IntPtr.Zero; IntPtr selectionContainer = IntPtr.Zero; uint itemid; // Retrieve shell interface in order to get current selection IVsMonitorSelection monitorSelection =     Package.GetGlobalService(typeof(SVsShellMonitorSelection)) as     IVsMonitorSelection; if (monitorSelection == null) throw new InvalidOperationException(); try { // Get the current project hierarchy, project item, and selection container for the current selection // If the selection spans multiple hierachies, hierarchyPtr is Zero IVsMultiItemSelect multiItemSelect = null; ErrorHandler.ThrowOnFailure( monitorSelection.GetCurrentSelection( out hierarchyPtr, out itemid, out multiItemSelect, out selectionContainer)); // We only care if there is only one node selected in the tree if (!(itemid == VSConstants.VSITEMID_NIL || hierarchyPtr == IntPtr.Zero || multiItemSelect != null || itemid == VSConstants.VSITEMID_SELECTION)) { hierarchy = Marshal.GetObjectForIUnknown(hierarchyPtr) as IVsHierarchy; } } finally { if (hierarchyPtr != IntPtr.Zero) Marshal.Release(hierarchyPtr); if (selectionContainer != IntPtr.Zero) Marshal.Release(selectionContainer); }  
    ```  
  
2.  
  
### Item\-Eigenschaft der ausgewählten Projekt beibehalten werden, erhält die Projekthierarchie  
  
1.  Fügen Sie den folgenden Code, um den Code in der Methode in der vorherigen Prozedur gegeben:  
  
    ```  
    IVsBuildPropertyStorage buildPropertyStorage = hierarchy as IVsBuildPropertyStorage; if (buildPropertyStorage != null) { buildPropertyStorage.SetItemAttribute(itemId, "Author", "Tom"); }  
    ```  
  
### Um sicherzustellen, dass die Eigenschaft gespeichert wird  
  
1.  Starten Sie [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] und öffnen oder erstellen Sie eine Lösung.  
  
2.  Wählen Sie das Projekt VsPkg.cs im Element **Projektmappen\-Explorer**.  
  
3.  Verwenden Sie einen Haltepunkt oder andernfalls zu bestimmen Sie, dass das VSPackage geladen wird und dass SetItemAttribute ausgeführt wird.  
  
    > [!NOTE]
    >  Automatisches Laden eines VSPackages in dem Benutzeroberflächenkontext können <xref:Microsoft.VisualStudio.VSConstants.UICONTEXT_SolutionExists>. Weitere Informationen finden Sie unter [Laden von VSPackages](../extensibility/loading-vspackages.md).  
  
4.  Schließen [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] und öffnen Sie die Datei in Editor. Das Tag \< Author \> mit dem Wert Tom, sollte wie folgt angezeigt werden:  
  
    ```  
    <Compile Include="VsPkg.cs"> <Author>Tom</Author> </Compile>  
    ```  
  
## Siehe auch  
 [Benutzerdefinierte Tools](../extensibility/internals/custom-tools.md)