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
ms.openlocfilehash: 151d45159c6c5dda42e138899a027adcc60774c2
ms.sourcegitcommit: d0425b6b7d4b99e17ca6ac0671282bc718f80910
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/21/2019
ms.locfileid: "56619536"
---
# <a name="safecontrols-element"></a>SafeControls-Element
  Eine Auflistung von ASPX-Steuerelementen und Webparts, die für alle Benutzer Zugriff auf jede ASPX-Seite auf die SharePoint-Website als sicher gekennzeichnet sind.

## <a name="syntax"></a>Syntax

```xml
<SafeControls>
  <SafeControl.../>
</SafeControls>
```

## <a name="attributes-and-elements"></a>Attribute und Elemente
 In den folgenden Abschnitten werden Attribute sowie untergeordnete und übergeordnete Elemente beschrieben.

### <a name="attributes"></a>Attribute
 Keine.

### <a name="child-elements"></a>Untergeordnete Elemente

|Element|Beschreibung|
|-------------|-----------------|
|[SafeControl](../sharepoint/safecontrol-element.md)|Optionales Element.<br /><br /> Stellt eine ASPX-Steuerelement oder ein Webpart, das als für alle Benutzer Zugriff auf jede ASPX-Seite auf die SharePoint-Website festgelegt ist.|

### <a name="parent-elements"></a>Übergeordnete Elemente

|Element|Beschreibung|
|-------------|-----------------|
|[ProjectItem](../sharepoint/projectitem-element.md)|Stellt ein SharePoint-Projektelement dar. Dieses Element die Erforderliches Stammelement von der *SPDATA* Datei.|

## <a name="remarks"></a>Hinweise
 Weitere Informationen zu sicheren Steuerelementen finden Sie unter [Angaben zu packen und-Bereitstellen in Projektelementen](../sharepoint/providing-packaging-and-deployment-information-in-project-items.md).

## <a name="element-information"></a>Elementinformationen

|||
|-|-|
|**Namespace**|http<nolink>://schemas.microsoft.com/VisualStudio/<br>2010/SharePointTools/SharePointProjectItemModel|
|**Name des Schemas**|SharePoint-Projektelementschema|
|**Validierungsdatei**|ProjectItemModelSchema.xsd|
|**Kann leer sein.**|Nein|

## <a name="see-also"></a>Siehe auch
- [SharePoint-Projektelementschema](../sharepoint/sharepoint-project-item-schema-reference.md)
- [Angaben Sie zu packen und-Bereitstellen in Projektelementen](../sharepoint/providing-packaging-and-deployment-information-in-project-items.md)
