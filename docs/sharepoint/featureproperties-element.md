---
title: FeatureProperties-Element | Microsoft-Dokumentation
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- FeatureProperties element
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: fb345e66a53f9816281df6e948a8961252c0fcea
ms.sourcegitcommit: c0202a77d4dc562cdc55dc2e6223c062281d9749
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/24/2019
ms.locfileid: "54862588"
---
# <a name="featureproperties-element"></a>Element „FeatureProperties“
  Eine Auflistung von Eigenschaftswerten, die mit einer Funktion enthalten sind, wenn sie in SharePoint bereitgestellt wird. Nachdem eine Funktion bereitgestellt wird, können Sie die Eigenschaftswerte in Ihrem Code zugreifen.  
  
## <a name="syntax"></a>Syntax  
  
```xml  
<FeatureProperties>  
  <FeatureProperty.../>  
</FeatureProperties>  
```  
  
## <a name="attributes-and-elements"></a>Attribute und Elemente
 In den folgenden Abschnitten werden Attribute sowie untergeordnete und übergeordnete Elemente beschrieben.  
  
### <a name="attributes"></a>Attribute  
 Keine  
  
### <a name="child-elements"></a>Untergeordnete Elemente
  
|Element|Beschreibung|  
|-------------|-----------------|  
|[FeatureProperty](../sharepoint/featureproperty-element.md)|Optionales Element.<br /><br /> Stellt eine benutzerdefinierte Eigenschaft im Schlüssel/Wert-Format dar.|  
  
### <a name="parent-elements"></a>Übergeordnete Elemente
  
|Element|Beschreibung|  
|-------------|-----------------|  
|[ProjectItem](../sharepoint/projectitem-element.md)|Stellt ein SharePoint-Projektelement dar. Dieses Element die Erforderliches Stammelement von der `.spdata` Datei.|  
  
## <a name="remarks"></a>Hinweise  
 Weitere Informationen zu Feature-Eigenschaften finden Sie unter [Angaben zu packen und-Bereitstellen in Projektelementen](../sharepoint/providing-packaging-and-deployment-information-in-project-items.md).  
  
## <a name="element-information"></a>Elementinformationen
  
|Element|Beschreibung|  
|-------------|-----------------|  
|**Namespace**|http<nolink>://schemas.microsoft.com/VisualStudio/<br>2010/SharePointTools/SharePointProjectItemModel|  
|**Name des Schemas**|SharePoint-Projektelementschema|  
|**Validierungsdatei**|ProjectItemModelSchema.xsd|  
|**Kann leer sein.**|Nein|  
  
## <a name="see-also"></a>Siehe auch
 [SharePoint-Projektelementschema](../sharepoint/sharepoint-project-item-schema-reference.md)   
 [Angaben Sie zu packen und-Bereitstellen in Projektelementen](../sharepoint/providing-packaging-and-deployment-information-in-project-items.md)  
