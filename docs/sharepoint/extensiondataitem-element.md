---
title: ExtensionDataItem-Element | Microsoft-Dokumentation
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- ExtensionDataItem element
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: a460f31679ef01fab9dbfb181905475a2cadede5
ms.sourcegitcommit: e6b13898cfbd89449f786c2e8f3e3e7377afcf25
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/22/2018
ms.locfileid: "36325720"
---
# <a name="extensiondataitem-element"></a>ExtensionDataItem-Element
  Eine benutzerdefinierte Daten-Element, das Schlüssel/Wert-Format der SharePoint-Projektelement zugeordnet ist. Sowohl der Schlüssel und Wert müssen Zeichenfolgen sein.  
  
## <a name="syntax"></a>Syntax  
  
```xml  
<ExtensionDataItem Key = "Key of the data item"  
    Value = "Value of the data item" />  
```  
  
## <a name="attributes-and-elements"></a>Attribute und Elemente
 In den folgenden Abschnitten werden Attribute sowie untergeordnete und übergeordnete Elemente beschrieben.  
  
### <a name="attributes"></a>Attribute  
  
|Attribut|Beschreibung|  
|---------------|-----------------|  
|**Key**|Erforderliche **Xs: String** Attribut.<br /><br /> Der Schlüssel, der zum Speichern und Abrufen des Datenelements verwendet wird.|  
|**Wert**|Erforderliche **xs: String** Attribut.<br /><br /> Der Wert des Datenelements.|  
  
### <a name="child-elements"></a>Untergeordnete Elemente
 Keine  
  
### <a name="parent-elements"></a>Übergeordnete Elemente
  
|Element|Beschreibung|  
|-------------|-----------------|  
|[ExtensionData](../sharepoint/extensiondata-element.md)|Stellt eine Auflistung von benutzerdefinierten Daten-Elementen, die die SharePoint-Projektelement zugeordnet sind.|  
  
## <a name="remarks"></a>Hinweise  
 Wenn Sie benutzerdefinierte Daten mit einem SharePoint-Projektelement mit Zuordnen der <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItem.ExtensionData%2A> Eigenschaft eine <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItem> Visual Studio speichert die Daten in ein neues Objekt **ExtensionDataItem** Element in der `.spdata` -Datei für die das Projektelement. Weitere Informationen finden Sie unter [Speichern von Daten in Erweiterungen des SharePoint-Projektsystem](../sharepoint/saving-data-in-extensions-of-the-sharepoint-project-system.md).  
  
## <a name="element-information"></a>Elementinformationen
  
|||  
|-|-|  
|**Namespace**|HTTP<nolink>: //schemas.microsoft.com/VisualStudio/<br>2010/SharePointTools/SharePointProjectItemModel| 
|**Name des Schemas**|SharePoint-Projektelementschema|  
|**Validierungsdatei**|"ProjectItemModelSchema.xsd" benannt|  
|**Kann leer sein.**|Nein|  
  
## <a name="see-also"></a>Siehe auch
 [SharePoint-Projektelementschema](../sharepoint/sharepoint-project-item-schema-reference.md)  
  
  
