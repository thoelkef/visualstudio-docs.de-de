---
title: "ProjectItemFolder Element"
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
  - "ProjectItemFolder element"
ms.assetid: 15b386dd-f523-4425-9fcc-517325681358
caps.latest.revision: 12
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 11
---
# ProjectItemFolder Element
  Stellt einen zugeordneten Ordner dar.  
  
## Syntax  
  
```  
<ProjectItemFolder Target = "Path of SharePoint folder the mapped folder corresponds to"  
    Type = "Type of deployment for the mapped folder" />  
```  
  
## Typ  
 **ProjectItemFolderType**  
  
## Attribute und Elemente  
 In den folgenden Abschnitten werden Attribute sowie untergeordnete und übergeordnete Elemente beschrieben.  
  
### Attribute  
  
|Attribut|Beschreibung|  
|--------------|------------------|  
|**Target**|Erforderliches **xs:string**\-Attribut.<br /><br /> Der Pfad des Ordners in der SharePoint\-Installation, dem der zugeordnete Ordner entspricht, relativ zum Bereitstellungsstammordner.  Der Bereitstellungsstammordner wird vom Bereitstellungstyp angegeben, der vom **Type**\-Attribut angegeben wird.<br /><br /> Weitere Informationen erhalten Sie in den Beschreibungen zu den **Deployment Path**\- und **Deployment Root**\-Eigenschaften von SharePoint\-Projektelementen in [Developing SharePoint Solutions](../sharepoint/developing-sharepoint-solutions.md).|  
|**Type**|Erforderliches **xs:string**\-Attribut.<br /><br /> Der Typ der Bereitstellung für den zugeordneten Ordner.  Weitere Informationen zur den möglichen Werten finden Sie in der Beschreibung der **Deployment Type**\-Eigenschaft von SharePoint\-Projektelementen unter [Developing SharePoint Solutions](../sharepoint/developing-sharepoint-solutions.md).|  
  
### Untergeordnete Elemente  
 Keine.  
  
### Übergeordnete Elemente  
  
|Element|Beschreibung|  
|-------------|------------------|  
|[ProjectItem](../sharepoint/projectitem-element.md)|Stellt ein SharePoint\-Projektelement dar.  Dies ist das erforderliche Stammelement der SPDATA\-Datei.|  
  
## Hinweise  
 Weitere Informationen zu zugewiesenen Ordnern finden Sie unter [Gewusst wie: Hinzufügen und Entfernen zugeordneter Ordner](../sharepoint/how-to-add-and-remove-mapped-folders.md).  
  
## Elementinformationen  
  
|||  
|-|-|  
|**Namespace**|http:\/\/schemas.microsoft.com\/VisualStudio\/2010\/SharePointTools\/SharePointProjectItemModel|  
|**Schemaname**|SharePoint\-Projektelementschema|  
|**Validierungsdatei**|ProjectItemModelSchema.xsd|  
|**Kann leer sein.**|Nein|  
  
## Siehe auch  
 [SharePoint Project Item Schema Reference](../sharepoint/sharepoint-project-item-schema-reference.md)   
 [Gewusst wie: Hinzufügen und Entfernen zugeordneter Ordner](../sharepoint/how-to-add-and-remove-mapped-folders.md)  
  
  