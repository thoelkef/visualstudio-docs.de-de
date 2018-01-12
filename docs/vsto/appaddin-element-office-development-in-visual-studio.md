---
title: '&lt;AppAddin&gt; -Element (Office-Entwicklung in Visual Studio) | Microsoft Docs'
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
helpviewer_keywords: application manifests [Office development in Visual Studio], <appAddin> element
author: TerryGLee
ms.author: tglee
manager: ghogen
ms.workload: office
ms.openlocfilehash: 27f286f9bde8db68a7190796f1d154a402fb208d
ms.sourcegitcommit: f9fbf1f55f9ac14e4e5c6ae58c30dc1800ca6cda
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/10/2018
---
# <a name="ltappaddingt-element-office-development-in-visual-studio"></a>&lt;AppAddin&gt; -Element (Office-Entwicklung in Visual Studio)
  Im `appAddin` -Element des `vstov4` -Namespace werden anpassungsspezifische Informationen für VSTO-Add-Ins gespeichert.  
  
## <a name="syntax"></a>Syntax  
  
```  
<appAddin  
  application  
  loadBehavior  
  keyName>  
  <friendlyName>  
  <description>  
  <formRegions></formRegions>  
</appAddin>  
```  
  
## <a name="elements-and-attributes"></a>Elemente und Attribute  
 Das `appAddin` -Element ist erforderlich und befindet sich im `vstov4` -Namespace. In einem Anwendungsmanifest ist nur ein `appAddin` -Element definiert.  
  
 Das `appAddin` -Element weist folgende Attribute auf:  
  
|Attribut|Beschreibung|  
|---------------|-----------------|  
|`application`|Erforderlich. Identifiziert die Microsoft Office-Anwendung. Einer der folgenden Werte ist möglich: Excel, InfoPath, Outlook, PowerPoint, Project, Visio oder Word.|  
|`loadBehavior`|Dies ist optional. `loadBehavior` wird standardmäßig aktiviert, indem dieser Wert entsprechend festgelegt wird. Zum Debuggen kann das VSTO-Add-In deaktiviert werden, indem der Wert auf 2 festgelegt wird. Weitere Informationen finden Sie in der Tabelle mit dem Namen "LoadBehavior-Werte" in [Registry Entries for VSTO Add-ins](../vsto/registry-entries-for-vsto-add-ins.md).|  
|`keyName`|Erforderlich. Dieser Wert ist der Name des Registrierungsschlüssels, der von der Anwendung zum Laden des VSTO-Add-Ins verwendet wird. Weitere Informationen finden Sie unter [Registry Entries for VSTO Add-ins](../vsto/registry-entries-for-vsto-add-ins.md).|  
  
 Das `appAddin` -Element weist die folgenden untergeordneten Elemente auf:  
  
### <a name="friendlyname"></a>friendlyName  
 Dies ist optional. Die `friendlyName` Element wird erläutert [&#60; FriendlyName &#62; -Element &#40; Office-Entwicklung in Visual Studio &#41; ](../vsto/friendlyname-element-office-development-in-visual-studio.md).  
  
### <a name="description"></a>Beschreibung  
 Dies ist optional. Die `description` Element wird erläutert [&#60; Beschreibung &#62; -Element &#40; Office-Entwicklung in Visual Studio &#41; ](../vsto/description-element-office-development-in-visual-studio.md).  
  
### <a name="formregions"></a>formRegions  
 Nur für Outlook-VSTO-Add-Ins erforderlich, die Formularbereiche enthalten. Die `formRegions` Element wird erläutert [&#60; FormRegions &#62; -Element &#40; Office-Entwicklung in Visual Studio &#41; ](../vsto/formregions-element-office-development-in-visual-studio.md).  
  
## <a name="vsto-add-in-example"></a>Beispiel für ein VSTO-Add-In  
  
### <a name="description"></a>Beschreibung  
 Im folgenden Codebeispiel werden `appAddin` -Elemente in einer Outlook-Projektmappe veranschaulicht, die mit [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)]bereitgestellt wurde. Dieses Codebeispiel ist Teil eines umfangreicheren Beispiels unter [Application Manifests for Office Solutions](../vsto/application-manifests-for-office-solutions.md).  
  
### <a name="code"></a>Code  
  
```  
<vstov4:appAddIn   
  application="Outlook"   
  loadBehavior="3"   
  keyName="ContosoOutlookAddIn">  
  <vstov4:friendlyName>  
    ContosoOutlookAddIn  
  </vstov4:friendlyName>  
  <vstov4:description>  
    ContosoOutlookAddIn - Outlook VSTO Add-in   
    created with Visual Studio Tools for Office  
  </vstov4:description>  
  <vstov4:formRegions>  
    <vstov4:formRegion  
        name="OutlookAddIn1.FormRegion1">  
      <vstov4:messageClass name="IPM.Note" />  
      <vstov4:messageClass name="IPM.Contact" />  
      <vstov4:messageClass name="IPM.Appointment" />  
    </vstov4:formRegion>  
  </vstov4:formRegions>  
</vstov4:appAddIn>  
```  
  
## <a name="see-also"></a>Siehe auch  
 [Application Manifests for Office Solutions](../vsto/application-manifests-for-office-solutions.md)   
 [Bereitstellungsmanifeste für Office-Projektmappen](../vsto/deployment-manifests-for-office-solutions.md)   
 [ClickOnce-Anwendungsmanifest](/visualstudio/deployment/clickonce-application-manifest)  
  
  