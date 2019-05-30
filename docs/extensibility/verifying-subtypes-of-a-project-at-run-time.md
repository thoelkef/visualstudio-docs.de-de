---
title: Überprüfen von Untertypen eines Projekts zur Laufzeit | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- project subtypes
- check subtypes
ms.assetid: b87780ec-36a3-4e9a-9ee2-7abdc26db739
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 033f2971d0b8acb0390765f240a86a5ff543c353
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/29/2019
ms.locfileid: "66310687"
---
# <a name="verify-subtypes-of-a-project-at-run-time"></a>Überprüfen von Untertypen eines Projekts zur Laufzeit
Eine VSPackage, die von einem benutzerdefinierten Projektuntertyp abhängt aufzunehmen Logik auf die Suche nach, die Untertyp, damit er ordnungsgemäß ausfallen kann, wenn der Untertyp nicht vorhanden ist. Das folgende Verfahren veranschaulicht das Überprüfen Sie, ob das Vorhandensein einer angegebenen Untertyp.

### <a name="to-verify-the-presence-of-a-subtype"></a>Um zu überprüfen, ob das Vorhandensein eines Untertyps

1. Rufen Sie die Projekthierarchie aus den Projekt- und Projektmappendateien Objekten wie eine <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy> Objekt, indem Sie den folgenden Code hinzufügen, um Ihr VSPackage.

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

2. Wandeln Sie die Hierarchie der <xref:Microsoft.VisualStudio.Shell.Flavor.IVsAggregatableProjectCorrected> Schnittstelle.

    ```csharp
    IVsAggregatableProjectCorrected AP;
    AP = hierarchy as IVsAggregatableProjectCorrected;

    ```

3. Rufen Sie die Liste der Projekttyp-GUIDs, durch den Aufruf der <xref:Microsoft.VisualStudio.Shell.Flavor.IVsAggregatableProjectCorrected.GetAggregateProjectTypeGuids%2A>.

    ```csharp
    string projTypeGuids = AP.GetAggregateProjectTypeGuids().ToUpper();

    ```

4. Überprüfen Sie die Liste für die GUID für den angegebenen Untertyp.

    ```csharp
    // Replace the string "MyGUID" with the GUID of the subtype.
    string guidMySubtype = "MyGUID";
    if (projTypeGuids.IndexOf(guidMySubtype) > 0)
    {
        // The specified subtype is present.
    }
    ```

## <a name="see-also"></a>Siehe auch
- [Projektuntertypen](../extensibility/internals/project-subtypes.md)
- [Entwurf von Projektuntertypen](../extensibility/internals/project-subtypes-design.md)
- [Eigenschaften und Methoden, die von Projektuntertypen erweitert](../extensibility/internals/properties-and-methods-extended-by-project-subtypes.md)