---
title: ExtensionData-Element | Microsoft-Dokumentation
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- ExtensionData element
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 3b700239f97153cef94ab1d7010ad16ed9aa6001
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "85546561"
---
# <a name="extensiondata-element"></a>ExtensionData-Element
  Stellt eine Auflistung benutzerdefinierter Datenelemente dar, die dem SharePoint-Projekt Element zugeordnet sind.

## <a name="syntax"></a>Syntax

```xml
<ExtensionData>
  <ExtensionDataItem.../>
</ExtensionData>
```

## <a name="attributes-and-elements"></a>Attribute und Elemente
 In den folgenden Abschnitten werden Attribute sowie untergeordnete und übergeordnete Elemente beschrieben.

### <a name="attributes"></a>Attribute
 Keine

### <a name="child-elements"></a>Untergeordnete Elemente

|Element|Beschreibung|
|-------------|-----------------|
|[ExtensionDataItem](../sharepoint/extensiondataitem-element.md)|Optionales Element.<br /><br /> Stellt ein benutzerdefiniertes Datenelement dar, das dem SharePoint-Projekt Element im Schlüssel-Wert-Format zugeordnet ist. Sowohl der Schlüssel als auch der Wert müssen Zeichen folgen sein.|

### <a name="parent-elements"></a>Übergeordnete Elemente

|Element|Beschreibung|
|-------------|-----------------|
|[ProjectItem](../sharepoint/projectitem-element.md)|Stellt ein SharePoint-Projekt Element dar. Dieses Element ist das erforderliche Stamm Element der `.spdata` Datei.|

## <a name="remarks"></a>Bemerkungen
 Wenn Sie einem SharePoint-Projekt Element mithilfe der-Eigenschaft eines-Objekts benutzerdefinierte Daten zuordnen <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItem.ExtensionData%2A> <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItem> , speichert Visual Studio die Daten im **ExtensionData** -Element in der- `.spdata` Datei für das Projekt Element. Weitere Informationen finden Sie unter [Speichern von Daten in Erweiterungen des SharePoint-Projekt Systems](../sharepoint/saving-data-in-extensions-of-the-sharepoint-project-system.md).

## <a name="element-information"></a>Elementinformationen

|Eigenschaft|Wert|
|-|-|
|**Namespace**|http: \/ \/ Schemas.Microsoft.com/VisualStudio/<br>2010/sharepointtools/sharepointprojectitemmodel|
|**Schemaname**|SharePoint-Projekt Element Schema|
|**Validierungs Datei**|Projectitemmodelschema. xsd|
|**Kann leer sein**|Nein|

## <a name="see-also"></a>Weitere Informationen
- [Schema Referenz für SharePoint-Projekt Elemente](../sharepoint/sharepoint-project-item-schema-reference.md)
