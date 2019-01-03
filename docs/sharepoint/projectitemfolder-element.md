---
title: ProjectItemFolder-Element | Microsoft-Dokumentation
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- ProjectItemFolder element
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: fdecca0b987efd22d4ddd9d3555ede2601b8205e
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/02/2019
ms.locfileid: "53855623"
---
# <a name="projectitemfolder-element"></a>ProjectItemFolder-Element
  Stellt einen zugeordneten Ordner an.  
  
## <a name="syntax"></a>Syntax  
  
```xml  
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
|**Target**|Erforderliche **Xs: String** Attribut.<br /><br /> Der Pfad des Ordners, in der SharePoint-Installation, die der zugeordnete Ordner, relativ zum Stammordner Bereitstellung entspricht. Bereitstellungsstammordner richtet sich nach der Bereitstellungstyp anhand der **Typ** Attribut.<br /><br /> Weitere Informationen finden Sie in den Beschreibungen der **Bereitstellungspfad** und **Deployment Root** Eigenschaften von SharePoint-Projektelemente in [Entwickeln von SharePoint-Lösungen](../sharepoint/developing-sharepoint-solutions.md).|  
|**Type**|Erforderliche **xs: String** Attribut.<br /><br /> Der Typ der Bereitstellung für den zugeordneten Ordner. Weitere Informationen zu den möglichen Werten finden Sie in der Beschreibung für die **Bereitstellungstyp** Eigenschaft des SharePoint-Projektelemente in [Entwickeln von SharePoint-Lösungen](../sharepoint/developing-sharepoint-solutions.md).|  
  
### <a name="child-elements"></a>Untergeordnete Elemente
 Keine  
  
### <a name="parent-elements"></a>Übergeordnete Elemente
  
|Element|Beschreibung|  
|-------------|-----------------|  
|[ProjectItem](../sharepoint/projectitem-element.md)|Stellt ein SharePoint-Projektelement dar. Dieses Element ist das erforderliche Stammelement der *SPDATA* Datei.|  
  
## <a name="remarks"></a>Hinweise  
 Weitere Informationen zum zugeordneten Ordnern finden Sie unter [Vorgehensweise: Hinzufügen und entfernen zugeordneter Ordner](../sharepoint/how-to-add-and-remove-mapped-folders.md).  
  
## <a name="element-information"></a>Elementinformationen
  
|||  
|-|-|  
|**Namespace**|HTTP<nolink>: //schemas.microsoft.com/VisualStudio/2010/<br>SharePointTools/SharePointProjectItemModel|  
|**Name des Schemas**|SharePoint-Projektelementschema|  
|**Validierungsdatei**|"ProjectItemModelSchema.xsd" benannt|  
|**Kann leer sein.**|Nein|  
  
## <a name="see-also"></a>Siehe auch
 [SharePoint-Projektelementschema](../sharepoint/sharepoint-project-item-schema-reference.md)   
 [Gewusst wie: Hinzufügen und entfernen zugeordneter Ordner](../sharepoint/how-to-add-and-remove-mapped-folders.md)  
