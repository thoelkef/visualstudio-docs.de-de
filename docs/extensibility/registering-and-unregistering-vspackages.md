---
title: Registrieren und Aufheben der Registrierung von VSPackages | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- registration, VSPackages
- VSPackages, registering
ms.assetid: e25e7a46-6a55-4726-8def-ca316f553d6b
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 14b59a62aba3ffa189ea739061c51a04065882d3
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/25/2019
ms.locfileid: "55016836"
---
# <a name="register-and-unregister-vspackages"></a>An- und Abmelden von VSPackages
Verwenden Sie Attribute, zum Registrieren von einer VSPackages, aber  
  
## <a name="register-a-vspackage"></a>Registriert eine VSPackage  
 Sie können Attribute verwenden, um die Registrierung der verwaltete VSPackages zu steuern. Alle Registrierungsinformationen befindet sich einem *PKGDEF* Datei. Weitere Informationen zu Datei-basierte Registrierungsschlüssel, finden Sie unter [CreatePkgDef-Hilfsprogramm](../extensibility/internals/createpkgdef-utility.md).  
  
 Der folgende Code zeigt, wie Sie die Registrierungsattribute für die standard-verwenden, um Ihr VSPackage zu registrieren.  
  
```csharp  
[PackageRegistration(UseManagedResourcesOnly = true)]  
[Guid("0B81D86C-0A85-4f30-9B26-DD2616447F95")]  
public sealed class BasicPackage : Package  
{
    // ...
}  
```  
  
## <a name="unregister-an-extension"></a>Aufheben der Registrierung einer Erweiterungs  
 Wenn Sie mit einer Vielzahl von anderen VSPackages ausprobiert haben und sie aus der experimentellen Instanz entfernen möchten, können Sie nur Ausführen der **zurücksetzen** Befehl. Suchen Sie nach **Zurücksetzen der experimentellen Visual Studio-Instanz** auf der Startseite des Computers, oder führen Sie diesen Befehl über die Befehlszeile:  
  
```cmd  
<location of Visual Studio 2015 install>\"Microsoft Visual Studio 14.0\VSSDK\VisualStudioIntegration\Tools\Bin\CreateExpInstance.exe" /Reset /VSInstance=14.0 /RootSuffix=Exp  
```  
  
 Wenn Sie möchten eine Erweiterung zu deinstallieren, die Sie für Ihre Entwicklungsinstanz von Visual Studio installiert haben, fahren Sie mit **Tools** > **Erweiterungen und Updates**, suchen Sie nach der Erweiterung, und klicken Sie auf  **Deinstallieren Sie**.  
  
 Wenn aus irgendeinem Grund keine dieser Methoden erfolgreich ist die Erweiterung deinstallieren, können Sie die Registrierung die VSPackage-Assembly, über die Befehlszeile wie folgt aufheben:  
  
```cmd  
<location of Visual Studio 2015 install>\"Microsoft Visual Studio 14.0\VSSDK\VisualStudioIntegration\Tools\Bin\regpkg" /unregister <pathToVSPackage assembly>  
```  
  
<a name="using-a-custom-registration-attribute-to-register-an-extension"></a>  
  
## <a name="use-a-custom-registration-attribute-to-register-an-extension"></a>Verwenden eines benutzerdefinierten registrierungsattributs zum Registrieren einer Erweiterung  
  
In bestimmten Fällen müssen Sie ein neues Registrierungsattribut für die Erweiterung zu erstellen. Sie können Registrierungsattribute verwenden, um neue Registrierungsschlüssel hinzuzufügen oder um neue Werte zu vorhandenen Schlüssel hinzuzufügen. Das neue Attribut ableiten muss <xref:Microsoft.VisualStudio.Shell.RegistrationAttribute>, und sie überschreiben muss die <xref:Microsoft.VisualStudio.Shell.RegistrationAttribute.Register%2A> und <xref:Microsoft.VisualStudio.Shell.RegistrationAttribute.Unregister%2A> Methoden.  
  
### <a name="create-a-custom-attribute"></a>Erstellen eines benutzerdefinierten Attributs  
  
Der folgende Code zeigt, wie Sie ein neues Registrierungsattribut zu erstellen.  
  
```csharp  
[AttributeUsage(AttributeTargets.Class, Inherited = true, AllowMultiple = false)]  
public class CustomRegistrationAttribute : RegistrationAttribute  
{  
}  
```  
  
 Die <xref:System.AttributeUsageAttribute> auf Attributklassen verwendet, um das Programmelement in der das Attribut gehört, gibt an, ob es mehr als einmal verwendet werden kann, und gibt an, ob es geerbt werden kann (Klasse, Methode usw.) anzugeben.  
  
### <a name="create-a-registry-key"></a>Erstellen von Registrierungsschlüsseln  
  
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
  
### <a name="create-a-new-value-under-an-existing-registry-key"></a>Erstellen Sie einen neuen Wert in einen vorhandenen Registrierungsschlüssel  
  
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
