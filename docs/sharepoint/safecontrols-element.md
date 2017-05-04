---
title: "SafeControls Element | Microsoft Docs"
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
  - "SafeControls element"
ms.assetid: f5ffdbbe-cf85-4e5a-9d39-3cd4462f2a0e
caps.latest.revision: 11
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 10
---
# SafeControls Element
  Stellt eine Auflistung von ASPX\-Steuerelementen oder \-Webparts dar, die als sicher festgelegt sind, um allen Benutzern auf der SharePoint\-Website den Zugriff auf jede ASPX\-Seite zu ermöglichen.  
  
## Syntax  
  
```  
<SafeControls>  
  <SafeControl.../>  
</SafeControls>  
```  
  
## Attribute und Elemente  
 In den folgenden Abschnitten werden Attribute sowie untergeordnete und übergeordnete Elemente beschrieben.  
  
### Attribute  
 Keine.  
  
### Untergeordnete Elemente  
  
|Element|Beschreibung|  
|-------------|------------------|  
|[SafeControl](../sharepoint/safecontrol-element.md)|Optionales Element.<br /><br /> Stellt ein ASPX\-Steuerelement oder \-Webpart dar, das als sicher festgelegt ist, um allen Benutzern auf der SharePoint\-Website den Zugriff auf jede ASPX\-Seite zu ermöglichen.|  
  
### Übergeordnete Elemente  
  
|Element|Beschreibung|  
|-------------|------------------|  
|[ProjectItem](../sharepoint/projectitem-element.md)|Stellt ein SharePoint\-Projektelement dar.  Dies ist das erforderliche Stammelement der SPDATA\-Datei.|  
  
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
  
  