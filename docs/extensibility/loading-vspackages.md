---
title: Laden von VSPackages | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- VSPackages, autoloading
- VSPackages, loading
ms.assetid: f4c3dcea-5051-4065-898f-601269649d92
caps.latest.revision: "17"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 5efc043ae6e88f3f7b3c989a2c37c0ff9f555dd6
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/22/2017
---
# <a name="loading-vspackages"></a>Laden von VSPackages
VSPackages sind in Visual Studio nur geladen, wenn ihre Funktionalität erforderlich ist. Beispielsweise wird eine VSPackage geladen, wenn Visual Studio verwendet, ein Projekt Vorinstallations- oder ein Dienst, den das VSPackage implementiert. Dieses Feature heißt verzögertes Laden, die nach Möglichkeit zur Verbesserung der Leistung verwendet wird.  
  
> [!NOTE]
>  Visual Studio kann bestimmte VSPackage-Informationen, z. B. die Befehle ermitteln, die eine VSPackage bietet, ohne zu laden das VSPackage.  
  
 VSPackages können z. B. auf Autoload in einem bestimmten Benutzerkontext von Benutzeroberfläche (UI) festgelegt werden, wenn eine Projektmappe geöffnet ist. Die <xref:Microsoft.VisualStudio.Shell.ProvideAutoLoadAttribute> Attribut legt dieser Kontext fest.  
  
### <a name="autoloading-a-vspackage-in-a-specific-context"></a>Automatisches Laden ein VSPackage in einem bestimmten Kontext  
  
-   Hinzufügen der `ProvideAutoLoad` -Attribut auf die VSPackage-Attribute:  
  
    ```csharp  
    [DefaultRegistryRoot(@"Software\Microsoft\VisualStudio\14.0")]  
    [PackageRegistration(UseManagedResourcesOnly = true)]  
    [ProvideAutoLoad(UIContextGuids80.SolutionExists)]  
    [Guid("00000000-0000-0000-0000-000000000000")] // your specific package GUID  
    public class MyAutoloadedPackage : Package  
    {. . .}  
    ```  
  
     Finden Sie unter den aufgelisteten Felder des <xref:Microsoft.VisualStudio.Shell.Interop.UIContextGuids80> eine Liste der Benutzeroberflächen-Kontexte und ihre GUID-Werte.  
  
-   Legen Sie einen Haltepunkt der <xref:Microsoft.VisualStudio.Shell.Package.Initialize%2A> Methode.  
  
-   Das VSPackage erstellen und mit dem Debuggen beginnen.  
  
-   Laden Sie eine Projektmappe, oder erstellen.  
  
     Das VSPackage lädt und hält am Haltepunkt an.  
  
## <a name="forcing-a-vspackage-to-load"></a>Erzwingen eine VSPackage geladen  
 Unter bestimmten Umständen möglicherweise eine VSPackage Erzwingen von einem anderen VSPackage geladen werden soll. Eine einfache VSPackage möglicherweise z. B. eine größere VSPackage in einem Kontext geladen, die nicht als ein CMDUIContext verfügbar ist.  
  
 Sie können die <xref:Microsoft.VisualStudio.Shell.Interop.IVsShell.LoadPackage%2A> Methode, um ein VSPackage geladen zu erzwingen.  
  
-   Fügen Sie diesen Code in die <xref:Microsoft.VisualStudio.Shell.Package.Initialize%2A> Methode das VSPackage, das einem anderen VSPackage beim Laden erzwingt:  
  
    ```csharp  
    IVsShell shell = GetService(typeof(SVsShell)) as IVsShell;  
    if (shell == null) return;  
  
    IVsPackage package = null;  
    Guid PackageToBeLoadedGuid =   
        new Guid(Microsoft.PackageToBeLoaded.GuidList.guidPackageToBeLoadedPkgString);  
    shell.LoadPackage(ref PackageToBeLoadedGuid, out package);  
  
    ```  
  
     Bei der Initialisierung des VSPackages wird erzwungen `PackageToBeLoaded` geladen.  
  
     Force laden sollte nicht für die VSPackage-Kommunikation verwendet werden. Verwendung [verwenden und Bereitstellen von Diensten](../extensibility/using-and-providing-services.md) stattdessen.
  
## <a name="see-also"></a>Siehe auch  
 [VSPackages](../extensibility/internals/vspackages.md)
