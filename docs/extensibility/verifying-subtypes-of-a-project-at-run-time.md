---
title: Überprüfen von Untertypen eines Projekts zur Laufzeit | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- project subtypes
- check subtypes
ms.assetid: b87780ec-36a3-4e9a-9ee2-7abdc26db739
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: f0d739a9f8734dd8941e3254d03364cbf4c77350
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "80698180"
---
# <a name="verify-subtypes-of-a-project-at-run-time"></a>Überprüfen der Untertypen eines Projekts zur Laufzeit
Ein VSPackage, das von einem benutzerdefinierten Projekt Untertyp abhängt, sollte Logik zum Suchen nach dem Untertyp enthalten, damit er ordnungsgemäß fehlschlagen kann, wenn der Untertyp nicht vorhanden ist. Im folgenden Verfahren wird gezeigt, wie das vorhanden sein eines angegebenen unter Typs überprüft wird.

### <a name="to-verify-the-presence-of-a-subtype"></a>So überprüfen Sie das vorhanden sein eines Untertyps

1. Fügen Sie die Projekt Hierarchie aus dem Projekt und projektmappenobjekten als- <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy> Objekt ein, indem Sie den folgenden Code zu Ihrem VSPackage hinzufügen.

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

2. Wandeln Sie die Hierarchie in die- <xref:Microsoft.VisualStudio.Shell.Flavor.IVsAggregatableProjectCorrected> Schnittstelle um.

    ```csharp
    IVsAggregatableProjectCorrected AP;
    AP = hierarchy as IVsAggregatableProjectCorrected;

    ```

3. Rufen Sie die Liste der Projekttyp-GUIDs ab, indem Sie aufrufen <xref:Microsoft.VisualStudio.Shell.Flavor.IVsAggregatableProjectCorrected.GetAggregateProjectTypeGuids%2A> .

    ```csharp
    string projTypeGuids = AP.GetAggregateProjectTypeGuids().ToUpper();

    ```

4. Überprüfen Sie die Liste auf die GUID des angegebenen unter Typs.

    ```csharp
    // Replace the string "MyGUID" with the GUID of the subtype.
    string guidMySubtype = "MyGUID";
    if (projTypeGuids.IndexOf(guidMySubtype) > 0)
    {
        // The specified subtype is present.
    }
    ```

## <a name="see-also"></a>Weitere Informationen
- [Projekt Untertypen](../extensibility/internals/project-subtypes.md)
- [Entwerfen von Projekt Untertypen](../extensibility/internals/project-subtypes-design.md)
- [Eigenschaften und Methoden, die von Projekt Untertypen erweitert werden](../extensibility/internals/properties-and-methods-extended-by-project-subtypes.md)
