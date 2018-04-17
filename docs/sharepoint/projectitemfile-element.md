---
title: ProjectItemFile-Element | Microsoft Docs
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- ProjectItemFile element
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: cc9aa921c83bfe26c424e73fd53ad577e1aa527e
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/16/2018
---
# <a name="projectitemfile-element"></a>ProjectItemFile-Element
  Stellt eine SharePoint-Datei, z. B. Elementdatei Feature, das Projektelement enthalten sein soll, wenn er für SharePoint bereitgestellt wird.  
  
## <a name="syntax"></a>Syntax  
  
```  
<ProjectItemFile Source = "Name of the file"  
    Target = "Deployment path of the file"  
    Type = "Type of deployment for the file" />  
```  
  
## <a name="type"></a>Typ  
 **ProjectItemFileType**  
  
## <a name="attributes-and-elements"></a>Attribute und Elemente  
 In den folgenden Abschnitten werden Attribute sowie untergeordnete und übergeordnete Elemente beschrieben.  
  
### <a name="attributes"></a>Attribute  
  
|Attribut|Beschreibung|  
|---------------|-----------------|  
|**Quelle**|Erforderliche **xs: String** Attribut.<br /><br /> Der Name der Datei, die mit dem Projektelement bereitgestellt.|  
|**Target**|Optionale **xs: String** Attribut.<br /><br /> Der Pfad, in dem die Datei in SharePoint, relativ zum Stammordner Bereitstellung bereitgestellt wird. Stammordner der Bereitstellung richtet sich nach den Bereitstellungstyp, der gemäß der **Typ** Attribut. Wenn die **Ziel** Attribut nicht angegeben wird, die Datei wird in einem Ordner bereitgestellt werden, mit dem Namen im angegebenen der **Quelle** Attribut.<br /><br /> Weitere Informationen finden Sie die Beschreibungen für die **Bereitstellungspfad** und **Bereitstellungsstamm-** Eigenschaften von SharePoint-Projektelemente in [Entwickeln von SharePoint-Lösungen](../sharepoint/developing-sharepoint-solutions.md).|  
|**Type**|Erforderliche **xs: String** Attribut.<br /><br /> Der Typ der Bereitstellung für die Datei. Weitere Informationen zu den möglichen Werten finden Sie in der Beschreibung für die **Bereitstellungstyp** Eigenschaft der SharePoint-Projektelemente im [Entwickeln von SharePoint-Lösungen](../sharepoint/developing-sharepoint-solutions.md).|  
  
### <a name="child-elements"></a>Untergeordnete Elemente  
 Keine  
  
### <a name="parent-elements"></a>Übergeordnete Elemente  
  
|Element|Beschreibung|  
|-------------|-----------------|  
|[Dateien](../sharepoint/files-element.md)|Gibt die Dateien mit SharePoint-Projektelements eingeschlossen werden soll, wenn er für SharePoint bereitgestellt wird.|  
  
## <a name="remarks"></a>Hinweise  
 SharePoint-Dateien, auf die in der Regel verweist **ProjectItemFile** Elementen gehören featuredateien-Element ("Elements.xml"), die Schemadateien für Listendefinitionen (Schema.xml) und die Webpart-Definitionsdateien für Webparts (Webpart).  
  
## <a name="element-information"></a>Elementinformationen  
  
|||  
|-|-|  
|**Namespace**|http://schemas.microsoft.com/VisualStudio/2010/SharePointTools/SharePointProjectItemModel|  
|**Schemaname**|SharePoint-Projektelementschema|  
|**Validierungsdatei**|"ProjectItemModelSchema.xsd" benannt|  
|**Kann leer sein**|Nein|  
  
## <a name="see-also"></a>Siehe auch  
 [Referenz zum SharePoint-Projektelementschema](../sharepoint/sharepoint-project-item-schema-reference.md)  
  
  