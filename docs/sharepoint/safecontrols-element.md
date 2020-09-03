---
title: SafeControls-Element | Microsoft-Dokumentation
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SafeControls element
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: e840f0040cf94fea408615525358580d207f07c0
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "85547900"
---
# <a name="safecontrols-element"></a>SafeControls-Element
  Eine Auflistung von ASPX-Steuerelementen und Webparts, die für jeden Benutzer auf einer beliebigen ASPX-Seite auf der SharePoint-Website als sicher eingestuft werden.

## <a name="syntax"></a>Syntax

```xml
<SafeControls>
  <SafeControl.../>
</SafeControls>
```

## <a name="attributes-and-elements"></a>Attribute und Elemente
 In den folgenden Abschnitten werden Attribute sowie untergeordnete und übergeordnete Elemente beschrieben.

### <a name="attributes"></a>Attribute
 Keine

### <a name="child-elements"></a>Untergeordnete Elemente

|Element|BESCHREIBUNG|
|-------------|-----------------|
|[SafeControl](../sharepoint/safecontrol-element.md)|Optionales Element.<br /><br /> Stellt ein aspx-Steuerelement oder Webpart dar, das für jeden Benutzer auf einer beliebigen ASPX-Seite auf der SharePoint-Website als sicher eingestuft wird.|

### <a name="parent-elements"></a>Übergeordnete Elemente

|Element|BESCHREIBUNG|
|-------------|-----------------|
|[ProjectItem](../sharepoint/projectitem-element.md)|Stellt ein SharePoint-Projekt Element dar. Dieses Element ist das erforderliche Stamm Element der *spdata* -Datei.|

## <a name="remarks"></a>Bemerkungen
 Weitere Informationen zu sicheren Steuerelementen finden Sie unter [Bereitstellen von Verpackungs-und Bereitstellungs Informationen in Projekt Elementen](../sharepoint/providing-packaging-and-deployment-information-in-project-items.md).

## <a name="element-information"></a>Elementinformationen

|Eigenschaft|Wert|
|-|-|
|**Namespace**|http: \/ \/ Schemas.Microsoft.com/VisualStudio/<br>2010/sharepointtools/sharepointprojectitemmodel|
|**Schemaname**|SharePoint-Projekt Element Schema|
|**Validierungs Datei**|Projectitemmodelschema. xsd|
|**Kann leer sein**|Nein|

## <a name="see-also"></a>Weitere Informationen
- [Schema Referenz für SharePoint-Projekt Elemente](../sharepoint/sharepoint-project-item-schema-reference.md)
- [Bereitstellen von Verpackungs-und Bereitstellungs Informationen in Projekt Elementen](../sharepoint/providing-packaging-and-deployment-information-in-project-items.md)
