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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "62584904"
---
# <a name="verifying-subtypes-of-a-project-at-run-time"></a>Überprüfen von Untertypen eines Projekts zur Laufzeit
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Ein VSPackage, das von einem benutzerdefinierten Projekt Untertyp abhängt, sollte Logik zum Suchen nach dem Untertyp enthalten, damit er ordnungsgemäß fehlschlagen kann, wenn der Untertyp nicht vorhanden ist. Im folgenden Verfahren wird gezeigt, wie das vorhanden sein eines angegebenen unter Typs überprüft wird.  
  
### <a name="to-verify-the-presence-of-a-subtype"></a>So überprüfen Sie das vorhanden sein eines Untertyps  
  
1. Rufen Sie die Projekt Hierarchie aus dem Projekt und projektmappenobjekten als- <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy> Objekt ab, indem Sie den folgenden Code zu Ihrem VSPackage hinzufügen.  
  
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
  
2. Wandeln Sie die Hierarchie in die- <xref:Microsoft.VisualStudio.Shell.Flavor.IVsAggregatableProjectCorrected> Schnittstelle um.  
  
    ```  
    IVsAggregatableProjectCorrected AP;  
    AP = hierarchy as IVsAggregatableProjectCorrected;  
  
    ```  
  
3. Rufen Sie die Liste der Projekttyp-GUIDs ab, indem Sie aufrufen <xref:Microsoft.VisualStudio.Shell.Flavor.IVsAggregatableProjectCorrected.GetAggregateProjectTypeGuids%2A> .  
  
    ```  
    string projTypeGuids = AP.GetAggregateProjectTypeGuids().ToUpper();  
  
    ```  
  
4. Überprüfen Sie die Liste auf die GUID des angegebenen unter Typs.  
  
    ```  
    // Replace the string "MyGUID" with the GUID of the subtype.  
    string guidMySubtype = "MyGUID";  
    if (projTypeGuids.IndexOf(guidMySubtype) > 0)  
    {  
        // The specified subtype is present.  
    }  
    ```  
  
## <a name="see-also"></a>Weitere Informationen  
 [Projekt Untertypen](../extensibility/internals/project-subtypes.md)   
 [Entwerfen von Projekt Untertypen](../extensibility/internals/project-subtypes-design.md)   
 [Eigenschaften und Methoden, die von Projektuntertypen erweitert werden](../extensibility/internals/properties-and-methods-extended-by-project-subtypes.md)
