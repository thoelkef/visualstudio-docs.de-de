---
title: SafeControl-Element | Microsoft-Dokumentation
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SafeControl element
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: a56936ed867cdadfb938b9804fbcaeb2560e6d86
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/02/2019
ms.locfileid: "53864137"
---
# <a name="safecontrol-element"></a>SafeControl-Element
  Stellt eine ASPX-Steuerelement oder ein Webpart, das als für alle Benutzer Zugriff auf jede ASPX-Seite auf die SharePoint-Website festgelegt ist.  
  
## <a name="syntax"></a>Syntax  
  
```xml  
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
|**Assembly**|Optionale **xs: String** Attribut.<br /><br /> Der Name der Assembly, in der die ASPX-Steuerelement oder das Webpart definiert ist. Dieses Attribut verwendet standardmäßig die **$SharePoint.Project.AssemblyFullName$** ersetzbare Parameter für den Assemblynamen. Weitere Informationen finden Sie unter [ersetzbare Parameter](../sharepoint/replaceable-parameters.md).|  
|**IsSafe**|Optionale **xs: Boolean** Attribut.<br /><br /> Gibt an, ob die ASPX-Steuerelement oder ein Webpart für nicht vertrauenswürdigen Benutzern den Zugriff auf sicher.|  
|**IsSafeAgainstScript**|Optionale **xs: Boolean** Attribut.<br /><br /> Gibt an, ob nicht vertrauenswürdige Benutzer anzeigen oder bearbeiten Sie die Eigenschaften des ASPX-Steuerelements oder -Webpart können.|  
|**Name**|Optionale **xs: String** Attribut.<br /><br /> Der Name der diesem Eintrag für sicheres Steuerelement in der Auflistung.|  
|**Namespace**|Optionale **xs: String** Attribut.<br /><br /> Der Namespace des ASPX-Steuerelements oder -Webpart.|  
|**Typname**|Optionale **xs: String** Attribut.<br /><br /> Der Typname des ASPX-Steuerelements oder -Webpart.|  
  
### <a name="child-elements"></a>Untergeordnete Elemente
 Keine  
  
### <a name="parent-elements"></a>Übergeordnete Elemente
  
|Element|Beschreibung|  
|-------------|-----------------|  
|[SafeControls](../sharepoint/safecontrols-element.md)|Stellt eine Auflistung von ASPX-Steuerelementen und Webparts, die als sicher für alle Benutzer Zugriff auf jede ASPX-Seite auf die SharePoint-Website festgelegt werden.|  
  
## <a name="remarks"></a>Hinweise  
 Weitere Informationen zu sicheren Steuerelementen finden Sie unter [Angaben zu packen und-Bereitstellen in Projektelementen](../sharepoint/providing-packaging-and-deployment-information-in-project-items.md).  
  
## <a name="element-information"></a>Elementinformationen
  
|||  
|-|-|  
|**Namespace**|HTTP<nolink>: //schemas.microsoft.com/VisualStudio/<br>2010/SharePointTools/SharePointProjectItemModel|  
|**Name des Schemas**|SharePoint-Projektelementschema|  
|**Validierungsdatei**|"ProjectItemModelSchema.xsd" benannt|  
|**Kann leer sein.**|Nein|  
  
## <a name="see-also"></a>Siehe auch
 [SharePoint-Projektelementschema](../sharepoint/sharepoint-project-item-schema-reference.md)   
 [Angaben Sie zu packen und-Bereitstellen in Projektelementen](../sharepoint/providing-packaging-and-deployment-information-in-project-items.md)  
