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
ms.openlocfilehash: 192b745580ab676dab476b4dcf31c15b9095be2a
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62967343"
---
# <a name="extensiondata-element"></a>ExtensionData-Element
  Stellt eine Auflistung von benutzerdefinierten Daten-Elementen, die die SharePoint-Projektelement zugeordnet sind.

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
|[ExtensionDataItem](../sharepoint/extensiondataitem-element.md)|Optionales Element.<br /><br /> Stellt ein Element von benutzerdefinierten Daten, die im Schlüssel/Wert-Format der SharePoint-Projektelement zugeordnet ist. Sowohl der Schlüssel und Wert müssen Zeichenfolgen sein.|

### <a name="parent-elements"></a>Übergeordnete Elemente

|Element|Beschreibung|
|-------------|-----------------|
|[ProjectItem](../sharepoint/projectitem-element.md)|Stellt ein SharePoint-Projektelement dar. Dieses Element die Erforderliches Stammelement von der `.spdata` Datei.|

## <a name="remarks"></a>Hinweise
 Wenn Sie benutzerdefinierte Daten mit einem SharePoint-Projektelement mit Zuordnen der <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItem.ExtensionData%2A> Eigenschaft eine <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItem> -Objekt speichert die Daten in Visual Studio die **ExtensionData** Element in der `.spdata` Datei für das Projekt Element. Weitere Informationen finden Sie unter [Speichern von Daten in Erweiterungen des SharePoint-Projektsystem](../sharepoint/saving-data-in-extensions-of-the-sharepoint-project-system.md).

## <a name="element-information"></a>Elementinformationen

|||
|-|-|
|**Namespace**|http:\/\/schemas.microsoft.com/VisualStudio/<br>2010/SharePointTools/SharePointProjectItemModel|
|**Name des Schemas**|SharePoint-Projektelementschema|
|**Validierungsdatei**|ProjectItemModelSchema.xsd|
|**Kann leer sein.**|Nein|

## <a name="see-also"></a>Siehe auch
- [SharePoint-Projektelementschema](../sharepoint/sharepoint-project-item-schema-reference.md)
