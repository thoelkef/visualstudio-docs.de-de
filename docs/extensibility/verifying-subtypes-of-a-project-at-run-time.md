---
title: "&#220;berpr&#252;ft, ob Untertypen eines Projekts zur Laufzeit | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Projekt-Untertypen"
  - "Überprüfen von Untertypen"
ms.assetid: b87780ec-36a3-4e9a-9ee2-7abdc26db739
caps.latest.revision: 11
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 11
---
# &#220;berpr&#252;ft, ob Untertypen eines Projekts zur Laufzeit
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Ein VSPackage, das einen benutzerdefinierten Untertyp abhängt aufzunehmen Logik gesucht, die Untertyp, damit Sie ordnungsgemäß ausgeführt werden kann, wenn der Untertyp nicht vorhanden ist. Das folgende Verfahren zeigt, wie das Vorhandensein eines bestimmten Untertyps überprüfen.  
  
### Das Vorhandensein eines Untertyps überprüft  
  
1.  Abrufen die Projekthierarchie von Projekt\- und Projektmappendateien Objekte als ein <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy> Objekt, indem Sie den folgenden Code an Ihr VSPackage.  
  
    ```  
    EnvDTE.DTE dte;  
    dte = (EnvDTE.DTE)Package.GetGlobalService(typeof(EnvDTE.DTE));  
  
    EnvDTE.Project project;  
    project = dte.Solution.Projects.Item(1);  
  
    IVsSolution solution;  
    solution = (IVsSolution)Package.GetGlobalService(typeof(SVsSolution));  
  
    IVsHierarchy hierarchy;  
    hierarchy = solution.GetProjectOfUniqueName(project.UniqueName);  
  
    ```  
  
2.  Wandeln Sie die Hierarchie der <xref:Microsoft.VisualStudio.Shell.Flavor.IVsAggregatableProjectCorrected> Schnittstelle.  
  
    ```  
    IVsAggregatableProjectCorrected AP;  
    AP = hierarchy as IVsAggregatableProjectCorrected;  
  
    ```  
  
3.  Rufen Sie die Liste der Projekttyp GUIDs durch Aufrufen der <xref:Microsoft.VisualStudio.Shell.Flavor.IVsAggregatableProjectCorrected.GetAggregateProjectTypeGuids%2A>.  
  
    ```  
    string projTypeGuids = AP.GetAggregateProjectTypeGuids().ToUpper();  
  
    ```  
  
4.  Überprüfen Sie die Liste für die GUID für den angegebenen Untertyp.  
  
    ```  
    // Replace the string "MyGUID" with the GUID of the subtype.  
    string guidMySubtype = "MyGUID";  
    if (projTypeGuids.IndexOf(guidMySubtype) > 0)  
    {  
        // The specified subtype is present.  
    }  
    ```  
  
## Siehe auch  
 [Projekt\-Untertypen](../extensibility/internals/project-subtypes.md)   
 [Project Untertypen Design](../extensibility/internals/project-subtypes-design.md)   
 [Eigenschaften und Methoden, die vom Projekt Untertypen erweitert](../extensibility/internals/properties-and-methods-extended-by-project-subtypes.md)