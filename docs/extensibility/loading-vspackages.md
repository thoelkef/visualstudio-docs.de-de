---
title: VSPackages laden | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- VSPackages, autoloading
- VSPackages, loading
ms.assetid: f4c3dcea-5051-4065-898f-601269649d92
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: b1c221bf06ef3b7e37e2afc1856f3e54fe5ad95e
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/06/2020
ms.locfileid: "80702963"
---
# <a name="load-vspackages"></a>VSPackages laden
VSPackages werden nur dann in Visual Studio geladen, wenn ihre Funktionalität erforderlich ist. Beispielsweise wird ein VSPackage geladen, wenn Visual Studio eine Projektfactory oder einen Dienst verwendet, den das VSPackage implementiert. Diese Funktion wird als verzögertes Laden bezeichnet, das nach Möglichkeit zur Verbesserung der Leistung verwendet wird.

> [!NOTE]
> Visual Studio kann bestimmte VSPackage-Informationen ermitteln, z. B. die Befehle, die ein VSPackage bietet, ohne das VSPackage zu laden.

 VSPackages kann so eingestellt werden, dass es in einem bestimmten Benutzeroberflächenkontext automatisch geladen wird, z. B. wenn eine Lösung geöffnet ist. Das <xref:Microsoft.VisualStudio.Shell.ProvideAutoLoadAttribute> Attribut legt diesen Kontext fest.

### <a name="autoload-a-vspackage-in-a-specific-context"></a>Automatisches Laden eines VSPackage in einem bestimmten Kontext

- Fügen `ProvideAutoLoad` Sie das Attribut den VSPackage-Attributen hinzu:

    ```csharp
    [DefaultRegistryRoot(@"Software\Microsoft\VisualStudio\14.0")]
    [PackageRegistration(UseManagedResourcesOnly = true)]
    [ProvideAutoLoad(UIContextGuids80.SolutionExists)]
    [Guid("00000000-0000-0000-0000-000000000000")] // your specific package GUID
    public class MyAutoloadedPackage : Package
    {. . .}
    ```

     Eine Liste der UI-Kontexte und deren GUID-Werte finden Sie in den aufgezählten Feldern. <xref:Microsoft.VisualStudio.Shell.Interop.UIContextGuids80>

- Legen Sie einen <xref:Microsoft.VisualStudio.Shell.Package.Initialize%2A> Haltepunkt in der Methode fest.

- Erstellen Sie das VSPackage, und beginnen Sie mit dem Debuggen.

- Laden Sie eine Lösung, oder erstellen Sie eine.

     Das VSPackage wird geladen und stoppt am Haltepunkt.

## <a name="force-a-vspackage-to-load"></a>Erzwingen des Ladens eines VSPackage
 Unter bestimmten Umständen muss ein VSPackage das Laden eines anderen VSPackage erzwingen. Beispielsweise kann ein leichtes VSPackage ein größeres VSPackage in einem Kontext laden, der nicht als CMDUIContext verfügbar ist.

 Sie können <xref:Microsoft.VisualStudio.Shell.Interop.IVsShell.LoadPackage%2A> die Methode verwenden, um das Laden eines VSPackage zu erzwingen.

- Fügen Sie diesen <xref:Microsoft.VisualStudio.Shell.Package.Initialize%2A> Code in die Methode des VSPackage ein, die das Laden eines anderen VSPackage erzwingt:

    ```csharp
    IVsShell shell = GetService(typeof(SVsShell)) as IVsShell;
    if (shell == null) return;

    IVsPackage package = null;
    Guid PackageToBeLoadedGuid =
        new Guid(Microsoft.PackageToBeLoaded.GuidList.guidPackageToBeLoadedPkgString);
    shell.LoadPackage(ref PackageToBeLoadedGuid, out package);

    ```

     Wenn das VSPackage initialisiert wird, wird das Laden erzwingen. `PackageToBeLoaded`

     Das Laden von Kraft sollte nicht für die VSPackage-Kommunikation verwendet werden. Verwenden Sie stattdessen [Use and provide services.](../extensibility/using-and-providing-services.md)

## <a name="see-also"></a>Weitere Informationen
- [VSPackages](../extensibility/internals/vspackages.md)
