---
title: Überprüfen von Untertypen eines Projekts zur Laufzeit | Microsoft-Dokumentation
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
- project subtypes
- check subtypes
ms.assetid: b87780ec-36a3-4e9a-9ee2-7abdc26db739
caps.latest.revision: 12
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: e77fa60687ecfebdae8555b516af678cf3966211
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/22/2018
ms.locfileid: "47511963"
---
# <a name="verifying-subtypes-of-a-project-at-run-time"></a>Überprüfen von Untertypen eines Projekts zur Laufzeit
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Die neueste Version dieses Themas finden Sie unter [Überprüfen von Untertypen eines Projekts zur Laufzeit](https://docs.microsoft.com/visualstudio/extensibility/verifying-subtypes-of-a-project-at-run-time).  
  
Eine VSPackage, die von einem benutzerdefinierten Projektuntertyp abhängt aufzunehmen Logik auf die Suche nach, die Untertyp, damit er ordnungsgemäß ausfallen kann, wenn der Untertyp nicht vorhanden ist. Das folgende Verfahren veranschaulicht das Überprüfen Sie, ob das Vorhandensein einer angegebenen Untertyp.  
  
### <a name="to-verify-the-presence-of-a-subtype"></a>Um zu überprüfen, ob das Vorhandensein eines Untertyps  
  
1.  Abrufen die Projekthierarchie aus den Projekt- und Projektmappendateien Objekten als eine <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy> Objekt, indem Sie den folgenden Code hinzufügen, um Ihr VSPackage.  
  
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
  
3.  Rufen Sie die Liste der Projekttyp-GUIDs, durch den Aufruf der <xref:Microsoft.VisualStudio.Shell.Flavor.IVsAggregatableProjectCorrected.GetAggregateProjectTypeGuids%2A>.  
  
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
  
## <a name="see-also"></a>Siehe auch  
 [Projektuntertypen](../extensibility/internals/project-subtypes.md)   
 [Entwurf von Projektuntertypen](../extensibility/internals/project-subtypes-design.md)   
 [Eigenschaften und Methoden, die von Projektuntertypen erweitert werden](../extensibility/internals/properties-and-methods-extended-by-project-subtypes.md)

