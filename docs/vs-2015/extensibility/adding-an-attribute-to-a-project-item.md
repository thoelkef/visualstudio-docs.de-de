---
title: Hinzufügen eines Attributs zu einem Projektelement | Microsoft-Dokumentation
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- attributes [Visual Studio], adding to a project item
ms.assetid: 404a71d5-cce5-44e7-9eaf-d747c794fedb
caps.latest.revision: 5
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 55f7c296f79b020b4c5549c8c9103205cc04d009
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/22/2018
ms.locfileid: "47514556"
---
# <a name="adding-an-attribute-to-a-project-item"></a>Hinzufügen eines Attributs zu einem Projektelement
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Die neueste Version dieses Themas finden Sie unter [Hinzufügen eines Attributs zu einem Projektelement](https://docs.microsoft.com/visualstudio/extensibility/adding-an-attribute-to-a-project-item).  
  
Die Methoden <xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildPropertyStorage.GetItemAttribute%2A> und <xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildPropertyStorage.SetItemAttribute%2A> abrufen und Festlegen des Werts der Attribute eines Projektelements. SetItemAttribute erstellt das Attribut, wenn es nicht bereits vorhanden ist, die Elementmetadaten Projekt hinzugefügt.  
  
## <a name="adding-an-attribute-to-a-project-item"></a>Hinzufügen eines Attributs zu einem Projektelement  
  
#### <a name="to-add-an-attribute-to-a-project-item"></a>Ein Attribut auf ein Projektelement hinzufügen  
  
-   Der folgende code verwendet die <xref:EnvDTE.DTE> Automatisierungsobjekt und <xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildPropertyStorage.SetItemAttribute%2A> Methode, um ein Attribut auf ein Projektelement hinzuzufügen. Die Projekt-ID wird aus dem Projekt Element namens "program.cs" abgerufen. Das Attribut "MyAttribute" ist zu diesem Projektelement hinzugefügt und den Wert "MyValue".  
  
    ```  
    EnvDTE.DTE dte = (EnvDTE.DTE)Package.GetGlobalService(typeof(EnvDTE.DTE));  
    EnvDTE.Project project = dte.Solution.Projects.Item(1);  
  
    string uniqueName = project.UniqueName;  
    IVsSolution solution =     (IVsSolution)Package.GetGlobalService(typeof(SVsSolution));  
    IVsHierarchy hierarchy;  
    solution.GetProjectOfUniqueName(uniqueName, out hierarchy);  
    IVsBuildPropertyStorage buildPropertyStorage = hierarchy as IVsBuildPropertyStorage;  
    if (buildPropertyStorage != null)  
    {  
        uint itemId;  
        string fullPath =         (string)project.ProjectItems.Item("Program.cs").Properties.Item("FullPath").Value;  
        hierarchy.ParseCanonicalName(fullPath, out itemId);  
        buildPropertyStorage.SetItemAttribute(  
            itemId, "MyAttribute", "MyValue");  
    }  
  
    ```  
  
## <a name="see-also"></a>Siehe auch  
 [Beibehalten von Daten in der MSBuild-Projektdatei](../extensibility/internals/persisting-data-in-the-msbuild-project-file.md)

