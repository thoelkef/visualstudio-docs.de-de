---
title: Hinzufügen eines Attributs zu einem Projekt Element | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- attributes [Visual Studio], adding to a project item
ms.assetid: 404a71d5-cce5-44e7-9eaf-d747c794fedb
caps.latest.revision: 5
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 1740ac4dfdeb64d5b4b2b0aab264845de9c186dd
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "68184816"
---
# <a name="adding-an-attribute-to-a-project-item"></a>Hinzufügen eines Attributs zu einem Projektelement
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Mit den Methoden <xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildPropertyStorage.GetItemAttribute%2A> und wird <xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildPropertyStorage.SetItemAttribute%2A> der Wert der Attribute eines Projekt Elements erhalten und festgelegt. "", Wenn das Attribut nicht bereits vorhanden ist, wird das Attribut erstellt, und die Metadaten werden den Projekt Element Metadaten hinzugefügt.  
  
## <a name="adding-an-attribute-to-a-project-item"></a>Hinzufügen eines Attributs zu einem Projekt Element  
  
#### <a name="to-add-an-attribute-to-a-project-item"></a>So fügen Sie einem Projekt Element ein Attribut hinzu  
  
- Im folgenden Code werden das <xref:EnvDTE.DTE> Automation-Objekt und die- <xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildPropertyStorage.SetItemAttribute%2A> Methode verwendet, um einem Projekt Element ein Attribut hinzuzufügen. Die Projekt Element-ID wird aus dem Projekt Elementnamen "Program.cs" abgerufen. Das Attribut "MyAttribute" wird diesem Projekt Element hinzugefügt und erhält den Wert "myValue".  
  
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
  
## <a name="see-also"></a>Weitere Informationen  
 [Beibehalten von Daten in der MSBuild-Projektdatei](../extensibility/internals/persisting-data-in-the-msbuild-project-file.md)
