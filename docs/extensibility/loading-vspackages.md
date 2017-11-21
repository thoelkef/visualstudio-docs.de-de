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
ms.openlocfilehash: 94db8d3bb95e254a3fa528a424048162916fce99
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/31/2017
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
  
## <a name="using-a-custom-attribute-to-register-a-vspackage"></a>Verwenden eine VSPackage Registrieren eines benutzerdefinierten Attributs  
 In bestimmten Fällen müssen Sie möglicherweise ein neues Registrierungsattribut für die Erweiterung zu erstellen. Sie können Registrierungsattribute verwenden, um neuen Registrierungsschlüssel hinzuzufügen oder um neue Werte zu vorhandenen Schlüssel hinzuzufügen. Das neue Attribut ableiten muss <xref:Microsoft.VisualStudio.Shell.RegistrationAttribute>, und es muss die <xref:Microsoft.VisualStudio.Shell.RegistrationAttribute.Register%2A> und <xref:Microsoft.VisualStudio.Shell.RegistrationAttribute.Unregister%2A> Methoden.  
  
## <a name="creating-a-registry-key"></a>Erstellen eines Registrierungsschlüssels  
 Im folgenden Code wird das benutzerdefinierte Attribut erstellt eine **benutzerdefinierte** Unterschlüssel unter dem Schlüssel für das VSPackage, der registriert wird.  
  
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
 Sie können benutzerdefinierte Werte für einen vorhandenen Schlüssel hinzufügen. Der folgende Code zeigt, wie ein VSPackage-Registrierungsschlüssel einen neuen Wert hinzu.  
  
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