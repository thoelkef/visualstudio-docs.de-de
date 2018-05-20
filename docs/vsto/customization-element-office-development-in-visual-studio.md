---
title: '&lt;Anpassung&gt; -Element (Office-Entwicklung in Visual Studio)'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- application manifests [Office development in Visual Studio], <customization> element
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 02cf84dd225eadd1dcd9c1f20040811e654ebbc0
ms.sourcegitcommit: 209c2c068ff0975994ed892b62aa9b834a7f6077
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/17/2018
---
# <a name="ltcustomizationgt-element-office-development-in-visual-studio"></a>&lt;Anpassung&gt; -Element (Office-Entwicklung in Visual Studio)
  Das `customization` -Element des `vstov4` -Namespace beschreibt eine bestimmte Office-Projektmappe. Die untergeordneten Elemente sind für Anpassungen auf Dokumentebene und für VSTO-Add-Ins unterschiedlich.  
  
## <a name="syntax-for-document-level-customizations"></a>Syntax für Anpassungen auf Dokumentebene  
  
```xml
<customization  
  id  
  <document  
    solutionId  
  />  
</customization>  
```  
  
## <a name="syntax-for-vsto-add-ins"></a>Syntax für VSTO-Add-Ins  
  
```xml
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
 Die `document` Element in der `vstov4` Namespace ist definiert [ &#60;Dokument&#62; Element &#40;Office-Entwicklung in Visual Studio&#41;](../vsto/document-element-office-development-in-visual-studio.md).  
  
### <a name="vsto-add-ins"></a>VSTO-Add-Ins  
 Das `customization` -Element hat das folgende untergeordnete Element:  
  
#### <a name="appaddin"></a>appAddin  
 Die `appAddin` Element in der `vstov4` Namespace ist definiert [ &#60;AppAddin&#62; Element &#40;Office-Entwicklung in Visual Studio&#41;](../vsto/appaddin-element-office-development-in-visual-studio.md).  
  
## <a name="example-of-a-document-level-customization"></a>Beispiel für eine Anpassung auf Dokumentebene  
  
### <a name="description"></a>Beschreibung  
 Im folgenden Codebeispiel wird das `customization` -Element für eine Anpassung auf Dokumentebene veranschaulicht. Dieses Codebeispiel ist Teil eines umfangreicheren Beispiels [Anwendungsmanifeste für Office-Projektmappen](../vsto/application-manifests-for-office-solutions.md).  
  
### <a name="code"></a>Code  
  
```xml
<vstov4:customization>  
  <vstov4:document   
    solutionId="73e" />  
</vstov4:customization>  
```  
  
## <a name="example-of-an-vsto-add-in"></a>Beispiel für ein VSTO-Add-in  
  
### <a name="description"></a>Beschreibung  
 Im folgenden Codebeispiel wird das `customization` -Element für ein VSTO-Add-In veranschaulicht. Das Add-In ist ein Outlook-VSTO-Add-in, das Formularbereiche enthält. Dieses Codebeispiel ist Teil eines umfangreicheren Beispiels [Anwendungsmanifeste für Office-Projektmappen](../vsto/application-manifests-for-office-solutions.md).  
  
### <a name="code"></a>Code  
  
```xml  
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
 [Anwendungsmanifeste für Office-Projektmappen](../vsto/application-manifests-for-office-solutions.md)   
 [Bereitstellungsmanifeste für Office-Projektmappen](../vsto/deployment-manifests-for-office-solutions.md)   
 [ClickOnce-Anwendungsmanifest](/visualstudio/deployment/clickonce-application-manifest)  
  
  