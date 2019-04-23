---
title: Überprüfen von Untertypen eines Projekts zur Laufzeit | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- project subtypes
- check subtypes
ms.assetid: b87780ec-36a3-4e9a-9ee2-7abdc26db739
caps.latest.revision: 12
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 1e3940097ac53255b7bdd2c12c9ccc64605016e1
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/22/2019
ms.locfileid: "60061241"
---
# <a name="verifying-subtypes-of-a-project-at-run-time"></a>Überprüfen von Untertypen eines Projekts zur Laufzeit
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Eine VSPackage, die von einem benutzerdefinierten Projektuntertyp abhängt aufzunehmen Logik auf die Suche nach, die Untertyp, damit er ordnungsgemäß ausfallen kann, wenn der Untertyp nicht vorhanden ist. Das folgende Verfahren veranschaulicht das Überprüfen Sie, ob das Vorhandensein einer angegebenen Untertyp.  
  
### <a name="to-verify-the-presence-of-a-subtype"></a>Um zu überprüfen, ob das Vorhandensein eines Untertyps  
  
1. Abrufen die Projekthierarchie aus den Projekt- und Projektmappendateien Objekten als eine <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy> Objekt, indem Sie den folgenden Code hinzufügen, um Ihr VSPackage.  
  
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
  
2. Wandeln Sie die Hierarchie der <xref:Microsoft.VisualStudio.Shell.Flavor.IVsAggregatableProjectCorrected> Schnittstelle.  
  
    ```  
    IVsAggregatableProjectCorrected AP;  
    AP = hierarchy as IVsAggregatableProjectCorrected;  
  
    ```  
  
3. Rufen Sie die Liste der Projekttyp-GUIDs, durch den Aufruf der <xref:Microsoft.VisualStudio.Shell.Flavor.IVsAggregatableProjectCorrected.GetAggregateProjectTypeGuids%2A>.  
  
    ```  
    string projTypeGuids = AP.GetAggregateProjectTypeGuids().ToUpper();  
  
    ```  
  
4. Überprüfen Sie die Liste für die GUID für den angegebenen Untertyp.  
  
    ```  
    // Replace the string "MyGUID" with the GUID of the subtype.  
    string guidMySubtype = "MyGUID";  
    if (projTypeGuids.IndexOf(guidMySubtype) > 0)  
    {  
        // The specified subtype is present.  
    }  
    ```  
  
## <a name="see-also"></a>Siehe auch  
 [Projektuntertypen](../extensibility/internals/project-subtypes.md)   
 [Entwurf von Projektuntertypen](../extensibility/internals/project-subtypes-design.md)   
 [Eigenschaften und Methoden, die von Projektuntertypen erweitert werden](../extensibility/internals/properties-and-methods-extended-by-project-subtypes.md)
