---
title: VSPackages werden geladen | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- VSPackages, autoloading
- VSPackages, loading
ms.assetid: f4c3dcea-5051-4065-898f-601269649d92
caps.latest.revision: 18
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: e20caff476e116ad59430692719bdbbe22c4914c
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "90841012"
---
# <a name="loading-vspackages"></a>Laden von VSPackages
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

VSPackages werden nur dann in Visual Studio geladen, wenn ihre Funktionalität erforderlich ist. Beispielsweise wird ein VSPackage geladen, wenn Visual Studio eine projektfactory oder einen Dienst verwendet, den das VSPackage implementiert. Diese Funktion wird als verzögertes Laden bezeichnet und wird nach Möglichkeit verwendet, um die Leistung zu verbessern.  
  
> [!NOTE]
> Visual Studio kann bestimmte VSPackage-Informationen wie die von einem VSPackage angebotenen Befehle ermitteln, ohne das VSPackage zu laden.  
  
 VSPackages können in einem bestimmten Benutzeroberflächen Kontext auf "AutoLoad" festgelegt werden, z. b. Wenn eine Projekt Mappe geöffnet ist. Das- <xref:Microsoft.VisualStudio.Shell.ProvideAutoLoadAttribute> Attribut legt diesen Kontext fest.  
  
### <a name="autoloading-a-vspackage-in-a-specific-context"></a>Autoloading eines VSPackage in einem bestimmten Kontext  
  
- Fügen Sie dem `ProvideAutoLoad` VSPackage-Attribut das-Attribut hinzu:  
  
    ```csharp  
    [DefaultRegistryRoot(@"Software\Microsoft\VisualStudio\14.0")]  
    [PackageRegistration(UseManagedResourcesOnly = true)]  
    [ProvideAutoLoad(UIContextGuids80.SolutionExists)]  
    [Guid("00000000-0000-0000-0000-000000000000")] // your specific package GUID  
    public class MyAutoloadedPackage : Package  
    {. . .}  
    ```  
  
     <xref:Microsoft.VisualStudio.Shell.Interop.UIContextGuids80>Eine Liste der Benutzeroberflächen Kontexte und ihrer GUID-Werte finden Sie in den aufgelisteten Feldern von.  
  
- Legen Sie einen Haltepunkt in der- <xref:Microsoft.VisualStudio.Shell.Package.Initialize%2A> Methode fest.  
  
- Erstellen Sie das VSPackage, und starten Sie das Debugging.  
  
- Laden Sie eine Projekt Mappe, oder erstellen Sie eine.  
  
     Das VSPackage wird am Haltepunkt geladen und angehalten.  
  
## <a name="forcing-a-vspackage-to-load"></a>Erzwingen, dass ein VSPackage geladen wird  
 Unter bestimmten Umständen kann ein VSPackage erzwingen, dass ein anderes VSPackage geladen wird. Beispielsweise kann ein VSPackage mit einfachem VSPackage in einem Kontext, der nicht als cmduicontext verfügbar ist, ein größeres VSPackage laden.  
  
 Sie können die- <xref:Microsoft.VisualStudio.Shell.Interop.IVsShell.LoadPackage%2A> Methode verwenden, um das Laden eines VSPackages zu erzwingen.  
  
- Fügen Sie diesen Code in die- <xref:Microsoft.VisualStudio.Shell.Package.Initialize%2A> Methode des VSPackage ein, das ein anderes VSPackage erzwingt, das geladen werden soll:  
  
    ```csharp  
    IVsShell shell = GetService(typeof(SVsShell)) as IVsShell;  
    if (shell == null) return;  
  
    IVsPackage package = null;  
    Guid PackageToBeLoadedGuid =   
        new Guid(Microsoft.PackageToBeLoaded.GuidList.guidPackageToBeLoadedPkgString);  
    shell.LoadPackage(ref PackageToBeLoadedGuid, out package);  
  
    ```  
  
     Wenn das VSPackage initialisiert ist, wird das `PackageToBeLoaded` Laden erzwungen.  
  
     Das Erzwingen von Ladevorgängen sollte nicht für die VSPackage-Kommunikation verwendet werden. Verwenden [Sie stattdessen und die Bereitstellung von Diensten](../extensibility/using-and-providing-services.md) .  
  
## <a name="using-a-custom-attribute-to-register-a-vspackage"></a>Verwenden eines benutzerdefinierten Attributs zum Registrieren eines VSPackages  
 In bestimmten Fällen müssen Sie möglicherweise ein neues Registrierungs Attribut für die Erweiterung erstellen. Mit Registrierungs Attributen können Sie neue Registrierungsschlüssel hinzufügen oder vorhandenen Schlüsseln neue Werte hinzufügen. Das neue Attribut muss von abgeleitet sein <xref:Microsoft.VisualStudio.Shell.RegistrationAttribute> , und es muss die <xref:Microsoft.VisualStudio.Shell.RegistrationAttribute.Register%2A> -Methode und die-Methode überschreiben <xref:Microsoft.VisualStudio.Shell.RegistrationAttribute.Unregister%2A> .  
  
## <a name="creating-a-registry-key"></a>Erstellen eines Registrierungsschlüssels  
 Im folgenden Code erstellt das benutzerdefinierte Attribut unter dem Schlüssel für das VSPackage, das registriert wird, einen **benutzerdefinierten** Unterschlüssel.  
  
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
  
## <a name="creating-a-new-value-under-an-existing-registry-key"></a>Erstellen eines neuen Werts unter einem vorhandenen Registrierungsschlüssel  
 Sie können einem vorhandenen Schlüssel benutzerdefinierte Werte hinzufügen. Der folgende Code zeigt, wie Sie einen neuen Wert zu einem VSPackage-Registrierungsschlüssel hinzufügen.  
  
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
  
## <a name="see-also"></a>Weitere Informationen  
 [VSPackages](../extensibility/internals/vspackages.md)
