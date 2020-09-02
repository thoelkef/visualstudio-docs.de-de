---
title: Verwenden eines benutzerdefinierten Registrierungs Attributs zum Registrieren einer Erweiterung | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: devlang-csharp
ms.topic: conceptual
ms.assetid: 98068fa7-bda1-4922-b3f6-28680de58c3d
caps.latest.revision: 3
manager: jillfra
ms.openlocfilehash: a619c5d418df3b9b85ab09cf9b907617ebd81b67
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "62935783"
---
# <a name="using-a-custom-registration-attribute-to-register-an-extension"></a>Verwenden eines benutzerdefinierten Registrierungsattributs zum Registrieren einer Erweiterung
In bestimmten Fällen müssen Sie möglicherweise ein neues Registrierungs Attribut für die Erweiterung erstellen. Mit Registrierungs Attributen können Sie neue Registrierungsschlüssel hinzufügen oder vorhandenen Schlüsseln neue Werte hinzufügen. Das neue Attribut muss von abgeleitet sein <xref:Microsoft.VisualStudio.Shell.RegistrationAttribute> , und es muss die <xref:Microsoft.VisualStudio.Shell.RegistrationAttribute.Register%2A> -Methode und die-Methode überschreiben <xref:Microsoft.VisualStudio.Shell.RegistrationAttribute.Unregister%2A> .  
  
## <a name="creating-a-custom-attribute"></a>Erstellen eines benutzerdefinierten Attributs  
 Der folgende Code zeigt, wie ein neues Registrierungs Attribut erstellt wird.  
  
```  
[AttributeUsage(AttributeTargets.Class, Inherited = true, AllowMultiple = false)]  
    public class CustomRegistrationAttribute : RegistrationAttribute  
    {  
    }  
  
```  
  
 Der <xref:System.AttributeUsageAttribute> wird für Attribut Klassen verwendet, um das Programmelement (Klasse, Methode usw.) anzugeben, auf das sich das Attribut bezieht, ob es mehrmals verwendet werden kann und ob es vererbt werden kann.  
  
### <a name="creating-a-registry-key"></a>Erstellen eines Registrierungsschlüssels  
 Im folgenden Code erstellt das benutzerdefinierte Attribut unter dem Schlüssel für das VSPackage, das registriert wird, einen **benutzerdefinierten** Unterschlüssel.  
  
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
  
### <a name="creating-a-new-value-under-an-existing-registry-key"></a>Erstellen eines neuen Werts unter einem vorhandenen Registrierungsschlüssel  
 Sie können einem vorhandenen Schlüssel benutzerdefinierte Werte hinzufügen. Der folgende Code zeigt, wie Sie einen neuen Wert zu einem VSPackage-Registrierungsschlüssel hinzufügen.  
  
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