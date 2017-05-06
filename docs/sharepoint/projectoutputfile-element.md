---
title: "ProjectOutputFile Element"
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
  - "ProjectOutputFile element"
ms.assetid: 52a017bf-e19c-49e4-bb8f-cbe6958195c2
caps.latest.revision: 13
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 12
---
# ProjectOutputFile Element
  Stellt die Ausgabe eines separaten Projekts dar, die im Projektelement enthalten sein soll, wenn es in SharePoint bereitgestellt wird.  
  
## Syntax  
  
```  
<ProjectOutputFile ProjectId = "GUID of the project"  
    ProjectPath = "Relative path of the project"  
    Target = "Deployment path of the project output"  
    Type = "Type of deployment for the project output" />  
```  
  
## Typ  
 **ProjectOutputFileType**  
  
## Attribute und Elemente  
 In den folgenden Abschnitten werden Attribute sowie untergeordnete und übergeordnete Elemente beschrieben.  
  
### Attribute  
  
|Attribut|Beschreibung|  
|--------------|------------------|  
|**ProjectId**|Erforderliches **xs:string**\-Attribut.<br /><br /> Die GUID des abhängigen Projekts, das die einzuschließende Ausgabe besitzt.  Dieser Wert entspricht dem **ProjectGuid**\-Element in der abhängigen Projektdatei.|  
|**ProjectPath**|Erforderliches **xs:string**\-Attribut.<br /><br /> Der relative Pfad \(einschließlich Projektdateiname\) des abhängigen Projekts, das die einzuschließende Ausgabe besitzt.  Dieser Pfad ist relativ zum Stammordner des SharePoint\-Projekts, das das SharePoint\-Projektelement enthält.|  
|**Target**|Optionales **xs:string**\-Attribut.<br /><br /> Der Pfad, in dem die abhängige Projektausgabe auf dem SharePoint\-Server bereitgestellt werden soll, relativ zum Bereitstellungsstammordner.  Der Bereitstellungsstammordner wird vom Bereitstellungstyp angegeben, der vom **Type**\-Attribut angegeben wird.<br /><br /> Weitere Informationen erhalten Sie in den Beschreibungen zu den **Deployment Path**\- und **Deployment Root**\-Eigenschaften von SharePoint\-Projektelementen in [Developing SharePoint Solutions](../sharepoint/developing-sharepoint-solutions.md).|  
|**Type**|Erforderliches **xs:string**\-Attribut.<br /><br /> Der Typ der Bereitstellung, der für die Ausgabe des abhängigen Projekts verwendet werden soll.  Weitere Informationen zur den möglichen Werten finden Sie in der Beschreibung der **Deployment Type**\-Eigenschaft von SharePoint\-Projektelementen unter [Developing SharePoint Solutions](../sharepoint/developing-sharepoint-solutions.md).|  
  
### Untergeordnete Elemente  
 Keine.  
  
### Übergeordnete Elemente  
  
|Element|Beschreibung|  
|-------------|------------------|  
|[Dateien](../sharepoint/files-element.md)|Gibt die Dateien an, die im Projektelement enthalten sein sollen, wenn es in SharePoint bereitgestellt wird.|  
  
## Hinweise  
 Verwenden Sie das **ProjectOutputFile**\-Element, um die Ausgabe eines Projekts in die Bereitstellung des SharePoint\-Projektelements einzuschließen.  Sie können ein anderes Projekt angeben oder das gleiche Projekt, das das Projektelement enthält.  Weitere Informationen finden Sie unter [Bereitstellen von Pack- und Bereitstellungsinformationen in Projektelementen](../sharepoint/providing-packaging-and-deployment-information-in-project-items.md).  
  
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
 [Developing SharePoint Solutions](../sharepoint/developing-sharepoint-solutions.md)  
  
  