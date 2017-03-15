---
title: "Verwenden eines benutzerdefinierten Registrierungsattributs zum Registrieren einer Erweiterung | Microsoft Docs"
ms.custom: ""
ms.date: "10/29/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 98068fa7-bda1-4922-b3f6-28680de58c3d
caps.latest.revision: 3
caps.handback.revision: 3
manager: "douge"
---
# Verwenden eines benutzerdefinierten Registrierungsattributs zum Registrieren einer Erweiterung
In bestimmten Fällen müssen Sie möglicherweise ein Attribut Neuzulassungs für die Erweiterung erstellen.  Sie können Attribute Registrierung verwenden, um neue Registrierungsschlüssel hinzuzufügen oder neuen Werte vorhandenen Schlüssel hinzugefügt werden sollen.  Das neue Attribut muss von <xref:Microsoft.VisualStudio.Shell.RegistrationAttribute>abgeleitet werden, und es muss das <xref:Microsoft.VisualStudio.Shell.RegistrationAttribute.Register%2A> und die <xref:Microsoft.VisualStudio.Shell.RegistrationAttribute.Unregister%2A>\-Methode überschreiben.  
  
## Ein benutzerdefiniertes Attribut erstellen  
 Der folgende Code zeigt, wie Neuzulassungs ein Attribut erstellt.  
  
```  
[AttributeUsage(AttributeTargets.Class, Inherited = true, AllowMultiple = false)]  
    public class CustomRegistrationAttribute : RegistrationAttribute  
    {  
    }  
  
```  
  
 <xref:System.AttributeUsageAttribute> wird für Attributklassen verwendet, um das Programmelement \(Klasse, Methode usw.\) anzugeben, dass das Attribut betrifft, ob sie mehrmals verwendet werden kann und ob sie geerbt werden kann.  
  
### Erstellen eines Registrierungsschlüssels  
 Im folgenden Code wird das benutzerdefinierte Attribut einen benutzerdefinierten Unterschlüssel unter dem Schlüssel für ein VSPackage, die registriert wird.  
  
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
  
### Erstellen eines neuen Werts mit einem vorhandenen Registrierungsschlüssel erstellen  
 Sie können benutzerdefinierte Werte einer vorhandenen Schlüssel auf Hinzufügen.  Der folgende Code zeigt, wie Sie einen neuen Wert einer VSPackage\-Registrierungs Schlüssels hinzugefügt wird.  
  
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