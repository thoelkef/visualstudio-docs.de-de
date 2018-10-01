---
title: Laden von VSPackages | Microsoft-Dokumentation
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
- VSPackages, autoloading
- VSPackages, loading
ms.assetid: f4c3dcea-5051-4065-898f-601269649d92
caps.latest.revision: 18
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: a6e128b4e8decef7d8dfabc1f2bd8a56ea592e06
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/22/2018
ms.locfileid: "47520863"
---
# <a name="loading-vspackages"></a>Laden von VSPackages
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Die neueste Version dieses Themas finden Sie unter [Laden von VSPackages](https://docs.microsoft.com/visualstudio/extensibility/loading-vspackages).  
  
VSPackages sind in Visual Studio geladen werden, nur, wenn ihre Funktionalität erforderlich ist. Beispielsweise wird eine VSPackage geladen, wenn Visual Studio verwendet eine Projektzuordnungsinstanz oder ein Dienst, den das VSPackage implementiert. Dieses Feature heißt verzögertes Laden, die nach Möglichkeit zur Verbesserung der Leistung verwendet wird.  
  
> [!NOTE]
>  Visual Studio kann bestimmte VSPackage-Informationen, z. B. der Befehle bestimmen, die eine VSPackage bietet, ohne Sie zu das VSPackage zu laden.  
  
 VSPackages kann z. B. Automatisches Laden, in einem bestimmten Benutzerkontext von Benutzeroberfläche (UI) festgelegt werden, wenn eine Projektmappe geöffnet ist. Die <xref:Microsoft.VisualStudio.Shell.ProvideAutoLoadAttribute> -Attribut wird von diesem Kontext.  
  
### <a name="autoloading-a-vspackage-in-a-specific-context"></a>Automatisches Laden eines VSPackage in einem bestimmten Kontext  
  
-   Hinzufügen der `ProvideAutoLoad` -Attribut auf die VSPackage-Attribute:  
  
    ```csharp  
    [DefaultRegistryRoot(@"Software\Microsoft\VisualStudio\14.0")]  
    [PackageRegistration(UseManagedResourcesOnly = true)]  
    [ProvideAutoLoad(UIContextGuids80.SolutionExists)]  
    [Guid("00000000-0000-0000-0000-000000000000")] // your specific package GUID  
    public class MyAutoloadedPackage : Package  
    {. . .}  
    ```  
  
     Finden Sie unter den aufgelisteten Felder <xref:Microsoft.VisualStudio.Shell.Interop.UIContextGuids80> für eine Liste mit den Benutzeroberfläche-Kontexte und die GUID-Werte.  
  
-   Festlegen eines Haltepunkts in der <xref:Microsoft.VisualStudio.Shell.Package.Initialize%2A> Methode.  
  
-   Das VSPackage zu erstellen und mit dem Debuggen beginnen.  
  
-   Laden Sie eine Projektmappe, oder erstellen.  
  
     Das VSPackage lädt, und die Ausführung am Haltepunkt beendet.  
  
## <a name="forcing-a-vspackage-to-load"></a>Erzwingen ein VSPackage geladen  
 Unter bestimmten Umständen möglicherweise eine VSPackage Erzwingen von einem anderen VSPackage geladen werden. Eine einfache VSPackage kann z. B. eine größeren VSPackage in einem Kontext laden, die nicht als eine CMDUIContext verfügbar ist.  
  
 Sie können die <xref:Microsoft.VisualStudio.Shell.Interop.IVsShell.LoadPackage%2A> -Methode zum Erzwingen eines VSPackages zu laden.  
  
-   Fügen Sie diesen Code in die <xref:Microsoft.VisualStudio.Shell.Package.Initialize%2A> -Methode des VSPackages, die erzwingt, einem anderen VSPackage dass zu laden:  
  
    ```csharp  
    IVsShell shell = GetService(typeof(SVsShell)) as IVsShell;  
    if (shell == null) return;  
  
    IVsPackage package = null;  
    Guid PackageToBeLoadedGuid =   
        new Guid(Microsoft.PackageToBeLoaded.GuidList.guidPackageToBeLoadedPkgString);  
    shell.LoadPackage(ref PackageToBeLoadedGuid, out package);  
  
    ```  
  
     Bei der Initialisierung des VSPackages wird gezwungen `PackageToBeLoaded` geladen.  
  
     -Force-Loading sollte nicht für die VSPackage-Kommunikation verwendet werden. Verwendung [verwenden und Bereitstellen von Diensten](../extensibility/using-and-providing-services.md) stattdessen.  
  
## <a name="using-a-custom-attribute-to-register-a-vspackage"></a>Mithilfe eines benutzerdefinierten Attributs, um ein VSPackage zu registrieren.  
 In bestimmten Fällen müssen Sie ein neues Registrierungsattribut für die Erweiterung zu erstellen. Sie können Registrierungsattribute verwenden, um neue Registrierungsschlüssel hinzuzufügen oder um neue Werte zu vorhandenen Schlüssel hinzuzufügen. Das neue Attribut ableiten muss <xref:Microsoft.VisualStudio.Shell.RegistrationAttribute>, und sie überschreiben muss die <xref:Microsoft.VisualStudio.Shell.RegistrationAttribute.Register%2A> und <xref:Microsoft.VisualStudio.Shell.RegistrationAttribute.Unregister%2A> Methoden.  
  
## <a name="creating-a-registry-key"></a>Erstellen eines Registrierungsschlüssels  
 Im folgenden Code wird das benutzerdefinierte Attribut erstellt einen **benutzerdefinierte** Unterschlüssel unter dem Schlüssel für das VSPackage, das registriert wird.  
  
```csharp  
public override void Register(RegistrationAttribute.RegistrationContext context)  
{  
    Key packageKey = null;  
    try  
    {   
        packageKey = context.CreateKey(@"Packages\{" + context.ComponentType.GUID + @"}\Custom");  
        packageKey.SetValue("NewCustom", 1);  
    }  
    finally  
    {  
        if (packageKey != null)  
            packageKey.Close();  
    }  
}  
  
public override void Unregister(RegistrationContext context)  
{  
    context.RemoveKey(@"Packages\" + context.ComponentType.GUID + @"}\Custom");  
}  
  
```  
  
## <a name="creating-a-new-value-under-an-existing-registry-key"></a>Erstellen einen neuen Wert in einen vorhandenen Registrierungsschlüssel  
 Sie können benutzerdefinierte Werte für einen vorhandenen Schlüssel hinzufügen. Der folgende Code zeigt, wie ein VSPackage-Registrierungsschlüssel einen neuen Wert hinzugefügt wird.  
  
```csharp  
public override void Register(RegistrationAttribute.RegistrationContext context)  
{  
    Key packageKey = null;  
    try  
    {   
        packageKey = context.CreateKey(@"Packages\{" + context.ComponentType.GUID + "}");  
        packageKey.SetValue("NewCustom", 1);  
    }  
    finally  
    {  
        if (packageKey != null)  
            packageKey.Close();  
                }  
}  
  
public override void Unregister(RegistrationContext context)  
{  
    context.RemoveValue(@"Packages\" + context.ComponentType.GUID, "NewCustom");  
}  
```  
  
## <a name="see-also"></a>Siehe auch  
 [VSPackages](../extensibility/internals/vspackages.md)

