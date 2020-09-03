---
title: Extensiondataitem-Element | Microsoft-Dokumentation
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- ExtensionDataItem element
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 295ee649cec01e50b237b4fad1798806d460727b
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "85546548"
---
# <a name="extensiondataitem-element"></a>ExtensionDataItem-Element
  Ein benutzerdefiniertes Datenelement, das dem SharePoint-Projekt Element im Schlüssel-Wert-Format zugeordnet ist. Sowohl der Schlüssel als auch der Wert müssen Zeichen folgen sein.

## <a name="syntax"></a>Syntax

```xml
<ExtensionDataItem Key = "Key of the data item"
    Value = "Value of the data item" />
```

## <a name="attributes-and-elements"></a>Attribute und Elemente
 In den folgenden Abschnitten werden Attribute sowie untergeordnete und übergeordnete Elemente beschrieben.

### <a name="attributes"></a>Attribute

|attribute|BESCHREIBUNG|
|---------------|-----------------|
|**Schlüssel**|Erforderliches **xs: String** -Attribut.<br /><br /> Der Schlüssel, der verwendet wird, um das Datenelement zu speichern und abzurufen.|
|**Wert**|Erforderliches **xs: String** -Attribut.<br /><br /> Der Wert des Datenelements.|

### <a name="child-elements"></a>Untergeordnete Elemente
 Keine

### <a name="parent-elements"></a>Übergeordnete Elemente

|Element|BESCHREIBUNG|
|-------------|-----------------|
|[ExtensionData](../sharepoint/extensiondata-element.md)|Stellt eine Auflistung benutzerdefinierter Datenelemente dar, die dem SharePoint-Projekt Element zugeordnet sind.|

## <a name="remarks"></a>Bemerkungen
 Wenn Sie einem SharePoint-Projekt Element mithilfe der-Eigenschaft eines Objekts benutzerdefinierte Daten zuordnen <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItem.ExtensionData%2A> <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItem> , speichert Visual Studio die Daten in einem neuen **extensiondataitem** -Element in der- `.spdata` Datei für das Projekt Element. Weitere Informationen finden Sie unter [Speichern von Daten in Erweiterungen des SharePoint-Projekt Systems](../sharepoint/saving-data-in-extensions-of-the-sharepoint-project-system.md).

## <a name="element-information"></a>Elementinformationen

|Eigenschaft|Wert|
|-|-|
|**Namespace**|http: \/ \/ Schemas.Microsoft.com/VisualStudio/<br>2010/sharepointtools/sharepointprojectitemmodel|
|**Schemaname**|SharePoint-Projekt Element Schema|
|**Validierungs Datei**|Projectitemmodelschema. xsd|
|**Kann leer sein**|Nein|

## <a name="see-also"></a>Weitere Informationen
- [Schema Referenz für SharePoint-Projekt Elemente](../sharepoint/sharepoint-project-item-schema-reference.md)
