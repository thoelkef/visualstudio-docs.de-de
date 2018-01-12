---
title: '&lt;FormRegions&gt; -Element (Office-Entwicklung in Visual Studio) | Microsoft Docs'
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
helpviewer_keywords:
- formRegions element
- <formRegions> element
- application manifests [Office development in Visual Studio], <formRegions> element
author: TerryGLee
ms.author: tglee
manager: ghogen
ms.workload: office
ms.openlocfilehash: eb7008f86dd552eac2b8a6ba9b227884270c8694
ms.sourcegitcommit: f9fbf1f55f9ac14e4e5c6ae58c30dc1800ca6cda
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/10/2018
---
# <a name="ltformregionsgt-element-office-development-in-visual-studio"></a>&lt;FormRegions&gt; -Element (Office-Entwicklung in Visual Studio)
  Das `formRegions` -Element des `vstov4` -Namespace enthält die Microsoft Office Outlook-Formularbereiche, die einem VSTO-Add-In zugeordnet sind  
  
## <a name="syntax"></a>Syntax  
  
```  
<formRegions>  
  <formRegion>  
  </formRegion>  
</formRegions>  
```  
  
## <a name="elements-and-attributes"></a>Elemente und Attribute  
 Das `formRegions` -Element des `vstov4` -Namespace enthält alle `formRegion` -Elemente für ein Outlook-VSTO-Add-In. Es ist nur für Outlook-VSTO-Add-Ins erforderlich, die Formularbereiche beinhalten.  
  
 In einem Anwendungsmanifest kann nur ein `formRegions` -Element definiert sein.  
  
 Das `formRegions` -Element hat keine Attribute.  
  
 Das `formRegions` -Element hat das folgende Element.  
  
### <a name="formregion"></a>formRegion  
 Erforderlich für Outlook-VSTO-Add-Ins, die Formularbereiche beinhalten. Die `formRegion` im-Element definiert [&#60; FormRegion &#62; -Element &#40; Office-Entwicklung in Visual Studio &#41; ](../vsto/formregion-element-office-development-in-visual-studio.md).  
  
## <a name="vsto-add-in-example"></a>Beispiel für ein VSTO-Add-In  
  
### <a name="description"></a>Beschreibung  
 Das folgende Codebeispiel veranschaulicht ein `formRegions` -Element in einem Anwendungsmanifest für eine mit [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)]bereitgestellte Office-Projektmappe auf Anwendungsebene. Dieses Codebeispiel ist Teil eines umfangreicheren Beispiels unter [Application Manifests for Office Solutions](../vsto/application-manifests-for-office-solutions.md).  
  
### <a name="code"></a>Code  
  
```  
<vstov4:formRegions>  
  <vstov4:formRegion  
      name="OutlookAddIn1.FormRegion1">  
    <vstov4:messageClass name="IPM.Note" />  
    <vstov4:messageClass name="IPM.Contact" />  
    <vstov4:messageClass name="IPM.Appointment" />  
  </vstov4:formRegion>  
</vstov4:formRegions>  
```  
  
## <a name="see-also"></a>Siehe auch  
 [Application Manifests for Office Solutions](../vsto/application-manifests-for-office-solutions.md)   
 [Bereitstellungsmanifeste für Office-Projektmappen](../vsto/deployment-manifests-for-office-solutions.md)   
 [ClickOnce-Anwendungsmanifest](/visualstudio/deployment/clickonce-application-manifest)  
  
  