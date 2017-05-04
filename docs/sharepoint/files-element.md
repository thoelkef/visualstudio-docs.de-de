---
title: "Files Element | Microsoft Docs"
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
  - "Files element"
ms.assetid: 3c611d5b-28f1-48a7-a068-63e01fa2f3aa
caps.latest.revision: 12
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 11
---
# Files Element
  Gibt die Dateien an, die zusammen mit dem SharePoint\-Projektelement bereitgestellt werden sollen \(beispielsweise Funktionselementdateien und die Ausgabe von abhängigen Nicht\-SharePoint\-Projekten\).  
  
## Syntax  
  
```  
<Files>  
  <ProjectItemFile.../>  
  <ProjectOutputFile.../>  
</Files>  
```  
  
## Typ  
 **FileCollectionType**  
  
## Attribute und Elemente  
 In den folgenden Abschnitten werden Attribute sowie untergeordnete und übergeordnete Elemente beschrieben.  
  
### Attribute  
 Keine.  
  
### Untergeordnete Elemente  
  
|Element|Beschreibung|  
|-------------|------------------|  
|[ProjectItemFile](../sharepoint/projectitemfile-element.md)|Optionales **ProjectItemFileType**\-Element.<br /><br /> Stellt eine SharePoint\-Datei \(beispielsweise eine Feature\-Elementdatei\) dar, die im Projektelement enthalten sein soll, wenn dieses für SharePoint bereitgestellt wird.|  
|[ProjectOutputFile](../sharepoint/projectoutputfile-element.md)|Optionales **ProjectOutputFileType**\-Element.<br /><br /> Stellt die Ausgabe eines Projekts dar, die im Projektelement enthalten sein soll, wenn es in SharePoint bereitgestellt wird.|  
  
### Übergeordnete Elemente  
  
|Element|Beschreibung|  
|-------------|------------------|  
|[ProjectItem](../sharepoint/projectitem-element.md)|Stellt ein SharePoint\-Projektelement dar.  Dies ist das erforderliche Stammelement der SPDATA\-Datei.|  
  
## Elementinformationen  
  
|||  
|-|-|  
|**Namespace**|http:\/\/schemas.microsoft.com\/VisualStudio\/2010\/SharePointTools\/SharePointProjectItemModel|  
|**Schemaname**|SharePoint\-Projektelementschema|  
|**Validierungsdatei**|ProjectItemModelSchema.xsd|  
|**Kann leer sein.**|Nein|  
  
## Siehe auch  
 [SharePoint Project Item Schema Reference](../sharepoint/sharepoint-project-item-schema-reference.md)  
  
  