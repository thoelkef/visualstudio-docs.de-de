---
title: "ExtensionDataItem Element | Microsoft Docs"
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
  - "ExtensionDataItem element"
ms.assetid: 6a5fe7eb-b433-42dc-bd50-4882b780e2fb
caps.latest.revision: 10
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 9
---
# ExtensionDataItem Element
  Stellt ein benutzerdefiniertes Datenelement \(im Schlüssel\-Wert\-Format\) dar, das dem SharePoint\-Projektelement zugeordnet ist.  Sowohl der Schlüssel als auch der Wert muss eine Zeichenfolge sein.  
  
## Syntax  
  
```  
<ExtensionDataItem Key = "Key of the data item"  
    Value = "Value of the data item" />  
```  
  
## Attribute und Elemente  
 In den folgenden Abschnitten werden Attribute sowie untergeordnete und übergeordnete Elemente beschrieben.  
  
### Attribute  
  
|Attribut|Beschreibung|  
|--------------|------------------|  
|**Key**|Erforderliches **xs:string**\-Attribut.<br /><br /> Der Schlüssel, der zum Speichern und Abrufen des Datenelements verwendet wird.|  
|**Value**|Erforderliches **xs:string**\-Attribut.<br /><br /> Der Wert des Datenelements.|  
  
### Untergeordnete Elemente  
 Keine.  
  
### Übergeordnete Elemente  
  
|Element|Beschreibung|  
|-------------|------------------|  
|[ExtensionData](../sharepoint/extensiondata-element.md)|Stellt eine Auflistung benutzerdefinierter Datenelemente dar, die dem SharePoint\-Projektelement zugeordnet sind.|  
  
## Hinweise  
 Wenn Sie benutzerdefinierte Daten einem SharePoint\-Projektelement mit der <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItem.ExtensionData%2A>\-Eigenschaft eines <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItem>\-Objekts zuordnen, speichert Visual Studio die Daten in einem neuen **ExtensionDataItem**\-Element in der SPDATA\-Datei für das Projektelement.  Weitere Informationen finden Sie unter [Saving Data in Extensions of the SharePoint Project System](../sharepoint/saving-data-in-extensions-of-the-sharepoint-project-system.md).  
  
## Elementinformationen  
  
|||  
|-|-|  
|**Namespace**|http:\/\/schemas.microsoft.com\/VisualStudio\/2010\/SharePointTools\/SharePointProjectItemModel|  
|**Schemaname**|SharePoint\-Projektelementschema|  
|**Validierungsdatei**|ProjectItemModelSchema.xsd|  
|**Kann leer sein.**|Nein|  
  
## Siehe auch  
 [SharePoint Project Item Schema Reference](../sharepoint/sharepoint-project-item-schema-reference.md)  
  
  