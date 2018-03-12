---
title: SafeControl-Element | Microsoft Docs
ms.custom: 
ms.date: 02/02/2017
ms.reviewer: 
ms.suite: 
ms.technology:
- office-development
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SafeControl element
author: TerryGLee
ms.author: tglee
manager: ghogen
ms.workload:
- office
ms.openlocfilehash: 7458120d7a130de96a1a271c83e5376fe94481f3
ms.sourcegitcommit: f9fbf1f55f9ac14e4e5c6ae58c30dc1800ca6cda
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/10/2018
---
# <a name="safecontrol-element"></a>SafeControl-Element
  Stellt eine ASPX-Steuerelement oder ein Webpart, das als sichere für alle Benutzer Zugriff auf alle ASPX-Seite auf der SharePoint-Website festgelegt ist.  
  
## <a name="syntax"></a>Syntax  
  
```  
<SafeControl Assembly = "Name of assembly that contains the safe control"  
    IsSafe = "true/false"  
    IsSafeAgainstScript = "true/false"  
    Name = "Name of this safe control entry"  
    Namespace = "Namespace of the safe control"  
    TypeName = "Type of the safe control" />  
```  
  
## <a name="attributes-and-elements"></a>Attribute und Elemente  
 In den folgenden Abschnitten werden Attribute sowie untergeordnete und übergeordnete Elemente beschrieben.  
  
### <a name="attributes"></a>Attribute  
  
|Attribut|Beschreibung|  
|---------------|-----------------|  
|**Assembly**|Optionale **xs: String** Attribut.<br /><br /> Der Name der Assembly, in der die ASPX-Steuerelement oder ein Webpart definiert ist. Dieses Attribut verwendet standardmäßig die **$SharePoint.Project.AssemblyFullName$** ersetzbare Parameter für den Assemblynamen. Weitere Informationen finden Sie unter [ersetzbare Parameter](../sharepoint/replaceable-parameters.md).|  
|**IsSafe**|Optionale **xs: Boolean** Attribut.<br /><br /> Gibt an, ob die ASPX-Steuerelements oder -Webpart nicht vertrauenswürdigen Benutzern den Zugriff auf sichere.|  
|**IsSafeAgainstScript**|Optionale **xs: Boolean** Attribut.<br /><br /> Gibt an, ob nicht vertrauenswürdige Benutzer anzeigen oder bearbeiten Sie die Eigenschaften des ASPX-Steuerelements oder des Webparts können.|  
|**Name**|Optionale **xs: String** Attribut.<br /><br /> Der Name dieses Eintrags sicheres Steuerelement in der Auflistung.|  
|**Namespace**|Optionale **xs: String** Attribut.<br /><br /> Der Namespace des ASPX-Steuerelements oder -Webpart.|  
|**Typname**|Optionale **xs: String** Attribut.<br /><br /> Der Typname des ASPX-Steuerelements oder -Webpart.|  
  
### <a name="child-elements"></a>Untergeordnete Elemente  
 Keine  
  
### <a name="parent-elements"></a>Übergeordnete Elemente  
  
|Element|Beschreibung|  
|-------------|-----------------|  
|["SafeControls"](../sharepoint/safecontrols-element.md)|Stellt eine Auflistung von ASPX-Steuerelementen und Webparts, die als sichere für alle Benutzer Zugriff auf alle ASPX-Seite auf der SharePoint-Website festgelegt werden.|  
  
## <a name="remarks"></a>Hinweise  
 Weitere Informationen zu sicheren Steuerelementen finden Sie unter [Bereitstellen von Pack- und Bereitstellungsinformationen in Projektelementen](../sharepoint/providing-packaging-and-deployment-information-in-project-items.md).  
  
## <a name="element-information"></a>Elementinformationen  
  
|||  
|-|-|  
|**Namespace**|http://Schemas.Microsoft.com/VisualStudio/2010/SharePointTools/SharePointProjectItemModel|  
|**Schemaname**|SharePoint-Projektelementschema|  
|**Validierungsdatei**|"ProjectItemModelSchema.xsd" benannt|  
|**Kann leer sein**|Nein|  
  
## <a name="see-also"></a>Siehe auch  
 [SharePoint-Projektelementschema](../sharepoint/sharepoint-project-item-schema-reference.md)   
 [Bereitstellen von Pack- und Bereitstellungsinformationen in Projektelementen](../sharepoint/providing-packaging-and-deployment-information-in-project-items.md)  
  
  