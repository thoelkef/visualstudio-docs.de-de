---
title: "SafeControl Element | Microsoft Docs"
ms.custom: ""
ms.date: "02/02/2017"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "office-development"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
helpviewer_keywords: 
  - "SafeControl element"
ms.assetid: e7c61749-fc73-412c-be30-4af5ff2a9fd2
caps.latest.revision: 11
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 10
---
# SafeControl Element
  Stellt ein ASPX\-Steuerelement oder \-Webpart dar, das als sicher festgelegt ist, um allen Benutzern auf der SharePoint\-Website den Zugriff auf jede ASPX\-Seite zu ermöglichen.  
  
## Syntax  
  
```  
<SafeControl Assembly = "Name of assembly that contains the safe control"  
    IsSafe = "true/false"  
    IsSafeAgainstScript = "true/false"  
    Name = "Name of this safe control entry"  
    Namespace = "Namespace of the safe control"  
    TypeName = "Type of the safe control" />  
```  
  
## Attribute und Elemente  
 In den folgenden Abschnitten werden Attribute sowie untergeordnete und übergeordnete Elemente beschrieben.  
  
### Attribute  
  
|Attribut|Beschreibung|  
|--------------|------------------|  
|**Assembly**|Optionales **xs:string**\-Attribut.<br /><br /> Der Name der Assembly, in der das ASPX\-Steuerelement oder \-Webpart definiert ist.  Standardmäßig verwendet dieses Attribut den ersetzbaren **$SharePoint.Project.AssemblyFullName$**\-Parameter für den Assemblynamen.  Weitere Informationen finden Sie unter [Ersetzbare Parameter](../sharepoint/replaceable-parameters.md).|  
|**IsSafe**|Optionales **xs:boolean**\-Attribut.<br /><br /> Gibt an, ob das ASPX\-Steuerelement oder das Webpart sicher ist, damit nicht vertrauenswürdige Benutzer zugreifen können.|  
|**IsSafeAgainstScript**|Optionales **xs:boolean**\-Attribut.<br /><br /> Gibt an, ob nicht vertrauenswürdige Benutzer die Eigenschaften des ASPX\-Steuerelements oder des Webparts anzeigen oder bearbeiten können.|  
|**Name**|Optionales **xs:string**\-Attribut.<br /><br /> Der Name dieses sicheren Steuerungseintrags in der Auflistung.|  
|**Namespace**|Optionales **xs:string**\-Attribut.<br /><br /> Der Namespace des ASPX\-Steuerelements oder \-Webparts.|  
|**TypeName**|Optionales **xs:string**\-Attribut.<br /><br /> Der Typname des ASPX\-Steuerelements oder \-Webparts.|  
  
### Untergeordnete Elemente  
 Keine.  
  
### Übergeordnete Elemente  
  
|Element|Beschreibung|  
|-------------|------------------|  
|[SafeControls](../sharepoint/safecontrols-element.md)|Stellt eine Auflistung von ASPX\-Steuerelementen oder \-Webparts dar, die als sicher festgelegt sind, um allen Benutzern auf der SharePoint\-Website den Zugriff auf jede ASPX\-Seite zu ermöglichen.|  
  
## Hinweise  
 Weitere Informationen zu sicheren Steuerelementen finden Sie unter [Bereitstellen von Pack- und Bereitstellungsinformationen in Projektelementen](../sharepoint/providing-packaging-and-deployment-information-in-project-items.md).  
  
## Elementinformationen  
  
|||  
|-|-|  
|**Namespace**|http:\/\/schemas.microsoft.com\/VisualStudio\/2010\/SharePointTools\/SharePointProjectItemModel|  
|**Schemaname**|SharePoint\-Projektelementschema|  
|**Validierungsdatei**|ProjectItemModelSchema.xsd|  
|**Kann leer sein.**|Nein|  
  
## Siehe auch  
 [SharePoint Project Item Schema Reference](../sharepoint/sharepoint-project-item-schema-reference.md)   
 [Bereitstellen von Pack- und Bereitstellungsinformationen in Projektelementen](../sharepoint/providing-packaging-and-deployment-information-in-project-items.md)  
  
  