---
title: "Laden von VSPackages | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "VSPackages, automatisches Laden"
  - "VSPackages, laden"
ms.assetid: f4c3dcea-5051-4065-898f-601269649d92
caps.latest.revision: 17
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 17
---
# Laden von VSPackages
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

VSPackages sind in Visual Studio nur geladen, wenn ihre Funktionalität erforderlich ist. Beispielsweise wird ein VSPackage geladen, wenn Visual Studio verwendet eine Projekt\-Factory oder einen Dienst, den das VSPackage implementiert. Dieses Feature heißt verzögertes Laden die Möglichkeit zur Verbesserung der Leistung verwendet wird.  
  
> [!NOTE]
>  Visual Studio kann bestimmte VSPackage\-Informationen, z. B. die Befehle ermitteln, die ein VSPackage bietet, ohne dass das VSPackage geladen.  
  
 VSPackages kann z. B. auf Autoload in einem bestimmten Benutzerkontext von Benutzeroberfläche \(UI\) festgelegt werden, wenn eine Projektmappe geöffnet ist. Die <xref:Microsoft.VisualStudio.Shell.ProvideAutoLoadAttribute> Attribut legt dieser Kontext fest.  
  
### Es einem VSPackage in einem bestimmten Kontext  
  
-   Hinzufügen der `ProvideAutoLoad` \-Attribut auf die VSPackage\-Attribute:  
  
    ```c#  
    [DefaultRegistryRoot(@"Software\Microsoft\VisualStudio\14.0")]  
    [PackageRegistration(UseManagedResourcesOnly = true)]  
    [ProvideAutoLoad(UIContextGuids80.SolutionExists)]  
    [Guid("00000000-0000-0000-0000-000000000000")] // your specific package GUID  
    public class MyAutoloadedPackage : Package  
    {. . .}  
    ```  
  
     Die aufgelisteten Felder des <xref:Microsoft.VisualStudio.Shell.Interop.UIContextGuids80> eine Liste der Benutzeroberflächen\-Kontexte und die GUID\-Werte.  
  
-   Legen Sie einen Haltepunkt die <xref:Microsoft.VisualStudio.Shell.Package.Initialize%2A> Methode.  
  
-   Das VSPackage erstellen und Debuggen.  
  
-   Laden Sie eine Projektmappe, oder erstellen.  
  
     Das VSPackage geladen und hält am Haltepunkt.  
  
## Erzwingen ein VSPackage geladen  
 Unter bestimmten Umständen möglicherweise ein VSPackage Erzwingen einer anderen VSPackage geladen werden. Eine einfache VSPackage kann z. B. eine größere VSPackage in einem Kontext laden, die nicht als ein CMDUIContext verfügbar ist.  
  
 Sie können die <xref:Microsoft.VisualStudio.Shell.Interop.IVsShell.LoadPackage%2A> \-Methode zum Erzwingen eines VSPackages geladen.  
  
-   Fügen Sie diesen Code in die <xref:Microsoft.VisualStudio.Shell.Package.Initialize%2A> \-Methode des VSPackages, die erzwingt, eine andere VSPackage dass geladen:  
  
    ```c#  
    IVsShell shell = GetService(typeof(SVsShell)) as IVsShell;  
    if (shell == null) return;  
  
    IVsPackage package = null;  
    Guid PackageToBeLoadedGuid =   
        new Guid(Microsoft.PackageToBeLoaded.GuidList.guidPackageToBeLoadedPkgString);  
    shell.LoadPackage(ref PackageToBeLoadedGuid, out package);  
  
    ```  
  
     Bei der Initialisierung des VSPackages wird sie zwingt `PackageToBeLoaded` geladen.  
  
     Force laden sollte nicht für VSPackage\-Kommunikation verwendet werden. Verwenden Sie stattdessen [Verwendung und Bereitstellung von Diensten](../extensibility/using-and-providing-services.md).  
  
## Verwenden eines benutzerdefinierten Attributs um ein VSPackage zu registrieren.  
 In bestimmten Fällen müssen Sie ein neues Registrierungsattribut für die Erweiterung zu erstellen. Attribute der Registrierung können neue Registrierungsschlüssel hinzufügen oder vorhandene Schlüssel neue Werte hinzu. Das neue Attribut durch Ableiten von <xref:Microsoft.VisualStudio.Shell.RegistrationAttribute>, und es muss überschreiben die <xref:Microsoft.VisualStudio.Shell.RegistrationAttribute.Register%2A> und <xref:Microsoft.VisualStudio.Shell.RegistrationAttribute.Unregister%2A> Methoden.  
  
## Erstellen eines Registrierungsschlüssels  
 Im folgenden Code wird das benutzerdefinierte Attribut erstellt einen **benutzerdefinierte** Unterschlüssel unter dem Schlüssel für das VSPackage, das registriert wird.  
  
```c#  
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
  
## Erstellen einen neuen Wert in einen vorhandenen Registrierungsschlüssel  
 Sie können benutzerdefinierte Werte für einen vorhandenen Schlüssel hinzufügen. Der folgende Code zeigt, wie Sie einen VSPackage\-Registrierungsschlüssel einen neuen Wert hinzufügen.  
  
```c#  
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
  
## Siehe auch  
 [VSPackages](../extensibility/internals/vspackages.md)