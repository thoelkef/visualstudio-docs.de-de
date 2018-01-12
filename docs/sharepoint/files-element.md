---
title: Element-Dateien | Microsoft Docs
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
helpviewer_keywords: Files element
author: TerryGLee
ms.author: tglee
manager: ghogen
ms.workload: office
ms.openlocfilehash: 609bd9e590362efefbabcc79fd910eef3653ff92
ms.sourcegitcommit: f9fbf1f55f9ac14e4e5c6ae58c30dc1800ca6cda
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/10/2018
---
# <a name="files-element"></a>Files-Element
  Gibt die Dateien, die mit der SharePoint-Projektelement, z. B. featuredateien-Element und die Ausgabe der abhängigen nicht-SharePoint-Projekten bereitgestellt.  
  
## <a name="syntax"></a>Syntax  
  
```  
<Files>  
  <ProjectItemFile.../>  
  <ProjectOutputFile.../>  
</Files>  
```  
  
## <a name="type"></a>Typ  
 **FileCollectionType**  
  
## <a name="attributes-and-elements"></a>Attribute und Elemente  
 In den folgenden Abschnitten werden Attribute sowie untergeordnete und übergeordnete Elemente beschrieben.  
  
### <a name="attributes"></a>Attribute  
 Keine  
  
### <a name="child-elements"></a>Untergeordnete Elemente  
  
|Element|Beschreibung|  
|-------------|-----------------|  
|[ProjectItemFile](../sharepoint/projectitemfile-element.md)|Optionale **ProjectItemFileType** Element.<br /><br /> Stellt eine SharePoint-Datei, z. B. Elementdatei Feature, das Projektelement enthalten sein soll, wenn er für SharePoint bereitgestellt wird.|  
|[ProjectOutputFile](../sharepoint/projectoutputfile-element.md)|Optionale **ProjectOutputFileType** Element.<br /><br /> Stellt die Ausgabe eines Projekts mit dem Projektelement eingeschlossen werden soll, wenn er für SharePoint bereitgestellt wird.|  
  
### <a name="parent-elements"></a>Übergeordnete Elemente  
  
|Element|Beschreibung|  
|-------------|-----------------|  
|[ProjectItem](../sharepoint/projectitem-element.md)|Stellt ein SharePoint-Projektelement dar. Dies ist das erforderliche Stammelement der SPDATA-Datei.|  
  
## <a name="element-information"></a>Elementinformationen  
  
|||  
|-|-|  
|**Namespace**|http://Schemas.Microsoft.com/VisualStudio/2010/SharePointTools/SharePointProjectItemModel|  
|**Schemaname**|SharePoint-Projektelementschema|  
|**Validierungsdatei**|"ProjectItemModelSchema.xsd" benannt|  
|**Kann leer sein**|Nein|  
  
## <a name="see-also"></a>Siehe auch  
 [Referenz zum SharePoint-Projektelementschema](../sharepoint/sharepoint-project-item-schema-reference.md)  
  
  