---
title: "&lt;customization&gt;-Element (Office-Entwicklung in Visual Studio)"
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
  - "Anwendungsmanifeste [Office-Entwicklung in Visual Studio], <customization>-Element"
ms.assetid: a3bf7f35-bd98-4530-9226-46489cd37bb1
caps.latest.revision: 23
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 22
---
# &lt;customization&gt;-Element (Office-Entwicklung in Visual Studio)
  Das `customization`\-Element des `vstov4`\-Namespace beschreibt eine bestimmte Office\-Projektmappe. Die untergeordneten Elemente sind für Anpassungen auf Dokumentebene und für VSTO\-Add\-Ins unterschiedlich.  
  
## Syntax für Anpassungen auf Dokumentebene  
  
```  
<customization id <document solutionId /> </customization>  
```  
  
## Syntax für VSTO\-Add\-Ins  
  
```  
<customization id <appAddin application loadBehavior keyName> <friendlyName></friendlyName> <description></description> <formRegions></formRegions> </customization>  
```  
  
## Elemente und Attribute  
 Das `customization`\-Element enthält anpassungsspezifische Informationen. Dieses Element muss sich im folgenden Namespace befinden: `vstov4=urn:schemas-microsoft-com:vsto.v4`. Für jede Office\-Projektmappe ist ein `customization`\-Element vorhanden. Wenn Sie z. B. in einer Bereitstellung mit mehreren Projekten drei Office\-Projektmappen bereitstellen, befinden sich im Anwendungsmanifest drei `customization`\-Elemente.  
  
 Untergeordnete Elemente der Assembly müssen sich ebenfalls in diesem Namespace befinden.  
  
 Das `customization`\-Element hat das folgende Attribut.  
  
|Attribut|Beschreibung|  
|--------------|------------------|  
|`id`|Ist für eine Bereitstellung mit mehreren Projekten erforderlich. Das `id`\-Element kennzeichnet eine Office\-Projektmappe eindeutig.|  
  
### Anpassungen auf Dokumentebene  
 Das `customization`\-Element hat das folgende untergeordnete Element:  
  
#### Dokument  
 Das `document`\-Element im `vstov4`\-Namespace ist im [&#60;document&#62;-Element &#40;Office-Entwicklung in Visual Studio&#41;](../vsto/document-element-office-development-in-visual-studio.md) definiert.  
  
### VSTO\-Add\-Ins  
 Das `customization`\-Element hat das folgende untergeordnete Element:  
  
#### appAddin  
 Das `appAddin`\-Element im `vstov4`\-Namespace ist im [&#60;appAddin&#62;-Element &#40;Office-Entwicklung in Visual Studio&#41;](../vsto/appaddin-element-office-development-in-visual-studio.md) definiert.  
  
## Beispiel für eine Anpassung auf Dokumentebene  
  
### Beschreibung  
 Im folgenden Codebeispiel wird das `customization`\-Element für eine Anpassung auf Dokumentebene veranschaulicht. Dieses Codebeispiel ist Teil eines umfangreicheren Beispiels unter [Anwendungsmanifeste für Office-Projektmappen](../vsto/application-manifests-for-office-solutions.md).  
  
### Code  
  
```  
<vstov4:customization> <vstov4:document solutionId="73e" /> </vstov4:customization>  
```  
  
## Beispiel für ein VSTO\-Add\-in  
  
### Beschreibung  
 Im folgenden Codebeispiel wird das `customization`\-Element für ein VSTO\-Add\-In veranschaulicht. Das Add\-In ist ein Outlook\-VSTO\-Add\-in, das Formularbereiche enthält. Dieses Codebeispiel ist Teil eines umfangreicheren Beispiels unter [Anwendungsmanifeste für Office-Projektmappen](../vsto/application-manifests-for-office-solutions.md).  
  
### Code  
  
```  
<vstov4:customization> <vstov4:appAddIn application="Outlook" loadBehavior="3" keyName="ContosoOutlookAddIn"> <vstov4:friendlyName> ContosoOutlookAddIn </vstov4:friendlyName> <vstov4:description> ContosoOutlookAddIn - Outlook VSTO Add-in created with Visual Studio Tools for Office </vstov4:description> <vstov4:formRegions> <vstov4:formRegion name="OutlookAddIn1.FormRegion1"> <vstov4:messageClass name="IPM.Note" /> <vstov4:messageClass name="IPM.Contact" /> <vstov4:messageClass name="IPM.Appointment" /> </vstov4:formRegion> </vstov4:formRegions> </vstov4:appAddIn> </vstov4:customization>  
```  
  
## Siehe auch  
 [Anwendungsmanifeste für Office-Projektmappen](../vsto/application-manifests-for-office-solutions.md)   
 [Bereitstellungsmanifeste für Office-Projektmappen](../vsto/deployment-manifests-for-office-solutions.md)   
 [ClickOnce Application Manifest](../deployment/clickonce-application-manifest.md)  
  
  