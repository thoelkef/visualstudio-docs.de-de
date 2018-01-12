---
title: FeatureProperty-Element | Microsoft Docs
ms.custom: 
ms.date: 02/02/2017
ms.reviewer: 
ms.suite: 
ms.technology: office-development
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
helpviewer_keywords: FeatureProperty element
author: TerryGLee
ms.author: tglee
manager: ghogen
ms.workload: office
ms.openlocfilehash: 9dcb2cd375a9c725eea6609edbaeda041922a283
ms.sourcegitcommit: f9fbf1f55f9ac14e4e5c6ae58c30dc1800ca6cda
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/10/2018
---
# <a name="featureproperty-element"></a>FeatureProperty-Element
  Stellt eine benutzerdefinierte Eigenschaft, die in eine Funktion eingeschlossen wird, wenn er für SharePoint bereitgestellt wird. Nachdem eine Funktion bereitgestellt wird, können Sie die Eigenschaft im Code zugreifen.  
  
## <a name="syntax"></a>Syntax  
  
```  
<FeatureProperty Key = "Key of the property value"  
    Value = "Property value" />  
```  
  
## <a name="attributes-and-elements"></a>Attribute und Elemente  
 In den folgenden Abschnitten werden Attribute sowie untergeordnete und übergeordnete Elemente beschrieben.  
  
### <a name="attributes"></a>Attribute  
  
|Attribut|Beschreibung|  
|---------------|-----------------|  
|**Key**|Erforderliche **xs: String** Attribut.<br /><br /> Der Schlüssel, der zum Speichern und Abrufen des Werts der Eigenschaft verwendet wird. Jede Eigenschaft muss einen Schlüssel enthalten, der innerhalb der Funktion eindeutig ist.|  
|**Wert**|Erforderliche **xs: String** Attribut.<br /><br /> Der Eigenschaftswert.|  
  
### <a name="child-elements"></a>Untergeordnete Elemente  
 Keine  
  
### <a name="parent-elements"></a>Übergeordnete Elemente  
  
|Element|Beschreibung|  
|-------------|-----------------|  
|[FeatureProperties](../sharepoint/featureproperties-element.md)|Stellt eine Auflistung von Eigenschaftswerten, die in eine Funktion eingeschlossen werden, wenn er für SharePoint bereitgestellt wird.|  
  
## <a name="remarks"></a>Hinweise  
 Weitere Informationen zu Eigenschaften finden Sie unter [Bereitstellen von Pack- und Bereitstellungsinformationen in Projektelementen](../sharepoint/providing-packaging-and-deployment-information-in-project-items.md).  
  
## <a name="element-information"></a>Elementinformationen  
  
|||  
|-|-|  
|**Namespace**|http://Schemas.Microsoft.com/VisualStudio/2010/SharePointTools/SharePointProjectItemModel|  
|**Schemaname**|SharePoint-Projektelementschema|  
|**Validierungsdatei**|"ProjectItemModelSchema.xsd" benannt|  
|**Kann leer sein**|Nein|  
  
## <a name="see-also"></a>Siehe auch  
 [SharePoint-Projektelementschema](../sharepoint/sharepoint-project-item-schema-reference.md)   
 [Bereitstellen von Pack- und Bereitstellungsinformationen in Projektelementen](../sharepoint/providing-packaging-and-deployment-information-in-project-items.md)  
  
  