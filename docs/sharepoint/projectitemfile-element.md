---
title: ProjectItemFile-Element | Microsoft-Dokumentation
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- ProjectItemFile element
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 57c491c79030eea1a01024235c01aec425d5994c
ms.sourcegitcommit: 3d37c2460584f6c61769be70ef29c1a67397cf14
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/21/2019
ms.locfileid: "58322911"
---
# <a name="projectitemfile-element"></a>ProjectItemFile-Element
  Stellt eine SharePoint-Datei, z. B. Feature-Element-Datei, um mit dem Projektelement enthalten, wenn sie in SharePoint bereitgestellt wird.

## <a name="syntax"></a>Syntax

```xml
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
|**Quelle**|Erforderliche **xs: String** Attribut.<br /><br /> Der Name der Datei, die mit dem Projektelement bereitstellen.|
|**Target**|Optionale **xs: String** Attribut.<br /><br /> Der Pfad, in dem die Datei in SharePoint relativ zum Stammordner Bereitstellung bereitgestellt wird. Bereitstellungsstammordner richtet sich nach der Bereitstellungstyp anhand der **Typ** Attribut. Wenn die **Ziel** Attribut nicht angegeben ist, wird die Datei in einem Ordner bereitgestellt werden, mit dem Namen im angegebenen die **Quelle** Attribut.<br /><br /> Weitere Informationen finden Sie in den Beschreibungen der **Bereitstellungspfad** und **Deployment Root** Eigenschaften von SharePoint-Projektelemente in [Entwickeln von SharePoint-Lösungen](../sharepoint/developing-sharepoint-solutions.md).|
|**Type**|Erforderliche **xs: String** Attribut.<br /><br /> Der Typ der Bereitstellung für die Datei. Weitere Informationen zu den möglichen Werten finden Sie in der Beschreibung für die **Bereitstellungstyp** Eigenschaft des SharePoint-Projektelemente in [Entwickeln von SharePoint-Lösungen](../sharepoint/developing-sharepoint-solutions.md).|

### <a name="child-elements"></a>Untergeordnete Elemente
 Keine

### <a name="parent-elements"></a>Übergeordnete Elemente

|Element|Beschreibung|
|-------------|-----------------|
|[Dateien](../sharepoint/files-element.md)|Gibt die Dateien mit SharePoint-Projektelements eingeschlossen werden soll, wenn sie in SharePoint bereitgestellt wird.|

## <a name="remarks"></a>Hinweise
 SharePoint-Dateien, auf die in der Regel verweist **ProjectItemFile** Elemente umfassen featureelementen (*"Elements.xml"*), Schemadateien für Listendefinitionen (*"Schema.xml"*), und die Webpart-Definitionsdateien für die Webparts (*.webpart*).

## <a name="element-information"></a>Elementinformationen

|||
|-|-|
|**Namespace**|http:\/\/schemas.microsoft.com/VisualStudio/<br>2010/SharePointTools/SharePointProjectItemModel|
|**Name des Schemas**|SharePoint-Projektelementschema|
|**Validierungsdatei**|ProjectItemModelSchema.xsd|
|**Kann leer sein.**|Nein|

## <a name="see-also"></a>Siehe auch
- [SharePoint-Projektelementschema](../sharepoint/sharepoint-project-item-schema-reference.md)
