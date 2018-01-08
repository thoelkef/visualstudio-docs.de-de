---
title: "Überprüfen von Untertypen von einem Projekt zur Laufzeit | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- project subtypes
- check subtypes
ms.assetid: b87780ec-36a3-4e9a-9ee2-7abdc26db739
caps.latest.revision: "11"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 18049c034286c33247aec11aba77071daa93ef5c
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/22/2017
---
# <a name="verifying-subtypes-of-a-project-at-run-time"></a>Überprüft, ob Untertypen von einem Projekt zur Laufzeit
Eine VSPackage, von die eine benutzerdefinierte Untertyp abhängt sollte Logik zu suchen, die Untertyp, damit Sie ordnungsgemäß ausgeführt werden kann, wenn der Untertyp nicht vorhanden ist enthalten. Das folgende Verfahren veranschaulicht, wie das Vorhandensein eines angegebenen Untertyps überprüfen.  
  
### <a name="to-verify-the-presence-of-a-subtype"></a>Um zu überprüfen, ob das Vorhandensein eines Untertyps  
  
1.  Abrufen die Projekthierarchie von Projekt- und Projektmappendateien Objekte als ein <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy> Objekt, indem Sie den folgenden Code hinzufügen, um Ihr VSPackage.  
  
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
  
4.  Überprüfen Sie die Liste für die GUID des dem angegebenen Untertyp.  
  
    ```  
    // Replace the string "MyGUID" with the GUID of the subtype.  
    string guidMySubtype = "MyGUID";  
    if (projTypeGuids.IndexOf(guidMySubtype) > 0)  
    {  
        // The specified subtype is present.  
    }  
    ```  
  
## <a name="see-also"></a>Siehe auch  
 [Projekt Untertypen](../extensibility/internals/project-subtypes.md)   
 [Projekt Untertypen Entwurf](../extensibility/internals/project-subtypes-design.md)   
 [Eigenschaften und Methoden, die von Projektuntertypen erweitert werden](../extensibility/internals/properties-and-methods-extended-by-project-subtypes.md)