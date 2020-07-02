---
title: Projectitemfolder-Element | Microsoft-Dokumentation
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- ProjectItemFolder element
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 38f8f70cc6480554441809e33c4083735600fbbb
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/30/2020
ms.locfileid: "85539814"
---
# <a name="projectitemfolder-element"></a>ProjectItemFolder-Element
  Stellt einen zugeordneten Ordner dar.

## <a name="syntax"></a>Syntax

```xml
<ProjectItemFolder Target = "Path of SharePoint folder the mapped folder corresponds to"
    Type = "Type of deployment for the mapped folder" />
```

## <a name="type"></a>Typ
 **Projectitemfoldertype**

## <a name="attributes-and-elements"></a>Attribute und Elemente
 In den folgenden Abschnitten werden Attribute sowie untergeordnete und übergeordnete Elemente beschrieben.

### <a name="attributes"></a>Attribute

|Attribut|BESCHREIBUNG|
|---------------|-----------------|
|**Target**|Erforderliches **xs: String** -Attribut.<br /><br /> Der Pfad des Ordners in der SharePoint-Installation, dem der zugeordnete Ordner entspricht, relativ zum Stamm Ordner der Bereitstellung. Der Stamm Ordner der Bereitstellung wird durch den Bereitstellungstyp bestimmt, der durch das **Type** -Attribut angegeben wird.<br /><br /> Weitere Informationen finden Sie in den Beschreibungen für den **Bereitstellungs Pfad** und die **Bereitstellungs** Stamm Eigenschaften von SharePoint-Projekt Elementen in [entwickeln von SharePoint-Lösungen](../sharepoint/developing-sharepoint-solutions.md).|
|**Type**|Erforderliches **xs: String** -Attribut.<br /><br /> Der Bereitstellungstyp für den zugeordneten Ordner. Weitere Informationen zu den möglichen Werten finden Sie in der Beschreibung der Eigenschaft " **Bereitstellungstyp** " von SharePoint-Projekt Elementen in [entwickeln von SharePoint-Lösungen](../sharepoint/developing-sharepoint-solutions.md).|

### <a name="child-elements"></a>Untergeordnete Elemente
 Keine

### <a name="parent-elements"></a>Übergeordnete Elemente

|Element|Beschreibung|
|-------------|-----------------|
|[ProjectItem](../sharepoint/projectitem-element.md)|Stellt ein SharePoint-Projekt Element dar. Dieses Element ist das erforderliche Stamm Element der *spdata* -Datei.|

## <a name="remarks"></a>Hinweise
 Weitere Informationen zu zugeordneten Ordnern finden Sie unter Gewusst [wie: Hinzufügen und entfernen](../sharepoint/how-to-add-and-remove-mapped-folders.md)von zugeordneten Ordnern.

## <a name="element-information"></a>Elementinformationen

|Eigenschaft|Wert|
|-|-|
|**Namespace**|http: \/ \/ Schemas.Microsoft.com/VisualStudio/2010/<br>Sharepointtools/sharepointprojectitemmodel|
|**Schema Name**|SharePoint-Projekt Element Schema|
|**Validierungs Datei**|Projectitemmodelschema. xsd|
|**Kann leer sein**|Nein|

## <a name="see-also"></a>Siehe auch
- [Schema Referenz für SharePoint-Projekt Elemente](../sharepoint/sharepoint-project-item-schema-reference.md)
- [Gewusst wie: Hinzufügen und entfernen zugeordneter Ordner](../sharepoint/how-to-add-and-remove-mapped-folders.md)
