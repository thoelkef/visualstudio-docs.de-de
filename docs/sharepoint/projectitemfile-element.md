---
title: "ProjectItemFile Element"
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
  - "ProjectItemFile element"
ms.assetid: 68d44d31-625a-4f02-b998-463ac0ffb2ef
caps.latest.revision: 10
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 9
---
# ProjectItemFile Element
  Stellt eine SharePoint\-Datei \(beispielsweise eine Feature\-Elementdatei\) dar, die im Projektelement enthalten sein soll, wenn dieses für SharePoint bereitgestellt wird.  
  
## Syntax  
  
```  
<ProjectItemFile Source = "Name of the file"  
    Target = "Deployment path of the file"  
    Type = "Type of deployment for the file" />  
```  
  
## Typ  
 **ProjectItemFileType**  
  
## Attribute und Elemente  
 In den folgenden Abschnitten werden Attribute sowie untergeordnete und übergeordnete Elemente beschrieben.  
  
### Attribute  
  
|Attribut|Beschreibung|  
|--------------|------------------|  
|**Source**|Erforderliches **xs:string**\-Attribut.<br /><br /> Der Name der Datei, die mit dem Projektelement bereitgestellt werden soll.|  
|**Target**|Optionales **xs:string**\-Attribut.<br /><br /> Der Pfad, in dem die Datei unter SharePoint bereitgestellt wird, relativ zum Bereitstellungsstammordner.  Der Bereitstellungsstammordner wird vom Bereitstellungstyp angegeben, der vom **Type**\-Attribut angegeben wird.  Wenn das **Target**\-Attribut nicht angegeben ist, wird die Datei in einem Ordner mit dem im **Source**\-Attribut angegebenen Namen bereitgestellt.<br /><br /> Weitere Informationen erhalten Sie in den Beschreibungen zu den **Deployment Path**\- und **Deployment Root**\-Eigenschaften von SharePoint\-Projektelementen in [Developing SharePoint Solutions](../sharepoint/developing-sharepoint-solutions.md).|  
|**Type**|Erforderliches **xs:string**\-Attribut.<br /><br /> Der Typ der Bereitstellung für die Datei.  Weitere Informationen zur den möglichen Werten finden Sie in der Beschreibung der **Deployment Type**\-Eigenschaft von SharePoint\-Projektelementen unter [Developing SharePoint Solutions](../sharepoint/developing-sharepoint-solutions.md).|  
  
### Untergeordnete Elemente  
 Keine.  
  
### Übergeordnete Elemente  
  
|Element|Beschreibung|  
|-------------|------------------|  
|[Dateien](../sharepoint/files-element.md)|Gibt die Dateien an, die im Projektelement enthalten sein sollen, wenn es in SharePoint bereitgestellt wird.|  
  
## Hinweise  
 SharePoint\-Dateien, auf die normalerweise in **ProjectItemFile**\-Elementen verwiesen wird, enthalten Funktionselementdateien \(Elements.xml\), Schemadateien für Listendefinitionen \(Schema.xml\) und Webpartdefinitionsdateien für Webparts \(.webpart\).  
  
## Elementinformationen  
  
|||  
|-|-|  
|**Namespace**|http:\/\/schemas.microsoft.com\/VisualStudio\/2010\/SharePointTools\/SharePointProjectItemModel|  
|**Schemaname**|SharePoint\-Projektelementschema|  
|**Validierungsdatei**|ProjectItemModelSchema.xsd|  
|**Kann leer sein.**|Nein|  
  
## Siehe auch  
 [SharePoint Project Item Schema Reference](../sharepoint/sharepoint-project-item-schema-reference.md)  
  
  