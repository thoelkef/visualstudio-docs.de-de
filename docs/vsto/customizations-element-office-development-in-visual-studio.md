---
title: "&lt;customizations&gt;-Element (Office-Entwicklung in Visual Studio) | Microsoft Docs"
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
  - "<customizations>-Element"
  - "customizations-Element"
  - "Anwendungsmanifeste [Office-Entwicklung in Visual Studio], <customizations>-Element"
ms.assetid: fe1133ef-5fdf-4945-a67b-55a66a4e2109
caps.latest.revision: 18
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 17
---
# &lt;customizations&gt;-Element (Office-Entwicklung in Visual Studio)
  Das `customizations`\-Element des `vstov4`\-Namespace enthält alle Informationen zum Installieren und Laden der einzelnen Office\-Projektmappen.  
  
## Syntax für Anpassungen auf Dokumentebene  
  
```  
<customizations> <customization id <document solutionId /> </customization> </customizations>  
```  
  
## Syntax für VSTO\-Add\-Ins  
  
```  
<customizations> <customization id <appAddin application loadBehavior keyName> <friendlyName></friendlyName> <description></description> <formRegions></formRegions> </customization> </customizations>  
```  
  
## Elemente und Attribute  
 Das `customizations`\-Element enthält bestimmte Informationen zu den einzelnen Office\-Projektmappen. Dieses Element muss sich im folgenden Namespace befinden: `vstov4=urn:schemas-microsoft-com:vsto.v4`. Untergeordnete Elemente der Assembly müssen sich ebenfalls in diesem Namespace befinden.  
  
 Das `customizations`\-Element weist keine Attribute auf.  
  
 Das `customizations`\-Element weist die folgenden untergeordneten Elemente auf.  
  
### Anpassung  
 Erforderlich. Das `customization`\-Element im `vstov4`\-Namespace ist im [&#60;customization&#62;-Element &#40;Office-Entwicklung in Visual Studio&#41;](../vsto/customization-element-office-development-in-visual-studio.md) definiert.  
  
## Beispiel für eine Anpassung auf Dokumentebene  
  
### Beschreibung  
 Im folgenden Codebeispiel wird das `customizations`\-Element für eine Anpassung auf Dokumentebene veranschaulicht.  
  
> [!NOTE]  
>  Dieses Codebeispiel ist Teil eines umfangreicheren Beispiels unter [Anwendungsmanifeste für Office-Projektmappen](../vsto/application-manifests-for-office-solutions.md).  
  
### Code  
  
```  
<vstov4:customizations xmlns:vstov4="urn:schemas-microsoft-com:vsto.v4"> <vstov4:customization> <vstov4:document solutionId="73e" /> </vstov4:customization> </vstov4:customizations>  
```  
  
## Beispiel für ein VSTO\-Add\-in  
  
### Beschreibung  
 Im folgenden Codebeispiel wird das `customizations`\-Element für ein VSTO\-Add\-In veranschaulicht. Das Add\-In ist ein Outlook\-VSTO\-Add\-in, das Formularbereiche enthält. Dieses Codebeispiel ist Teil eines umfangreicheren Beispiels unter [Anwendungsmanifeste für Office-Projektmappen](../vsto/application-manifests-for-office-solutions.md).  
  
### Code  
  
```  
<vstov4:customizations xmlns:vstov4="urn:schemas-microsoft-com:vsto.v4"> <vstov4:customization> <vstov4:appAddIn application="Outlook" loadBehavior="3" keyName="ContosoOutlookAddIn"> <vstov4:friendlyName> ContosoOutlookAddIn </vstov4:friendlyName> <vstov4:description> ContosoOutlookAddIn - Outlook VSTO Add-in created with Visual Studio Tools for Office </vstov4:description> <vstov4:formRegions> <vstov4:formRegion name="OutlookAddIn1.FormRegion1"> <vstov4:messageClass name="IPM.Note" /> <vstov4:messageClass name="IPM.Contact" /> <vstov4:messageClass name="IPM.Appointment" /> </vstov4:formRegion> </vstov4:formRegions> </vstov4:appAddIn> </vstov4:customization> </vstov4:customizations>  
```  
  
## Siehe auch  
 [Anwendungsmanifeste für Office-Projektmappen](../vsto/application-manifests-for-office-solutions.md)   
 [Bereitstellungsmanifeste für Office-Projektmappen](../vsto/deployment-manifests-for-office-solutions.md)   
 [ClickOnce Application Manifest](../deployment/clickonce-application-manifest.md)  
  
  