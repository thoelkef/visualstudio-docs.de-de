---
title: FeatureProperty-Element | Microsoft-Dokumentation
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- FeatureProperty element
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 3dc58683d2cff7e6c25493924b63666c390cdffc
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/02/2019
ms.locfileid: "53991187"
---
# <a name="featureproperty-element"></a>FeatureProperty-Element
  Stellt eine benutzerdefinierte Eigenschaft, die mit einer Funktion enthalten ist, wenn sie in SharePoint bereitgestellt wird. Nachdem eine Funktion bereitgestellt wird, können Sie die Eigenschaft in Ihrem Code zugreifen.  
  
## <a name="syntax"></a>Syntax  
  
```xml  
<FeatureProperty Key = "Key of the property value"  
    Value = "Property value" />  
```  
  
## <a name="attributes-and-elements"></a>Attribute und Elemente
 In den folgenden Abschnitten werden Attribute sowie untergeordnete und übergeordnete Elemente beschrieben.  
  
### <a name="attributes"></a>Attribute  
  
|Attribut|Beschreibung|  
|---------------|-----------------|  
|**Key**|Erforderliche **xs: String** Attribut.<br /><br /> Der Schlüssel, der zum Speichern und Abrufen von den Wert der Eigenschaft verwendet wird. Jede Eigenschaft muss es sich um einen Schlüssel verfügen, der innerhalb der Funktion eindeutig ist.|  
|**Wert**|Erforderliche **xs: String** Attribut.<br /><br /> Der Eigenschaftswert.|  
  
### <a name="child-elements"></a>Untergeordnete Elemente
 Keine  
  
### <a name="parent-elements"></a>Übergeordnete Elemente
  
|Element|Beschreibung|  
|-------------|-----------------|  
|[FeatureProperties](../sharepoint/featureproperties-element.md)|Stellt eine Auflistung von Eigenschaftswerten, die mit einer Funktion enthalten sind, wenn sie in SharePoint bereitgestellt wird.|  
  
## <a name="remarks"></a>Hinweise  
 Weitere Informationen zu Feature-Eigenschaften finden Sie unter [darauf einzugehen Paket und die Bereitstellung in Projektelementen](../sharepoint/providing-packaging-and-deployment-information-in-project-items.md).  
  
## <a name="element-information"></a>Elementinformationen
  
|||  
|-|-|  
|**Namespace**|HTTP<nolink>: //schemas.microsoft.com/VisualStudio/<br>2010/SharePointTools/SharePointProjectItemModel|  
|**Name des Schemas**|SharePoint-Projektelementschema|  
|**Validierungsdatei**|"ProjectItemModelSchema.xsd" benannt|  
|**Kann leer sein.**|Nein|  
  
## <a name="see-also"></a>Siehe auch
 [SharePoint-Projektelementschema](../sharepoint/sharepoint-project-item-schema-reference.md)   
 [Angaben Sie zu packen und-Bereitstellen in Projektelementen](../sharepoint/providing-packaging-and-deployment-information-in-project-items.md)  
