---
title: "ExtensionData Element"
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
  - "ExtensionData element"
ms.assetid: caf6843b-dcf5-4688-a9eb-a424aae1beab
caps.latest.revision: 11
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 10
---
# ExtensionData Element
  Stellt eine Auflistung benutzerdefinierter Datenelemente dar, die dem SharePoint\-Projektelement zugeordnet sind.  
  
## Syntax  
  
```  
<ExtensionData>  
  <ExtensionDataItem.../>  
</ExtensionData>  
```  
  
## Attribute und Elemente  
 In den folgenden Abschnitten werden Attribute sowie untergeordnete und übergeordnete Elemente beschrieben.  
  
### Attribute  
 Keine.  
  
### Untergeordnete Elemente  
  
|Element|Beschreibung|  
|-------------|------------------|  
|[ExtensionDataItem](../sharepoint/extensiondataitem-element.md)|Optionales Element.<br /><br /> Stellt ein benutzerdefiniertes Datenelement \(im Schlüssel\-Wert\-Format\) dar, das dem SharePoint\-Projektelement zugeordnet ist.  Sowohl der Schlüssel als auch der Wert muss eine Zeichenfolge sein.|  
  
### Übergeordnete Elemente  
  
|Element|Beschreibung|  
|-------------|------------------|  
|[ProjectItem](../sharepoint/projectitem-element.md)|Stellt ein SharePoint\-Projektelement dar.  Dies ist das erforderliche Stammelement der SPDATA\-Datei.|  
  
## Hinweise  
 Wenn Sie benutzerdefinierte Daten einem SharePoint\-Projektelement mit der <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItem.ExtensionData%2A>\-Eigenschaft eines <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItem>\-Objekts zuordnen, speichert Visual Studio die Daten in einem neuen **ExtensionData**\-Element in der SPDATA\-Datei für das Projektelement.  Weitere Informationen finden Sie unter [Saving Data in Extensions of the SharePoint Project System](../sharepoint/saving-data-in-extensions-of-the-sharepoint-project-system.md).  
  
## Elementinformationen  
  
|||  
|-|-|  
|**Namespace**|http:\/\/schemas.microsoft.com\/VisualStudio\/2010\/SharePointTools\/SharePointProjectItemModel|  
|**Schemaname**|SharePoint\-Projektelementschema|  
|**Validierungsdatei**|ProjectItemModelSchema.xsd|  
|**Kann leer sein.**|Nein|  
  
## Siehe auch  
 [SharePoint Project Item Schema Reference](../sharepoint/sharepoint-project-item-schema-reference.md)  
  
  