---
title: '&lt;Anpassungen&gt; -Element (Office-Entwicklung in Visual Studio) | Microsoft Docs'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- <customizations> element
- customizations element
- application manifests [Office development in Visual Studio], <customizations> element
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 7174f4f04914a120454d9977516e7c2443cbadda
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/16/2018
---
# <a name="ltcustomizationsgt-element-office-development-in-visual-studio"></a>&lt;Anpassungen&gt; -Element (Office-Entwicklung in Visual Studio)
  Das `customizations` -Element des `vstov4` -Namespace enthält alle Informationen zum Installieren und Laden der einzelnen Office-Projektmappen.  
  
## <a name="syntax-for-document-level-customizations"></a>Syntax für Anpassungen auf Dokumentebene  
  
```  
<customizations>  
  <customization  
    id  
    <document  
      solutionId  
    />  
  </customization>  
</customizations>  
```  
  
## <a name="syntax-for-vsto-add-ins"></a>Syntax für VSTO-Add-Ins  
  
```  
<customizations>  
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
</customizations>  
```  
  
## <a name="elements-and-attributes"></a>Elemente und Attribute  
 Das `customizations` -Element enthält bestimmte Informationen zu den einzelnen Office-Projektmappen. Dieses Element muss sich im folgenden Namespace befinden: `vstov4=urn:schemas-microsoft-com:vsto.v4`. Untergeordnete Elemente der Assembly müssen sich ebenfalls in diesem Namespace befinden.  
  
 Das `customizations` -Element weist keine Attribute auf.  
  
 Das `customizations` -Element weist die folgenden untergeordneten Elemente auf.  
  
### <a name="customization"></a>Anpassung  
 Erforderlich. Die `customization` Element in der `vstov4` Namespace ist definiert [ &#60;Anpassung&#62; Element &#40;Office-Entwicklung in Visual Studio&#41;](../vsto/customization-element-office-development-in-visual-studio.md).  
  
## <a name="example-of-a-document-level-customization"></a>Beispiel für eine Anpassung auf Dokumentebene  
  
### <a name="description"></a>Beschreibung  
 Im folgenden Codebeispiel wird das `customizations` -Element für eine Anpassung auf Dokumentebene veranschaulicht.  
  
> [!NOTE]  
>  Dieses Codebeispiel ist Teil eines umfangreicheren Beispiels unter [Application Manifests for Office Solutions](../vsto/application-manifests-for-office-solutions.md).  
  
### <a name="code"></a>Code  
  
```  
<vstov4:customizations   
  xmlns:vstov4="urn:schemas-microsoft-com:vsto.v4">  
  <vstov4:customization>  
    <vstov4:document   
      solutionId="73e" />  
  </vstov4:customization>  
</vstov4:customizations>  
```  
  
## <a name="example-of-an-vsto-add-in"></a>Beispiel für ein VSTO-Add-in  
  
### <a name="description"></a>Beschreibung  
 Im folgenden Codebeispiel wird das `customizations` -Element für ein VSTO-Add-In veranschaulicht. Das Add-In ist ein Outlook-VSTO-Add-in, das Formularbereiche enthält. Dieses Codebeispiel ist Teil eines umfangreicheren Beispiels unter [Application Manifests for Office Solutions](../vsto/application-manifests-for-office-solutions.md).  
  
### <a name="code"></a>Code  
  
```  
<vstov4:customizations   
  xmlns:vstov4="urn:schemas-microsoft-com:vsto.v4">  
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
</vstov4:customizations>  
```  
  
## <a name="see-also"></a>Siehe auch  
 [Application Manifests for Office Solutions](../vsto/application-manifests-for-office-solutions.md)   
 [Bereitstellungsmanifeste für Office-Projektmappen](../vsto/deployment-manifests-for-office-solutions.md)   
 [ClickOnce-Anwendungsmanifest](/visualstudio/deployment/clickonce-application-manifest)  
  
  