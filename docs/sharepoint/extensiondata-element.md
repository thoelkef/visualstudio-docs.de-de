---
title: ExtensionData-Element | Microsoft Docs
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
helpviewer_keywords: ExtensionData element
ms.assetid: caf6843b-dcf5-4688-a9eb-a424aae1beab
caps.latest.revision: "11"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 07369e6fb3b083acaeb4f617b0923a088e2a076b
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/31/2017
---
# <a name="extensiondata-element"></a>ExtensionData-Element
  Stellt eine Auflistung benutzerdefinierter Datenelemente, die SharePoint-Projektelements zugeordnet sind.  
  
## <a name="syntax"></a>Syntax  
  
```  
<ExtensionData>  
  <ExtensionDataItem.../>  
</ExtensionData>  
```  
  
## <a name="attributes-and-elements"></a>Attribute und Elemente  
 In den folgenden Abschnitten werden Attribute sowie untergeordnete und übergeordnete Elemente beschrieben.  
  
### <a name="attributes"></a>Attribute  
 Keine.  
  
### <a name="child-elements"></a>Untergeordnete Elemente  
  
|Element|Beschreibung|  
|-------------|-----------------|  
|[ExtensionDataItem](../sharepoint/extensiondataitem-element.md)|Optionales Element.<br /><br /> Stellt ein Element von benutzerdefinierten Daten, die die SharePoint-Projektelement im Schlüssel/Wert-Format zugeordnet ist. Sowohl der Schlüssel und Wert müssen Zeichenfolgen sein.|  
  
### <a name="parent-elements"></a>Übergeordnete Elemente  
  
|Element|Beschreibung|  
|-------------|-----------------|  
|[ProjectItem](../sharepoint/projectitem-element.md)|Stellt ein SharePoint-Projektelement dar. Dies ist das erforderliche Stammelement der SPDATA-Datei.|  
  
## <a name="remarks"></a>Hinweise  
 Wenn Sie benutzerdefinierte Daten mit einem SharePoint-Projektelement mithilfe Zuordnen der <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItem.ExtensionData%2A> Eigenschaft ein <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItem> -Objekt speichert die Daten in Visual Studio die **ExtensionData** -Element in der SPDATA-Datei für das Projektelement. Weitere Informationen finden Sie unter [speichern Daten in Erweiterungen des SharePoint-Projektsystem](../sharepoint/saving-data-in-extensions-of-the-sharepoint-project-system.md).  
  
## <a name="element-information"></a>Elementinformationen  
  
|||  
|-|-|  
|**Namespace**|http://Schemas.Microsoft.com/VisualStudio/2010/SharePointTools/SharePointProjectItemModel|  
|**Schemaname**|SharePoint-Projektelementschema|  
|**Validierungsdatei**|"ProjectItemModelSchema.xsd" benannt|  
|**Kann leer sein**|Nein|  
  
## <a name="see-also"></a>Siehe auch  
 [Referenz zum SharePoint-Projektelementschema](../sharepoint/sharepoint-project-item-schema-reference.md)  
  
  