---
title: "&lt;addin&gt;-Element (Office-Entwicklung in Visual Studio) | Microsoft Docs"
ms.custom: ""
ms.date: "02/02/2017"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "office-development"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
helpviewer_keywords: 
  - "Anwendungsmanifeste [Office-Entwicklung in Visual Studio], <addin>-Element"
  - "addin-Element"
  - "<addin>-Element"
ms.assetid: 4abec4c3-8c7c-4b2b-9128-79fa4e863281
caps.latest.revision: 21
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 20
---
# &lt;addin&gt;-Element (Office-Entwicklung in Visual Studio)
  Das `addin`\-Element des `vstav3` \-Namespace enthält spezifische Informationen zu Microsoft Office VSTO\-Add\-Ins und Anpassungen auf Dokumentebene, die mit Visual Studio entwickelt wurden.  
  
## Syntax  
  
```  
<addIn>  
  <entryPointsCollection>  
    <entryPoints>  
      <entryPoint>  
      </entryPoint>  
    </entryPoints>  
  </entryPointsCollection>  
  <update></update>  
  <postActions>  
    <postAction>  
      <postActionData>  
      </postActionData>  
    <postAction>  
  </postActions>  
  <application>  
    <customization>  
    </customization>  
  </application  
</addIn>  
```  
  
## Elemente und Attribute  
 Das `addin`\-Element des `vstav3` \-Namespace enthält Informationen zur Office\-Projektmappe und zur Microsoft Office\-Anwendung. Dieses Element muss sich im folgenden Namespace befinden: `vstav3=urn:schemas-microsoft-com:vsta.v3`. Untergeordnete Elemente müssen sich ebenfalls in diesem Namespace befinden.  
  
 Das `addin`\-Element weist keine Attribute auf.  
  
 Das `addin`\-Element weist die folgenden untergeordneten Elemente auf:  
  
### entryPoints  
 Erforderlich. Das `entryPoints`\-Element wird unter [&#60;entryPoints&#62;-Element &#40;Office-Entwicklung in Visual Studio&#41;](../vsto/entrypoints-element-office-development-in-visual-studio.md) beschrieben.  
  
### aktualisieren  
 Erforderlich. Das `update`\-Element wird unter [&#60;update&#62;-Element &#40;Office-Entwicklung in Visual Studio&#41;](../vsto/update-element-office-development-in-visual-studio.md) beschrieben.  
  
### postActions  
 Optional. Das `postActions`\-Element wird unter [&#60;postActions&#62;-Element &#40;Office-Entwicklung in Visual Studio&#41;](../vsto/postactions-element-office-development-in-visual-studio.md) beschrieben.  
  
### Anwendung  
 Erforderlich. Das `application`\-Element wird unter [&#60;application&#62;-Element &#40;Office-Entwicklung in Visual Studio&#41;](../vsto/application-element-office-development-in-visual-studio.md) beschrieben.  
  
## Beispiel für die Anpassung auf Dokumentebene  
  
### Beschreibung  
 Das folgende Codebeispiel veranschaulicht das `addin`\-Element in einer mit [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)] bereitgestellten Office\-Projektmappe auf Dokumentebene. Dieses Codebeispiel ist Teil eines umfangreicheren Beispiels unter [Anwendungsmanifeste für Office-Projektmappen](../vsto/application-manifests-for-office-solutions.md).  
  
### Code  
  
```  
<vstav3:addIn xmlns:vstav3="urn:schemas-microsoft-com:vsta.v3"> <vstav3:entryPointsCollection> <vstav3:entryPoints> <vstav3:entryPoint class="ContosoExcelWorkbook.ThisWorkbook"> <assemblyIdentity name="ContosoExcelWorkbook" version="1.0.0.0" language="neutral" processorArchitecture="msil" /> </vstav3:entryPoint> <vstav3:entryPoint class="ContosoExcelWorkbook.Sheet1"> <assemblyIdentity name="ContosoExcelWorkbook" version="1.0.0.0" language="neutral" processorArchitecture="msil" /> </vstav3:entryPoint> <vstav3:entryPoint class="ContosoExcelWorkbook.Sheet2"> <assemblyIdentity name="ContosoExcelWorkbook" version="1.0.0.0" language="neutral" processorArchitecture="msil" /> </vstav3:entryPoint> <vstav3:entryPoint class="ContosoExcelWorkbook.Sheet3"> <assemblyIdentity name="ContosoExcelWorkbook" version="1.0.0.0" language="neutral" processorArchitecture="msil" /> </vstav3:entryPoint> </vstav3:entryPoints> </vstav3:entryPointsCollection> <vstav3:update enabled="true"> <vstav3:expiration maximumAge="7" unit="days" /> </vstav3:update> <vstav3:application> <vstov4:customizations xmlns:vstov4="urn:schemas-microsoft-com:vsto.v4"> <vstov4:customization> <vstov4:document solutionId="73e" /> </vstov4:customization> </vstov4:customizations> </vstav3:application> </vstav3:addIn>  
```  
  
## Beispiel für ein VSTO\-Add\-In  
  
### Beschreibung  
 Das folgende Codebeispiel veranschaulicht das `addin`\-Element in einer mit [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)] bereitgestellten Office\-Projektmappe auf Anwendungsebene. Dieses Codebeispiel ist Teil eines umfangreicheren Beispiels unter [Anwendungsmanifeste für Office-Projektmappen](../vsto/application-manifests-for-office-solutions.md).  
  
### Code  
  
```  
<vstav3:addIn xmlns:vstav3="urn:schemas-microsoft-com:vsta.v3"> <vstav3:entryPointsCollection> <vstav3:entryPoints> <vstav3:entryPoint class="ContosoOutlookAddIn.ThisAddIn"> <assemblyIdentity name="ContosoOutlookAddIn" version="1.0.0.0" language="neutral" processorArchitecture="msil" /> </vstav3:entryPoint> </vstav3:entryPoints> </vstav3:entryPointsCollection> <vstav3:update enabled="true"> <vstav3:expiration maximumAge="7" unit="days" /> </vstav3:update> <vstav3:application> <vstov4:customizations xmlns:vstov4="urn:schemas-microsoft-com:vsto.v4"> <vstov4:customization> <vstov4:appAddIn application="Outlook" loadBehavior="3" keyName="ContosoOutlookAddIn"> <vstov4:friendlyName> ContosoOutlookAddIn </vstov4:friendlyName> <vstov4:description> ContosoOutlookAddIn - Outlook VSTO Add-in created with Visual Studio Tools for Office </vstov4:description> <vstov4:formRegions> <vstov4:formRegion name="OutlookAddIn1.FormRegion1"> <vstov4:messageClass name="IPM.Note" /> <vstov4:messageClass name="IPM.Contact" /> <vstov4:messageClass name="IPM.Appointment" /> </vstov4:formRegion> </vstov4:formRegions> </vstov4:appAddIn> </vstov4:customization> </vstov4:customizations> </vstav3:application> </vstav3:addIn>  
```  
  
## Siehe auch  
 [Anwendungsmanifeste für Office-Projektmappen](../vsto/application-manifests-for-office-solutions.md)   
 [Bereitstellungsmanifeste für Office-Projektmappen](../vsto/deployment-manifests-for-office-solutions.md)   
 [ClickOnce Application Manifest](../deployment/clickonce-application-manifest.md)  
  
  