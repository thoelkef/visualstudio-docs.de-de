---
title: ProjectItemFolder-Element | Microsoft Docs
ms.custom: 
ms.date: 02/02/2017
ms.reviewer: 
ms.suite: 
ms.technology:
- office-development
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- ProjectItemFolder element
author: TerryGLee
ms.author: tglee
manager: ghogen
ms.workload:
- office
ms.openlocfilehash: df3c5b91e5f95d6ec794bff08c2251c5bf5e5307
ms.sourcegitcommit: f9fbf1f55f9ac14e4e5c6ae58c30dc1800ca6cda
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/10/2018
---
# <a name="projectitemfolder-element"></a>ProjectItemFolder-Element
  Stellt einen zugeordneten Ordner dar.  
  
## <a name="syntax"></a>Syntax  
  
```  
<ProjectItemFolder Target = "Path of SharePoint folder the mapped folder corresponds to"  
    Type = "Type of deployment for the mapped folder" />  
```  
  
## <a name="type"></a>Typ  
 **ProjectItemFolderType**  
  
## <a name="attributes-and-elements"></a>Attribute und Elemente  
 In den folgenden Abschnitten werden Attribute sowie untergeordnete und übergeordnete Elemente beschrieben.  
  
### <a name="attributes"></a>Attribute  
  
|Attribut|Beschreibung|  
|---------------|-----------------|  
|**Target**|Erforderliche **xs: String** Attribut.<br /><br /> Der Pfad des Ordners, in der SharePoint-Installation, die der zugeordnete Ordner, relativ zum Stammordner Bereitstellung entspricht. Stammordner der Bereitstellung richtet sich nach den Bereitstellungstyp, der gemäß der **Typ** Attribut.<br /><br /> Weitere Informationen finden Sie die Beschreibungen für die **Bereitstellungspfad** und **Bereitstellungsstamm-** Eigenschaften von SharePoint-Projektelemente in [Entwickeln von SharePoint-Lösungen](../sharepoint/developing-sharepoint-solutions.md).|  
|**Type**|Erforderliche **xs: String** Attribut.<br /><br /> Der Typ der Bereitstellung für den zugeordneten Ordner. Weitere Informationen zu den möglichen Werten finden Sie in der Beschreibung für die **Bereitstellungstyp** Eigenschaft der SharePoint-Projektelemente im [Entwickeln von SharePoint-Lösungen](../sharepoint/developing-sharepoint-solutions.md).|  
  
### <a name="child-elements"></a>Untergeordnete Elemente  
 Keine  
  
### <a name="parent-elements"></a>Übergeordnete Elemente  
  
|Element|Beschreibung|  
|-------------|-----------------|  
|[ProjectItem](../sharepoint/projectitem-element.md)|Stellt ein SharePoint-Projektelement dar. Dies ist das erforderliche Stammelement der SPDATA-Datei.|  
  
## <a name="remarks"></a>Hinweise  
 Weitere Informationen zur Anzeige zugeordneter Ordner finden Sie unter [wie: Hinzufügen und Entfernen von zugeordneten Ordner](../sharepoint/how-to-add-and-remove-mapped-folders.md).  
  
## <a name="element-information"></a>Elementinformationen  
  
|||  
|-|-|  
|**Namespace**|http://Schemas.Microsoft.com/VisualStudio/2010/SharePointTools/SharePointProjectItemModel|  
|**Schemaname**|SharePoint-Projektelementschema|  
|**Validierungsdatei**|"ProjectItemModelSchema.xsd" benannt|  
|**Kann leer sein**|Nein|  
  
## <a name="see-also"></a>Siehe auch  
 [SharePoint-Projektelementschema](../sharepoint/sharepoint-project-item-schema-reference.md)   
 [Vorgehensweise: Hinzufügen und Entfernen zugeordneter Ordner](../sharepoint/how-to-add-and-remove-mapped-folders.md)  
  
  