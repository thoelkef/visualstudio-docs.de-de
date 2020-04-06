---
title: Überprüfen von Subtypes eines Projekts zur Laufzeit | Microsoft Docs
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
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/06/2020
ms.locfileid: "80698180"
---
# <a name="verify-subtypes-of-a-project-at-run-time"></a>Überprüfen von Untertypen eines Projekts zur Laufzeit
Ein VSPackage, das von einem benutzerdefinierten Projektsubtyp abhängt, sollte Logik enthalten, um nach diesem Subtype zu suchen, damit es ordnungsgemäß fehlschlagen kann, wenn der Subtype nicht vorhanden ist. Das folgende Verfahren zeigt, wie Sie das Vorhandensein eines angegebenen Subtyps überprüfen.

### <a name="to-verify-the-presence-of-a-subtype"></a>So überprüfen Sie das Vorhandensein eines Subtyps

1. Abrufen der Projekthierarchie aus den Projekt- und Projektmappenobjekten als <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy> Objekt, indem Sie dem VSPackage den folgenden Code hinzufügen.

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

2. Geben Sie die <xref:Microsoft.VisualStudio.Shell.Flavor.IVsAggregatableProjectCorrected> Hierarchie in die Schnittstelle um.

    ```csharp
    IVsAggregatableProjectCorrected AP;
    AP = hierarchy as IVsAggregatableProjectCorrected;

    ```

3. Ruft die Liste der Projekttyp-GUIDs <xref:Microsoft.VisualStudio.Shell.Flavor.IVsAggregatableProjectCorrected.GetAggregateProjectTypeGuids%2A>ab, indem Sie die aufrufen.

    ```csharp
    string projTypeGuids = AP.GetAggregateProjectTypeGuids().ToUpper();

    ```

4. Überprüfen Sie die Liste für die GUID des angegebenen Subtyps.

    ```csharp
    // Replace the string "MyGUID" with the GUID of the subtype.
    string guidMySubtype = "MyGUID";
    if (projTypeGuids.IndexOf(guidMySubtype) > 0)
    {
        // The specified subtype is present.
    }
    ```

## <a name="see-also"></a>Weitere Informationen
- [Projektuntertypen](../extensibility/internals/project-subtypes.md)
- [Projektsubtypes-Design](../extensibility/internals/project-subtypes-design.md)
- [Eigenschaften und Methoden, die durch Projektuntertypen erweitert werden](../extensibility/internals/properties-and-methods-extended-by-project-subtypes.md)
