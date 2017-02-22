---
title: "Hinzuf&#252;gen eines Attributs zu einem Projekt ein Projektelement | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Attribute [Visual Studio] ein Projektelement hinzufügen"
ms.assetid: 404a71d5-cce5-44e7-9eaf-d747c794fedb
caps.latest.revision: 4
caps.handback.revision: 4
ms.author: "gregvanl"
manager: "ghogen"
---
# Hinzuf&#252;gen eines Attributs zu einem Projekt ein Projektelement
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Das <xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildPropertyStorage.GetItemAttribute%2A>\-Methoden und \- <xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildPropertyStorage.SetItemAttribute%2A> Abrufen und legen Sie den Wert der Attribute eines Projektelements fest.  SetItemAttribute erstellt das Attribut, wenn es nicht bereits vorhanden ist und fügt ihn an den Metadaten des Projektelements hinzugefügt.  
  
## Ein Attribut auf ein Projektelement hinzu  
  
#### So fügen Sie einem Projektelement ein Attribut hinzu  
  
-   Im folgenden Code wird das <xref:EnvDTE.DTE> Automatisierungsobjekt und die <xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildPropertyStorage.SetItemAttribute%2A>\-Methode, um ein Attribut zu einem Projektelement hinzuzufügen.  Die Projektelement ID wird vom Projektelementnamen „program.cs“ abgerufen.  Das Attribut „MyAttribute“ wird mit diesem Projektelement und der Wert „MyValue“ hinzugefügt.  
  
    ```  
    EnvDTE.DTE dte = (EnvDTE.DTE)Package.GetGlobalService(typeof(EnvDTE.DTE));  
    EnvDTE.Project project = dte.Solution.Projects.Item(1);  
  
    string uniqueName = project.UniqueName;  
    IVsSolution solution =     (IVsSolution)Package.GetGlobalService(typeof(SVsSolution));  
    IVsHierarchy hierarchy;  
    solution.GetProjectOfUniqueName(uniqueName, out hierarchy);  
    IVsBuildPropertyStorage buildPropertyStorage = hierarchy as IVsBuildPropertyStorage;  
    if (buildPropertyStorage != null)  
    {  
        uint itemId;  
        string fullPath =         (string)project.ProjectItems.Item("Program.cs").Properties.Item("FullPath").Value;  
        hierarchy.ParseCanonicalName(fullPath, out itemId);  
        buildPropertyStorage.SetItemAttribute(  
            itemId, "MyAttribute", "MyValue");  
    }  
  
    ```  
  
## Siehe auch  
 [Beibehalten von Daten in der MSBuild\-Projektdatei](../extensibility/internals/persisting-data-in-the-msbuild-project-file.md)