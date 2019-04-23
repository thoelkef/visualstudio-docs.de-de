---
title: Laden von VSPackages | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- VSPackages, autoloading
- VSPackages, loading
ms.assetid: f4c3dcea-5051-4065-898f-601269649d92
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: ce0f09c1749621838729e1e4f64feb3ca8b07628
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/22/2019
ms.locfileid: "60117563"
---
# <a name="load-vspackages"></a>Laden von VSPackages
VSPackages sind in Visual Studio geladen werden, nur, wenn ihre Funktionalität erforderlich ist. Beispielsweise wird eine VSPackage geladen, wenn Visual Studio verwendet eine Projektzuordnungsinstanz oder ein Dienst, den das VSPackage implementiert. Dieses Feature heißt verzögertes Laden, die nach Möglichkeit zur Verbesserung der Leistung verwendet wird.

> [!NOTE]
>  Visual Studio kann bestimmte VSPackage-Informationen, z. B. der Befehle bestimmen, die eine VSPackage bietet, ohne Sie zu das VSPackage zu laden.

 VSPackages kann z. B. Automatisches Laden, in einem bestimmten Benutzerkontext von Benutzeroberfläche (UI) festgelegt werden, wenn eine Projektmappe geöffnet ist. Die <xref:Microsoft.VisualStudio.Shell.ProvideAutoLoadAttribute> -Attribut wird von diesem Kontext.

### <a name="autoload-a-vspackage-in-a-specific-context"></a>Automatisches Laden eines VSPackages in einem bestimmten Kontext

- Hinzufügen der `ProvideAutoLoad` -Attribut auf die VSPackage-Attribute:

    ```csharp
    [DefaultRegistryRoot(@"Software\Microsoft\VisualStudio\14.0")]
    [PackageRegistration(UseManagedResourcesOnly = true)]
    [ProvideAutoLoad(UIContextGuids80.SolutionExists)]
    [Guid("00000000-0000-0000-0000-000000000000")] // your specific package GUID
    public class MyAutoloadedPackage : Package
    {. . .}
    ```

     Finden Sie unter den aufgelisteten Felder <xref:Microsoft.VisualStudio.Shell.Interop.UIContextGuids80> für eine Liste mit den Benutzeroberfläche-Kontexte und die GUID-Werte.

- Festlegen eines Haltepunkts in der <xref:Microsoft.VisualStudio.Shell.Package.Initialize%2A> Methode.

- Das VSPackage zu erstellen und mit dem Debuggen beginnen.

- Laden Sie eine Projektmappe, oder erstellen.

     Das VSPackage lädt, und die Ausführung am Haltepunkt beendet.

## <a name="force-a-vspackage-to-load"></a>Erzwingen eines VSPackage geladen
 Unter bestimmten Umständen möglicherweise eine VSPackage Erzwingen von einem anderen VSPackage geladen werden. Eine einfache VSPackage kann z. B. eine größeren VSPackage in einem Kontext laden, die nicht als eine CMDUIContext verfügbar ist.

 Sie können die <xref:Microsoft.VisualStudio.Shell.Interop.IVsShell.LoadPackage%2A> -Methode zum Erzwingen eines VSPackages zu laden.

- Fügen Sie diesen Code in die <xref:Microsoft.VisualStudio.Shell.Package.Initialize%2A> -Methode des VSPackages, die erzwingt, einem anderen VSPackage dass zu laden:

    ```csharp
    IVsShell shell = GetService(typeof(SVsShell)) as IVsShell;
    if (shell == null) return;

    IVsPackage package = null;
    Guid PackageToBeLoadedGuid =
        new Guid(Microsoft.PackageToBeLoaded.GuidList.guidPackageToBeLoadedPkgString);
    shell.LoadPackage(ref PackageToBeLoadedGuid, out package);

    ```

     Bei der Initialisierung des VSPackages wird gezwungen `PackageToBeLoaded` geladen.

     -Force-Loading sollte nicht für die VSPackage-Kommunikation verwendet werden. Verwendung [verwenden und Dienste bereitstellen](../extensibility/using-and-providing-services.md) stattdessen.

## <a name="see-also"></a>Siehe auch
- [VSPackages](../extensibility/internals/vspackages.md)
