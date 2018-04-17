---
title: '&lt;FormRegion&gt; -Element (Office-Entwicklung in Visual Studio) | Microsoft Docs'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- application manifests [Office development in Visual Studio], <formRegion> element
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: af7dd4f3472692def9f05a937297d54d13c6f0d6
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/16/2018
---
# <a name="ltformregiongt-element-office-development-in-visual-studio"></a>&lt;FormRegion&gt; -Element (Office-Entwicklung in Visual Studio)
  Das `formRegion` -Element des `vstov4` -Namespace identifiziert einen Microsoft Office Outlook-Formularbereich, der einem VSTO-Add-In zugeordnet ist.  
  
## <a name="syntax"></a>Syntax  
  
```  
<formRegion  
  name>  
  <messageClass  
    name/>  
</formRegion>  
```  
  
## <a name="elements-and-attributes"></a>Elemente und Attribute  
 Das `formRegion` -Element des `vstov4` -Namespace identifiziert einen Formularbereich, der einem VSTO-Add-In für Outlook zugeordnet ist. Es ist nur für Outlook-VSTO-Add-Ins erforderlich, die Formularbereiche einbeziehen.  
  
 Es können mehrere `formRegion` -Elemente in einem `formRegions` -Element für ein einzelnes VSTO-Add-In definiert sein.  
  
 Das `formRegion` -Element hat das folgende Attribut.  
  
|Attribut|Beschreibung|  
|---------------|-----------------|  
|`name`|Erforderlich. Gibt den Namen des Formularbereichs an.|  
  
 Das `formRegion` -Element weist die folgenden untergeordneten Elemente auf.  
  
### <a name="messageclass"></a>messageClass  
 Das `messageClass` -Element identifiziert das Outlook-Formular, das dem Formularbereich zugeordnet ist.  
  
 Das `messageClass` -Element hat das folgende Attribut.  
  
|Attribut|Beschreibung|  
|---------------|-----------------|  
|`name`|Erforderlich. Identifiziert das Formular, das dem Formularbereich zugeordnet ist.|  
  
## <a name="example"></a>Beispiel  
 Das folgende Codebeispiel veranschaulicht ein `formRegion` -Element in einem Anwendungsmanifest für ein mit [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)]bereitgestelltes Outlook-VSTO-Add-In. Es gibt drei Nachrichtenklassen, die diesem einen Formularbereich zugeordnet sind. Dieses Codebeispiel ist Teil eines umfangreicheren Beispiels unter [Application Manifests for Office Solutions](../vsto/application-manifests-for-office-solutions.md).  
  
```  
<vstov4:formRegion  
    name="OutlookAddIn1.FormRegion1">  
  <vstov4:messageClass name="IPM.Note" />  
  <vstov4:messageClass name="IPM.Contact" />  
  <vstov4:messageClass name="IPM.Appointment" />  
</vstov4:formRegion>  
```  
  
## <a name="see-also"></a>Siehe auch  
 [Erstellen von Outlook-Formularbereichen](../vsto/creating-outlook-form-regions.md)   
 [Application Manifests for Office Solutions](../vsto/application-manifests-for-office-solutions.md)   
 [Bereitstellungsmanifeste für Office-Projektmappen](../vsto/deployment-manifests-for-office-solutions.md)   
 [ClickOnce-Anwendungsmanifest](/visualstudio/deployment/clickonce-application-manifest)  
  
  