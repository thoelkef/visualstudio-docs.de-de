---
title: Überprüfen von Untertypen eines Projekts zur Laufzeit | Microsoft-Dokumentation
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- project subtypes
- check subtypes
ms.assetid: b87780ec-36a3-4e9a-9ee2-7abdc26db739
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 22e3205f3a8bd8ef7ce7e44b775ae1ef5a30cfa5
ms.sourcegitcommit: 56ae5032d99d948aae0548ae318ca2bae97ea962
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/07/2018
ms.locfileid: "39586208"
---
# <a name="verify-subtypes-of-a-project-at-run-time"></a>Überprüfen von Untertypen eines Projekts zur Laufzeit
Eine VSPackage, die von einem benutzerdefinierten Projektuntertyp abhängt aufzunehmen Logik auf die Suche nach, die Untertyp, damit er ordnungsgemäß ausfallen kann, wenn der Untertyp nicht vorhanden ist. Das folgende Verfahren veranschaulicht das Überprüfen Sie, ob das Vorhandensein einer angegebenen Untertyp.  
  
### <a name="to-verify-the-presence-of-a-subtype"></a>Um zu überprüfen, ob das Vorhandensein eines Untertyps  
  
1.  Rufen Sie die Projekthierarchie aus den Projekt- und Projektmappendateien Objekten wie eine <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy> Objekt, indem Sie den folgenden Code hinzufügen, um Ihr VSPackage.  
  
    ```csharp  
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
  
    ```csharp  
    IVsAggregatableProjectCorrected AP;  
    AP = hierarchy as IVsAggregatableProjectCorrected;  
  
    ```  
  
3.  Rufen Sie die Liste der Projekttyp-GUIDs, durch den Aufruf der <xref:Microsoft.VisualStudio.Shell.Flavor.IVsAggregatableProjectCorrected.GetAggregateProjectTypeGuids%2A>.  
  
    ```csharp  
    string projTypeGuids = AP.GetAggregateProjectTypeGuids().ToUpper();  
  
    ```  
  
4.  Überprüfen Sie die Liste für die GUID für den angegebenen Untertyp.  
  
    ```csharp  
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
 [Eigenschaften und Methoden, die von Projektuntertypen erweitert](../extensibility/internals/properties-and-methods-extended-by-project-subtypes.md)