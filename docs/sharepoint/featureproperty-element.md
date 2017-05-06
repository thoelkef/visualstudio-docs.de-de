---
title: "FeatureProperty Element"
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
  - "FeatureProperty element"
ms.assetid: 36a771a6-98d0-4a40-a278-d76baea82452
caps.latest.revision: 10
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 9
---
# FeatureProperty Element
  Stellt eine benutzerdefinierte Eigenschaft dar, die in eine Funktion eingeschlossen wird, wenn diese für SharePoint bereitgestellt wird.  Nach dem Bereitstellen einer Funktion können Sie im Code auf die Eigenschaft zugreifen.  
  
## Syntax  
  
```  
<FeatureProperty Key = "Key of the property value"  
    Value = "Property value" />  
```  
  
## Attribute und Elemente  
 In den folgenden Abschnitten werden Attribute sowie untergeordnete und übergeordnete Elemente beschrieben.  
  
### Attribute  
  
|Attribut|Beschreibung|  
|--------------|------------------|  
|**Key**|Erforderliches **xs:string**\-Attribut.<br /><br /> Der Schlüssel, der zum Speichern und Abrufen des Eigenschaftswerts verwendet wird.  Jede Eigenschaft muss über einen Schlüssel verfügen, der innerhalb der Funktion eindeutig ist.|  
|**Value**|Erforderliches **xs:string**\-Attribut.<br /><br /> Der Eigenschaftswert.|  
  
### Untergeordnete Elemente  
 Keine.  
  
### Übergeordnete Elemente  
  
|Element|Beschreibung|  
|-------------|------------------|  
|[FeatureProperties](../sharepoint/featureproperties-element.md)|Stellt eine Auflistung von Eigenschaftswerten dar, die beim Bereitstellen für SharePoint in einer Funktion enthalten sind.|  
  
## Hinweise  
 Weitere Informationen zu Funktionseigenschaften finden Sie unter [Bereitstellen von Pack- und Bereitstellungsinformationen in Projektelementen](../sharepoint/providing-packaging-and-deployment-information-in-project-items.md).  
  
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
  
  