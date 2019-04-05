---
title: Verwenden eines benutzerdefinierten Registrierungsattributs zum Registrieren einer Erweiterungs | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: devlang-csharp
ms.topic: conceptual
ms.assetid: 98068fa7-bda1-4922-b3f6-28680de58c3d
caps.latest.revision: 3
manager: jillfra
ms.openlocfilehash: a619c5d418df3b9b85ab09cf9b907617ebd81b67
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/23/2019
ms.locfileid: "58958064"
---
# <a name="using-a-custom-registration-attribute-to-register-an-extension"></a>Verwenden eines benutzerdefinierten Registrierungsattributs zum Registrieren einer Erweiterung
In bestimmten Fällen müssen Sie ein neues Registrierungsattribut für die Erweiterung zu erstellen. Sie können Registrierungsattribute verwenden, um neue Registrierungsschlüssel hinzuzufügen oder um neue Werte zu vorhandenen Schlüssel hinzuzufügen. Das neue Attribut ableiten muss <xref:Microsoft.VisualStudio.Shell.RegistrationAttribute>, und sie überschreiben muss die <xref:Microsoft.VisualStudio.Shell.RegistrationAttribute.Register%2A> und <xref:Microsoft.VisualStudio.Shell.RegistrationAttribute.Unregister%2A> Methoden.  
  
## <a name="creating-a-custom-attribute"></a>Erstellen eines benutzerdefinierten Attributs  
 Der folgende Code zeigt, wie Sie ein neues Registrierungsattribut zu erstellen.  
  
```  
[AttributeUsage(AttributeTargets.Class, Inherited = true, AllowMultiple = false)]  
    public class CustomRegistrationAttribute : RegistrationAttribute  
    {  
    }  
  
```  
  
 Die <xref:System.AttributeUsageAttribute> auf Attributklassen verwendet, um das Programmelement in der das Attribut gehört, gibt an, ob es mehr als einmal verwendet werden kann, und gibt an, ob es geerbt werden kann (Klasse, Methode usw.) anzugeben.  
  
### <a name="creating-a-registry-key"></a>Erstellen eines Registrierungsschlüssels  
 Im folgenden Code wird das benutzerdefinierte Attribut erstellt einen **benutzerdefinierte** Unterschlüssel unter dem Schlüssel für das VSPackage, das registriert wird.  
  
```  
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
  
### <a name="creating-a-new-value-under-an-existing-registry-key"></a>Erstellen einen neuen Wert in einen vorhandenen Registrierungsschlüssel  
 Sie können benutzerdefinierte Werte für einen vorhandenen Schlüssel hinzufügen. Der folgende Code zeigt, wie ein VSPackage-Registrierungsschlüssel einen neuen Wert hinzugefügt wird.  
  
```  
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