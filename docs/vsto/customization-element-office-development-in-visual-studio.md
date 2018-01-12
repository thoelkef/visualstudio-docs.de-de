---
title: '&lt;Anpassung&gt; -Element (Office-Entwicklung in Visual Studio) | Microsoft Docs'
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
helpviewer_keywords: application manifests [Office development in Visual Studio], <customization> element
author: TerryGLee
ms.author: tglee
manager: ghogen
ms.workload: office
ms.openlocfilehash: b8e1c2c21fe5cf3a038066a47f50fe4b813b277e
ms.sourcegitcommit: f9fbf1f55f9ac14e4e5c6ae58c30dc1800ca6cda
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/10/2018
---
# <a name="ltcustomizationgt-element-office-development-in-visual-studio"></a>&lt;Anpassung&gt; -Element (Office-Entwicklung in Visual Studio)
  Das `customization` -Element des `vstov4` -Namespace beschreibt eine bestimmte Office-Projektmappe. Die untergeordneten Elemente sind für Anpassungen auf Dokumentebene und für VSTO-Add-Ins unterschiedlich.  
  
## <a name="syntax-for-document-level-customizations"></a>Syntax für Anpassungen auf Dokumentebene  
  
```  
<customization  
  id  
  <document  
    solutionId  
  />  
</customization>  
```  
  
## <a name="syntax-for-vsto-add-ins"></a>Syntax für VSTO-Add-Ins  
  
```  
<customization  
  id  
  <appAddin  
    application  
    loadBehavior  
    keyName>  
  <friendlyName></friendlyName>  
  <description></description>  
  <formRegions></formRegions>  
</customization>  
```  
  
## <a name="elements-and-attributes"></a>Elemente und Attribute  
 Das `customization` -Element enthält anpassungsspezifische Informationen. Dieses Element muss sich im folgenden Namespace befinden: `vstov4=urn:schemas-microsoft-com:vsto.v4`. Für jede Office-Projektmappe ist ein `customization` -Element vorhanden. Wenn Sie z. B. in einer Bereitstellung mit mehreren Projekten drei Office-Projektmappen bereitstellen, befinden sich im Anwendungsmanifest drei `customization` -Elemente.  
  
 Untergeordnete Elemente der Assembly müssen sich ebenfalls in diesem Namespace befinden.  
  
 Das `customization` -Element hat das folgende Attribut.  
  
|Attribut|Beschreibung|  
|---------------|-----------------|  
|`id`|Ist für eine Bereitstellung mit mehreren Projekten erforderlich. Das `id` -Element kennzeichnet eine Office-Projektmappe eindeutig.|  
  
### <a name="document-level-customizations"></a>Anpassungen auf Dokumentebene  
 Das `customization` -Element hat das folgende untergeordnete Element:  
  
#### <a name="document"></a>Dokument  
 Die `document` Element in der `vstov4` Namespace ist definiert [&#60; Dokument &#62; -Element &#40; Office-Entwicklung in Visual Studio &#41; ](../vsto/document-element-office-development-in-visual-studio.md).  
  
### <a name="vsto-add-ins"></a>VSTO-Add-Ins  
 Das `customization` -Element hat das folgende untergeordnete Element:  
  
#### <a name="appaddin"></a>appAddin  
 Die `appAddin` Element in der `vstov4` Namespace ist definiert [&#60; AppAddin &#62; -Element &#40; Office-Entwicklung in Visual Studio &#41; ](../vsto/appaddin-element-office-development-in-visual-studio.md).  
  
## <a name="example-of-a-document-level-customization"></a>Beispiel für eine Anpassung auf Dokumentebene  
  
### <a name="description"></a>Beschreibung  
 Im folgenden Codebeispiel wird das `customization` -Element für eine Anpassung auf Dokumentebene veranschaulicht. Dieses Codebeispiel ist Teil eines umfangreicheren Beispiels unter [Application Manifests for Office Solutions](../vsto/application-manifests-for-office-solutions.md).  
  
### <a name="code"></a>Code  
  
```  
<vstov4:customization>  
  <vstov4:document   
    solutionId="73e" />  
</vstov4:customization>  
```  
  
## <a name="example-of-an-vsto-add-in"></a>Beispiel für ein VSTO-Add-in  
  
### <a name="description"></a>Beschreibung  
 Im folgenden Codebeispiel wird das `customization` -Element für ein VSTO-Add-In veranschaulicht. Das Add-In ist ein Outlook-VSTO-Add-in, das Formularbereiche enthält. Dieses Codebeispiel ist Teil eines umfangreicheren Beispiels unter [Application Manifests for Office Solutions](../vsto/application-manifests-for-office-solutions.md).  
  
### <a name="code"></a>Code  
  
```  
<vstov4:customization>  
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
</vstov4:customization>  
```  
  
## <a name="see-also"></a>Siehe auch  
 [Application Manifests for Office Solutions](../vsto/application-manifests-for-office-solutions.md)   
 [Bereitstellungsmanifeste für Office-Projektmappen](../vsto/deployment-manifests-for-office-solutions.md)   
 [ClickOnce-Anwendungsmanifest](/visualstudio/deployment/clickonce-application-manifest)  
  
  