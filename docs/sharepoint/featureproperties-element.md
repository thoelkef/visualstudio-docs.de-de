---
title: "FeatureProperties Element | Microsoft Docs"
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
  - "FeatureProperties element"
ms.assetid: 89233274-a842-4f40-a81a-5548379f6f39
caps.latest.revision: 11
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 7
---
# FeatureProperties Element
  Stellt eine Auflistung von Eigenschaftswerten dar, die beim Bereitstellen für SharePoint in einer Funktion enthalten sind.  Nach dem Bereitstellen einer Funktion können Sie im Code auf die Eigenschaftswerte zugreifen.  
  
## Syntax  
  
```  
<FeatureProperties>  
  <FeatureProperty.../>  
</FeatureProperties>  
```  
  
## Attribute und Elemente  
 In den folgenden Abschnitten werden Attribute sowie untergeordnete und übergeordnete Elemente beschrieben.  
  
### Attribute  
 Keine.  
  
### Untergeordnete Elemente  
  
|Element|Beschreibung|  
|-------------|------------------|  
|[FeatureProperty](../sharepoint/featureproperty-element.md)|Optionales Element.<br /><br /> Stellt eine benutzerdefinierte Eigenschaft im Schlüssel\-Wert\-Format dar.|  
  
### Übergeordnete Elemente  
  
|Element|Beschreibung|  
|-------------|------------------|  
|[ProjectItem](../sharepoint/projectitem-element.md)|Stellt ein SharePoint\-Projektelement dar.  Dies ist das erforderliche Stammelement der SPDATA\-Datei.|  
  
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
  
  